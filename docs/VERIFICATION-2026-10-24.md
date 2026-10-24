# NextClick verification notes (October 24, 2026)

Status: planning only. No code written. No model calls made.

## Verified from this cloud session
- Working directory /home/user was empty. No repository, no prior NextClick code.
- No Meta API key is present in the environment.
- Network policy blocks dev.meta.ai, llama.developer.meta.com, llama.com, cerebralvalley.ai (CONNECT 403 / DNS not found). Official pages could not be read directly.

## Event (from third-party coverage and search summaries, NOT the official page)
- Meta Global AI Developer Hackathon, virtual, Oct 26 12:00 PM to Nov 4 9:00 PM Eastern.
- Applications due Oct 25, 11:59 PM Eastern, or earlier if the 20,000-participant cap fills.
- Each selected participant reportedly gets $150 in Meta Model API credits.
- Official rules reportedly still pending. Rules on pre-existing work and AI coding assistants: NOT verified.

## Meta Model API (from search summaries, NOT the official docs)
- Base URL https://api.meta.ai/v1, OpenAI-compatible (Chat Completions and Responses). Anthropic-style Messages endpoint also reported.
- Images: image_url content parts; public URL or base64 data URL.
- Model IDs seen in examples: muse-spark-1.3 and muse-spark-1.1. Confirm the current list.
- Reported pay-as-you-go price: $1.25 in / $4.25 out per million tokens.

## Open items before building
1. Dylan: one real website + task someone needed help with.
2. Dylan: apply to the hackathon before Oct 25 11:59 PM ET if not done.
3. Dylan: create a Meta Model API key and add it as an environment secret (never into the extension).
4. Environment: allow dev.meta.ai and api.meta.ai in Network access so docs and live calls work.
5. Decide where the code lives (new GitHub repo recommended).

## First demo task (chosen October 24, 2026)
Source: Dylan reports his mom, an ESU professor, could not find "the faculty page" on the redesigned esu.edu (launched January 2026). Dylan's recollection, not a direct observation.

Website: https://www.esu.edu (public pages only)
Task A: Starting on the esu.edu homepage, reach the Faculty & Staff page.
Variants to confirm with her: her own faculty directory profile; her department's faculty list.
Out of scope: anything behind a login (portal, email, course system).

Still to confirm with her: which "faculty page" she meant, where she ended up, what she clicked.

Draft test page states for Task A (fill in after esu.edu is reachable):
1. Homepage, menu closed. Expected target: the audience/menu control that leads to Faculty & Staff.
2. Homepage, main menu open. Expected target: Faculty & Staff link.
3. Homepage scrolled to footer. Expected target: Faculty & Staff footer link if present.
4. Wrong branch (e.g., landed on Admissions). Expected: recover, point back toward Faculty & Staff.
5. Faculty & Staff page reached. Expected state: possible completion, ask user to confirm.
6. Site search results for "faculty". Expected target: the correct result link, or clarification if duplicates.
7. Department page with a faculty list. Expected target: her name or the directory link.
8. Duplicate labels (two "Faculty" links visible). Expected: clarification or the correct one with a reason.
9. Target off-screen. Expected: scroll hint plus highlight after scroll.
10. Slow-loading page. Expected: wait/refresh guidance, no stale highlight.

## Application status (October 24, 2026)
- Dylan submitted the hackathon application. Status shown: Pending.
- Review criteria (from the event's "How Applications are Reviewed" page, screenshot): project idea clarity/feasibility and fit to "one of the two project themes", plus technical skill from the described AI project. Equal weight. Rolling review; applications above a scoring cut-off accepted automatically up to 20,000.
- Technical-skill answer described ARI (facts from Dylan's portfolio ari.md). Funding: Bootstrapped. GitHub: github.com/dndfiddle-boop (unverified from this environment).

## Verified from the official pages (downloaded October 24, 2026, after network allowlist change)
Event page (dev.meta.ai/events/global-hackathon):
- Tracks: Track 1 Indie developer (individuals and students; judged on creativity, technical ambition, whether it works). Track 2 Startup. NextClick -> Track 1.
- Themes: Theme 1 "Build for Your World" (bring Meta's models into your domain, solve a problem you know firsthand). Theme 2 "Push the Frontier". NextClick -> Theme 1.
- Dates (ET): approval notice by Oct 26 9:00 AM; kickoff Oct 26; workshops Oct 27-Nov 4; submissions due Nov 4 9:00 PM; judging Nov 4-8; winners Nov 9.
- Official Rules will be published before Oct 26 and must be accepted. Rules on pre-existing work and AI coding help are therefore STILL unverified.
- Models named for the event: Muse Spark series, Muse Image, SAM 3.1 via Meta Model API; open-weight models; Muse Code coding agent.

Meta Model API docs (dev.meta.ai/docs):
- Base URL https://api.meta.ai/v1. Drop-in compatible with the OpenAI SDK and the Anthropic SDK. Endpoints: /v1/responses (recommended), /v1/chat/completions, Messages API.
- Auth: "Authorization: Bearer <key>". Keys start with LLM_ and are created in the Model API dashboard, API keys tab. Docs use env var MODEL_API_KEY.
- Models: muse-spark-1.3, muse-spark-1.2, muse-spark-1.1 (standard); muse-spark-1.3-contributor (cheaper, different data terms); muse-wonder-1.0; muse-image-1.0; sam-3.1; muse-voice-transcribe-1.0.
- Image understanding: images only in user messages; pass as public URL, base64 data URL, or file_id. Responses API uses input_text + input_image blocks. Docs claim "perception grounding" (object locations as coordinates). Structured output page exists.
- From this container: api.meta.ai/v1/models answers 401 without a key (reachable). dev.meta.ai reachable.

ESU: www.esu.edu still fails from this container with a TLS trust error (its chain ends at emSign Root CA G1, missing from the container store; proxy returned 502 in Chromium). Not an allowlist problem. Dylan's own Chrome is unaffected.

## ESU homepage captured (October 24, 2026, via Firecrawl; see fixtures/esu-home-2026-10-24/)
- "Faculty & Staff" is NOT in the visible top navigation. It is inside the hamburger Menu overlay under "Tools and Support For:", and in the footer. URL: https://www.esu.edu/faculty-staff/index.php
- A near-duplicate label exists: "Faculty & Staff Directory" (https://www.esu.edu/faculty-staff/directory.php), in the same overlay and under About ESU.
- This matches Dylan's report: a longtime user looking for the faculty link in the main nav would not find it. Task A step 1 is therefore "Click Menu", step 2 "Click Faculty & Staff".
- Workaround for the container's TLS block on esu.edu: capture pages through Firecrawl (markdown + links + screenshot) as fixtures.
