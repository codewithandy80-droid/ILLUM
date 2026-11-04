# ILLYUM — Approved Skill Specifications

These specifications are locked baseline requirements. Do not simplify or reinterpret them without user approval.

## Skill 1 — Story-to-Script (APPROVED)
**Purpose:** Convert the user's original story source into a short-form video voiceover script.

**Inputs**
- Story source (text/article/URL/transcript or supported source input).
- Selected total video duration.
- Selected language: Hindi or English.

**Rules**
- Every part is maximum 8 seconds.
- Number of parts is determined by selected total duration; it is not fixed at four.
- Part 1: attractive curiosity-based hook.
- Middle parts: story development in connected flow.
- Final part: meaningful ending.
- Preserve source facts/events. No fabricated facts, characters, or incidents.
- If source information is incomplete or ambiguous, flag it.
- Avoid unnecessary words and repetition.
- Natural voiceover flow in the selected language.

**Required output for every part**
- Part Number
- Part Type: Hook / Story / Ending
- Voiceover Script
- Estimated Audio Duration

**Approval:** User reviews/edits and approves the script. Skill 2 and Skill 3 must consume this approved script only.

## Skill 2 — Script-to-Video Generation Prompt (APPROVED)
**Purpose:** Turn each approved script part into a detailed Google Flow-compatible video-generation prompt.

**Input boundary:** ONLY the approved Skill 1 script. Never directly use the original story source.

**Rules**
- One prompt per script part; each video part max 8 seconds; final may be shorter.
- Every prompt explicitly states selected aspect ratio and resolution.
- 9:16 = vertical Shorts/Reels; 16:9 = horizontal YouTube landscape.
- Describe visuals, characters, environment, actions, expressions, camera, movement, zoom, composition, transitions, lighting, and timeline.
- Keep characters and scenes consistent across parts.
- Include exact approved voiceover text and same language.
- Keep one consistent male or female narrator voice, with pitch/tone/accent/delivery specified.
- Voiceover remains narration unless script explicitly has a speaking character. Lip-sync only for actual character dialogue.
- Keep music identity consistent; mood/intensity may change. Sync SFX; prioritize voice clarity; define audio timing and transitions.
- Include all structured fields and the complete Google Flow prompt.
- Text prompt output only; no storyboard images.
- Check compatibility and safety; offer alternatives if needed; no guarantee of perfect generation.

**Required output fields**
Part number; script reference; duration; aspect ratio; resolution; visual description; character details; environment; camera; lighting; action timeline; exact voiceover; voice details; background music; SFX; audio timeline; continuity notes; complete Google Flow prompt.

## Skill 3 — Script-to-Thumbnail Generation Prompt (APPROVED)
**Purpose:** Produce image-generation prompts, not images, from the approved script.

**Input boundary:** ONLY the current project's approved Skill 1 script. Do not use the original source directly.

**Rules**
- Exactly two options per script.
- OPTION A and OPTION B must be fundamentally different concepts/vibes, not simple color variations.
- Analyze the whole script and choose the strongest visual moment, not automatically the first scene.
- Identify strongest emotion, mystery/shock, main subject, conflict, curiosity angle.
- Create curiosity without misleading or revealing the entire ending.
- Preserve character appearance consistency.
- Strong mobile readability, focal point, hierarchy, uncluttered composition.
- Text optional; if used, suggest 2–5 accurate words.
- Specify aspect ratio explicitly: 9:16 vertical for Shorts/Reels, or 16:9 horizontal for YouTube thumbnail.
- Include visual quality instructions and negative constraints (distorted faces, extra limbs/fingers, blur, unnatural proportions, unwanted text, watermarks).

**Required output**
Thumbnail analysis; OPTION A and OPTION B; each with vibe, concept, composition, subject/character, lighting/colors, text recommendation, ratio, mobile visibility, and complete image prompt.

## Skill 4 — Story & Script-to-SEO (APPROVED)
**Purpose:** Generate platform-specific discoverability metadata using both the source story and approved script.

**Input boundary:** BOTH original main source story AND approved Skill 1 script.

**Rules**
- Analyze source story and script separately, then combine.
- Do not include original article title, author, website, or source link in SEO description.
- Save YouTube SEO and Instagram SEO separately.
- YouTube title must be the exact first hook from the approved script.
- YouTube description includes attractive intro, story lines, topic, naturally integrated keywords, curiosity, CTA, transparent AI-assisted disclosure, relevant hashtags.
- YouTube tags: primary, secondary, long-tail, question-based, related search phrases; comma-separated.
- YouTube hashtags: relevant, limited, copy-paste format.
- Instagram caption: hook, short story intro, searchable keywords, curiosity, CTA, transparent AI-assisted disclosure.
- Instagram keywords: topic, niche, story phrases, long-tail.
- Instagram hashtags: relevant topic/niche/story/discovery, not excessive.
- Live research where possible (Google Trends, YouTube suggestions, related queries/results). Separate primary/secondary/long-tail; label trending vs evergreen. Never invent metrics or trends; disclose when live research unavailable.
- Avoid irrelevant trends and keyword stuffing.
- Optimize YouTube for search relevance, title/description, thumbnail-title match, interest, retention, watch time, satisfaction.
- Optimize Instagram for caption/search keywords/hashtags, watch time, shares, saves, engagement.
- Never guarantee ranking or virality.

**Required output**
Source-story analysis; script analysis; combined SEO analysis; YouTube title/description/disclosure/tags/hashtags; Instagram caption/keywords/hashtags/disclosure; keyword research with primary/secondary/long-tail/related queries/verified trends/evergreen.

## Cross-skill invalidation
If the approved script version changes, downstream outputs must be marked stale:
- Skill 2 video prompts
- Skill 3 thumbnail prompts
- Skill 4 SEO results
Require the user to regenerate or explicitly review them against the new script version.
