# ILLYUM — System Architecture & Data Model

## 1. Logical architecture
The implementation should preserve these logical layers, regardless of the final framework:
1. **Frontend/UI:** dashboard, project workspace, forms, tabs, review/approval, copy/export, status display.
2. **Backend/API layer:** validates requests, enforces permissions and dependencies, coordinates persistence and generation.
3. **Authentication/access layer:** suitable for the single owner; exact approach to be selected based on implementation environment and approved by user if consequential.
4. **Database/persistence:** projects, sources, settings, scripts, parts, prompts, SEO results, history, statuses.
5. **File storage:** source uploads and exports where supported.
6. **AI Workflow Orchestrator:** calls skills in the correct order and checks required approvals.
7. **Four skill engines:** Skill 1, Skill 2, Skill 3, Skill 4, each isolated with its own prompt and validation.
8. **AI model provider:** model calls; credentials must be handled securely.
9. **Search/trends provider:** optional/live research for Skill 4 when available.

## 2. Data entities
The planned logical entities are:
- **Users:** owner account and settings.
- **Projects:** project identity, name, lifecycle status, timestamps.
- **Source Stories:** original story content or supported reference, source type, extraction/import status.
- **Scripts:** generated script versions, selected language, selected total duration, approval status.
- **Script Parts:** part number, type, voiceover text, estimated duration, parent script version.
- **Video Prompts:** prompt per script part, ratio, resolution, structured fields, script-version reference, status.
- **Thumbnail Prompts:** exactly two options per approved script, ratio, structured fields, script-version reference, status.
- **SEO Results:** separate YouTube and Instagram records, both linked to source and script versions.
- **SEO Research:** keyword groups, evidence/source, retrieval date, trending/evergreen classification, availability note.
- **Generation History:** skill, input references, output version, timestamps, result/error, status.

## 3. Relationships and integrity
- One user can own multiple projects.
- One project can have one or more source-story versions.
- One project can have multiple script versions.
- One script version contains multiple ordered script parts.
- Each script part can have a corresponding video prompt.
- Each approved script version can have exactly two thumbnail prompt options.
- SEO result records must distinguish platform (`YouTube` or `Instagram`) and link to both source and script versions.
- Generation history records which inputs and prompt/skill version were used.
- Keep project data isolated.

## 4. Data dependency map
Source Story + selected duration + language -> Skill 1 -> Script review/approval.
Approved Script -> Skill 2 -> Video prompts.
Approved Script -> Skill 3 -> exactly two thumbnail prompts.
Source Story + Approved Script -> Skill 4 -> YouTube SEO + Instagram SEO.
Approved Script revision -> mark Skill 2, Skill 3, Skill 4 results stale.

## 5. Stack decisions
This PRD intentionally specifies logical architecture, not a mandatory framework/database/hosting provider. Google AI Studio may recommend implementation choices. Before adopting a consequential provider, database, authentication model, hosting, or paid service, the assistant must explain:
- what the choice does,
- why it is needed,
- expected cost or free-tier caveats if known,
- data/security implications,
- alternatives,
and obtain the user's approval where appropriate.
Never hard-code secrets in browser/client code.
