# ILLYUM — Product Requirements Document (PRD)

**Document status:** Approved baseline  
**Product:** ILLYUM  
**Primary user:** Single owner/operator; non-coder  
**Build approach:** Prompt-guided development in Google AI Studio  
**Scope rule:** Implement the approved requirements below; no silent additions or omissions.

## 1. Product vision
ILLYUM is a single-user AI-assisted content creation application that takes a story source and helps the user produce:
- a short-form video voiceover script,
- detailed Google Flow-compatible video-generation prompts,
- two distinct thumbnail-generation prompts,
- separate YouTube and Instagram SEO packages.

The application must preserve source accuracy, keep each skill's inputs controlled, and make each stage reviewable and reusable.

## 2. Primary user and operating principles
- The user is a non-coder and should operate the app through a clear graphical interface.
- Avoid requiring the user to edit source code, database queries, configuration files, or command-line instructions.
- Use clear labels, guided steps, validation, progress/status indicators, and useful error messages.
- Generated outputs must be editable, savable, copyable, and exportable.
- The application must show what is complete, pending, failed, or needs review.
- Do not imply that AI output is guaranteed error-free, viral, or ranked.

## 3. Core user journey
1. Open dashboard.
2. Create a new project.
3. Enter project name and add the original story source (text, article, URL, transcript, or other supported source type).
4. Configure Skill 1: desired video duration and language (Hindi or English).
5. Generate and review the script; approve it before downstream generation.
6. Generate Skill 2 video prompts from the approved Skill 1 script; review and save.
7. Generate Skill 3 exactly two thumbnail prompt options from the approved Skill 1 script; review and save.
8. Generate Skill 4 SEO using both the original source story and the approved Skill 1 script.
9. Review YouTube SEO and Instagram SEO separately.
10. Copy or export outputs and return to the project later.

## 4. Application navigation and screens
### 4.1 Main navigation
- Dashboard
- Projects
- Create New Project
- Settings

### 4.2 Project workspace tabs
- Source Story
- Script
- Video Prompts
- Thumbnail Prompts
- SEO

### 4.3 SEO workspace
SEO must contain two separate sub-tabs:
- **YouTube SEO**
- **Instagram SEO**

Each platform's output must be stored and displayed separately. Do not combine the two into one result field.

### 4.4 Common workspace capabilities
- Save project and generated outputs.
- Show generation status and timestamps where available.
- Allow review and approval before downstream use.
- Copy individual fields and complete output.
- Export outputs in practical formats where supported.
- Preserve previously approved versions when a new generation is requested.
- Show source/dependency references so users can understand which approved content was used.

## 5. Functional requirements
### FR-01 Project management
- Create, open, rename, and manage projects.
- List projects with useful status and last-updated information.
- Keep each project's source story, settings, generated assets, approvals, and history associated with that project.
- Avoid mixing content between projects.

### FR-02 Source story intake
- Accept source material supported by the chosen implementation (at minimum pasted text; URL/file intake may depend on provider and implementation capabilities).
- Store the original source or a durable reference to it.
- Show the source to the user before generation.
- If a URL cannot be accessed or content extraction fails, clearly ask for pasted text or a supported file; do not pretend it was read.
- Record source type and extraction/import status.

### FR-03 Skill 1 script generation
- Inputs: original story source, user-selected total video duration, selected language (Hindi or English).
- Generate a number of parts appropriate to the selected total duration.
- Each part must be no longer than 8 seconds.
- First part is a curiosity-based hook.
- Middle parts develop the story in a connected sequence.
- Last part provides a meaningful ending.
- Preserve source facts, events, people, and chronology. Do not invent facts, characters, or incidents.
- Flag missing, ambiguous, or incomplete source information.
- Avoid unnecessary words and repetition.
- Output fields per part: Part Number, Part Type (Hook/Story/Ending), Voiceover Script, Estimated Audio Duration.
- Natural, connected voiceover flow; language must consistently follow the selected language.
- User must be able to review, edit, save, and approve the script.
- Downstream Skills 2 and 3 must use the approved Skill 1 script, not independently reinterpret the original source.

### FR-04 Skill 2 video prompt generation
- Direct/primary input is ONLY the approved Skill 1 script. Do not directly use the original story source.
- Generate one detailed Google Flow-compatible video-generation prompt for each script part.
- Each generated video part is at most 8 seconds; final part may be shorter.
- Explicitly state selected screen ratio and resolution in every prompt:
  - 9:16: vertical 9:16 for YouTube Shorts/Reels.
  - 16:9: horizontal 16:9 for YouTube landscape.
- Include visual description, characters, environment, actions, expressions, camera angle/movement/zoom/composition/transitions, lighting, and action timeline.
- Maintain character consistency across parts (face, age, hairstyle, clothing, body appearance), unless the script explicitly requires a change.
- Maintain scene continuity (location, environment, weather, objects, visual style).
- Include the exact approved voiceover script, in the same language.
- Keep a consistent male or female voice across the video, including pitch, tone, accent, and delivery.
- Sync visuals to voiceover. Do not convert narration into character dialogue. Use lip-sync only when a character actually speaks in the script.
- Audio requirements: consistent music identity across the whole video; mood/intensity may vary; synchronized sound effects; voiceover clarity is the priority; define audio timing and natural transitions between parts.
- Include complete prompt and structured fields: part number, script reference, duration, ratio, resolution, visual description, character details, environment, camera, lighting, action timeline, exact voiceover, voice details, background music, SFX, audio timeline, continuity notes, complete Google Flow prompt.
- Text prompts only; do not create storyboard images.
- Review compatibility and safety. Give alternatives where a requested depiction may be problematic; do not promise flawless generation.

### FR-05 Skill 3 thumbnail prompt generation
- Direct source is ONLY the current project's approved Skill 1 script. Do not directly use the original story source.
- Do not generate images; output image-generation prompts only.
- Generate exactly two options for every script:
  - OPTION A: one distinct visual vibe/concept.
  - OPTION B: a completely different visual vibe/concept, not merely a color or lighting variation.
- Analyze the whole script to identify strongest visual moment, emotion, mystery/shock, main character/object, central conflict, and curiosity angle.
- Do not automatically choose the first scene. Choose the strongest visual moment.
- Create a curiosity gap without revealing the full ending or misleading the viewer.
- Keep character appearance consistent within the script.
- Ensure mobile visibility, strong focal point, clear visual hierarchy, uncluttered composition.
- Text is optional. If useful, suggest 2–5 powerful, accurate words; otherwise recommend no text.
- Specify cinematic lighting and high-quality visuals. Avoid distorted faces, extra fingers/limbs, blur, unnatural proportions, unwanted text, and watermarks.
- Explicitly specify selected aspect ratio:
  - 9:16 vertical for Shorts/Reels; no horizontal composition.
  - 16:9 horizontal for YouTube video thumbnail.
- Output thumbnail analysis plus OPTION A and OPTION B, each with vibe, concept, composition, character/subject, lighting/colors, text recommendation, ratio, mobile visibility, and complete image prompt.

### FR-06 Skill 4 story & script SEO
- Primary sources BOTH:
  1. Original main source story.
  2. Approved Skill 1 generated script.
- Analyze both separately and together: source-story analysis, script analysis, combined SEO analysis.
- Do not add original source article name, author, website, or link in the SEO description.
- Produce separate YouTube SEO and Instagram SEO packages, separately formatted and saved.
- YouTube title must be the exact first hook from the approved script; do not rewrite it.
- YouTube description: attractive intro, story-related lines, topic, relevant naturally integrated keywords, curiosity, CTA, transparent AI-assisted disclosure, relevant hashtags.
- YouTube tags: primary, secondary, long-tail, question-based, and related search phrases; provide comma-separated copy/paste format.
- YouTube hashtags: relevant and limited; copy/paste format.
- Instagram Reel caption: attractive opening hook, short story intro, searchable keywords, curiosity, CTA, transparent AI-assisted disclosure.
- Instagram search keywords: main topic, niche, story phrases, long-tail.
- Instagram hashtags: topic/niche/story/discovery, not excessive or irrelevant.
- Conduct live keyword research where possible using Google Trends, YouTube search suggestions, related queries/results. Separate primary, secondary, and long-tail keywords; distinguish current trending from evergreen.
- Never fabricate search volume, rankings, or trend claims. If live research is unavailable, say so.
- Do not use irrelevant trending terms or keyword stuffing.
- Platform optimization:
  - YouTube: search relevance, title/description, thumbnail-title match, interest, retention, watch time, audience satisfaction.
  - Instagram: caption/search keywords/hashtags, watch time, shares, saves, engagement.
- Do not guarantee ranking or virality.
- Output: source + script analysis, YouTube SEO (title, description, disclosure, tags, hashtags), Instagram SEO (caption, keywords, hashtags, disclosure), keyword research (primary, secondary, long-tail, related queries, verified current trends, evergreen).

## 6. Dependency rules (mandatory)
- Skill 1 depends on the original story source and user settings.
- Skill 2 depends ONLY on the approved Skill 1 script.
- Skill 3 depends ONLY on the approved Skill 1 script.
- Skill 4 depends on BOTH the original story source and approved Skill 1 script.
- If Skill 1 script changes after approval, mark Skill 2, Skill 3, and Skill 4 outputs as potentially outdated and require regeneration/review. Do not silently treat old downstream results as current.
- Never let a downstream skill run with missing or unapproved required inputs.

## 7. Non-functional requirements
- Usability: simple, guided interface for a non-technical single user.
- Reliability: save data safely and show failures clearly.
- Data integrity: maintain project separation, versions, source references, and approval states.
- Traceability: show which source/script version generated each output.
- Maintainability: modular skill services and clear boundaries.
- Security: protect user data, use secure provider-side secret handling, never expose API keys in client code.
- Responsivity: usable on desktop and mobile layouts where feasible.
- Accessibility: readable contrast, labels, keyboard-friendly controls where supported.
- Performance: show progress during long-running generation; do not freeze the interface.

## 8. Out of scope unless separately approved
- Multi-user collaboration, team roles, public social publishing, automatic uploading, payments/subscriptions, analytics dashboards, mobile native apps, and features not listed in this PRD.
- Do not select a technology stack or third-party service as an approved decision unless the user explicitly approves it. The implementation environment may recommend options, but must explain trade-offs and ask before committing to consequential choices.

## 9. Definition of product completion
The application is ready only when:
- All approved screens and project workflow are implemented.
- All four skills meet their detailed requirements.
- Skill input dependencies and approval gates work.
- YouTube and Instagram SEO are separate and saved separately.
- Projects and outputs persist after refresh/reopen using the chosen supported storage approach.
- Statuses, errors, history, copy/export, and audit tests pass.
- The user has reviewed and accepted the final phase.
