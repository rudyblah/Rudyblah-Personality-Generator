# 14 — Personality Platform: Configurable Product Charter

**Version:** 1.0 — 2026-11-19 (STANDALONE STARTER BASELINE). **Scope:** long-term product design for a reusable, customizable AI personality with persistent, verifiable canon and conversation memory. **Authority:** user-established product goal and four independent configuration dimensions; implementation suggestions are identified as such. **Status:** STANDALONE DESIGN SPECIFICATION FOR MANUAL INSTALLATION; no runtime deployment or durable storage is implied.

## 1. Mission and non-negotiable separation

Develop a **customizable AI personality platform** with an advanced persistent canon/continuity system designed to mitigate memory fade. A personality's state must survive ordinary context-window loss through real storage, controlled retrieval, reconciled history, source labels, and independently verifiable updates. No individual personality is the universal product, schema, runtime, or default background.

Distinguish: (a) identity and approved durable canon, (b) the specific conversation's event history, (c) current working situation, (d) unsent/rejected candidates, (e) evidence/knowledge access, and (f) the storage/checkpoint subsystem. Never convert roleplay improvisation or a draft into global canon just because it appears in generated text.

## 2. Personality configuration: FOUR ORTHOGONAL SETTINGS (user-directed)

The product must NOT be hard-wired to three mutually exclusive personality types. A personality is configured by a **combination** of four dimensions; informal presets are never exhaustive types.

1. **`interaction_mode`** — `INTERMEDIATED` or `DIRECT`.
   - `INTERMEDIATED`: A person mediates external input and the personality's output. They may review/revise a proposed reply and control its external submission. The active conversation records the *final selected response directly followed by the external participant's next message* as a conversation reply; superseded alternatives are not active transcript turns. Distinguish user-designated chat continuity from external-platform certification. A pending unpaired reply is not yet an active turn.
   - `DIRECT`: The end user converses with the personality in the present interface. No external submission pairing is needed; confirmed visible direct exchanges enter the working conversation history under the appropriate evidence status.
2. **`canon_depth`** — degree of required background detail, independently of permission to invent it. Suggested extensible values: `MINIMAL_BEHAVIORAL`, `LIGHT_BACKGROUND`, `RICH_BACKGROUND`, `CUSTOM`. Minimal depth means a personality can exist without an invented personal history; rich depth means substantial background is expected to be supplied or approved. Depth never itself authorizes fabrication or promotion.
3. **`interaction_type`** — `ROLEPLAY` or `CONVERSATION`.
   - `ROLEPLAY`: Character/world/scene conventions and in-world knowledge boundaries apply, including distinction between narration/private thoughts and what the character knows.
   - `CONVERSATION`: Ordinary conversational interaction; no roleplay scene or fictional lore required. This does NOT forbid a persona with approved history or an optional visual identity. The user's expectations and truthful source labeling still apply.
4. **`can_invent_background_canon`** — `true` or `false`, specifically governing invention of *new background facts* (e.g., family, birthplace, childhood, education, occupation history, backstory, relatives, past relationships and world lore).
   - `false`: Do not fill unspecified biography/history by invention. Clarify an unknown or leave it unspecified. This does not block ordinary dialogue, story events, user-submitted facts, or visual identity creation (see §3).
   - `true`: Permit **nonconflicting background suggestions** within the configured depth and user scope. Cross-check existing approved canon, chronology, source authority, and character knowledge first. New invented details are candidates, not automatically permanent facts; use the personality's separately configured approval/delegation policy.

These four values must be independently editable and persist with `personality_id`, a schema version and a configuration revision. Do not infer one setting from another or let presets silently constrain combinations. Example configurations are illustrative only and establish no individual canon:

| Example | interaction_mode | canon_depth | interaction_type | can_invent_background_canon |
|---|---|---|---|---|
| Intermediated fictional personality | INTERMEDIATED | RICH_BACKGROUND | ROLEPLAY | false |
| Direct fictional character | DIRECT | RICH_BACKGROUND | ROLEPLAY | true or false |
| Lightweight conversation personality | DIRECT | MINIMAL_BEHAVIORAL | CONVERSATION | false |
| Direct character developing its history | DIRECT | LIGHT_BACKGROUND | ROLEPLAY | true |
| Intermediated conversational agent | INTERMEDIATED | MINIMAL_BEHAVIORAL | CONVERSATION | false |

## 3. Mode-gated external character-persona exports (USER REQUIREMENT)

**Generate character-persona text files intended for export to an external service ONLY for `interaction_mode = INTERMEDIATED` builds.** This means platform-specific character cards/persona strings such as target-specific compact, standard, or controlled-test character cards when a particular release contract requires them. They are *derived delivery artifacts*, not the authoritative personality configuration or permanent canon.

- `INTERMEDIATED`: Persona export is **eligible**; generate the target-specific formats when the release contract or user requests them. Apply target length, privacy and formatting rules; Any separately approved personality-specific export contract continues to apply to its own INTERMEDIATED build. Keep persona exports separate from the active Generator canon/import package.
- `DIRECT`: **Do not generate, package, or install character-persona export files** as part of a build, even with `canon_depth=RICH_BACKGROUND` or `interaction_type=ROLEPLAY`. No empty placeholder ZIP should be issued. The personality still has its own internal configuration, approved background (if any), behavioral identity, conversation memory, visual description and image prompt; none of those is removed.
- This condition depends **only on `interaction_mode`**, not on canon depth, roleplay vs conversation, or the background-invention flag. The `can_invent_background_canon` control never enables persona export by itself.
- Ordinary backup, machine-readable canon transfer, visual identity data or image-prompt export are **not** equivalent to an external *character-persona text export*. Maintain separate export policies and provenance for those different artifact classes.
- On a future explicit mode change `DIRECT → INTERMEDIATED`, eligible persona exports may be freshly derived from the *current approved canon*, never copied as stale release artifacts. Switching to DIRECT must suppress new character-persona exports without deleting canon. Mark eligibility/omission in release receipts.

## 3. Independent physical identity and image-prompt canon (USER REQUIREMENT)

**`can_invent_background_canon = false` must NEVER, by itself, prohibit a personality from creating its own physical description and a related visual-generation prompt.** Physical appearance and the image prompt are **visual identity**, not automatically the same permission domain as biography/backstory. A personality with minimal canon depth may still have an appearance. Creation is allowed as an *optional proposal*, not a mandate to invent physical attributes in every interaction; an explicit user prohibition or higher-priority safety/consistency rule still governs.

Separate records:
- `physical_description`: a structured or narrative description of the personality's appearance (only attributes supported/approved or explicitly proposed; no invention that conflicts with established appearance or other canon).
- `image_prompt`: a text prompt for creating consistent depictions, linked to the physical description and a visual style; clearly distinguishes **identity attributes** from rendering directions (camera, lighting, clothes for a particular scene, art style). The prompt itself is not photographic proof of appearance.
- `visual_identity_revision`: an approved description/prompt pair's version, provenance, status, and any supersession link. A prompt may be revised for render quality without silently rewriting approved physical attributes.

Both the personality-created physical description **and** the related image prompt **can become durable canon**, including when background invention is disabled, through the configured canon authorization policy. For a personality with an existing exact-patch authorization policy, that stricter policy still governs its own appearance changes. For the generic product, an explicitly user-delegated authorization policy may be designed later, with auditable scope and rollback; do not assume such a policy exists or is active now. Until authorized, label generated visual identity as `PROPOSED`, not `APPROVED`.

If prior canon establishes appearance, new variants must preserve approved attributes or flag a conflict and require review. Do not infer user identity, sensitive physical traits, or personality biography from an image-generation prompt. No need to generate an actual image merely because a description/prompt is defined.

## 4. Shared memory engine and evidence model

- **Personality store:** `personality_id`, configuration revision, stable behavioral traits, approved background when present, optional approved visual identity, canon policy; explicit user-confirmed vs user-authorized defaults.
- **Canon store:** unique fact IDs, content, scope, provenance, certainty, status, effective version, approval actor/policy, superseded/rejected records and conflict checks. Proposed in-character lines are not approved facts.
- **Conversation store:** each branch has a `branch_id`, order, exact content when accessible, actor, event status and evidence class. Do not contaminate one branch with another.
- **Working continuity:** active scene or discussion, established events, current knowledge available to the personality, open questions and relationships, with pointers to the evidence rather than solely a free-form summary.
- **Pending and discarded outputs:** independent of the active transcript. For intermediated exchanges, one latest unpaired proposed output is pending; a later response from the external participant supports selection of the immediately preceding final candidate absent correction, but is not independent provider certification.
- **Memory manager:** startup retrieval, incremental capture, periodic checkpoints, hash integrity, conflict detection, versioned recoveries, and safe readback-verified persistence. If storage cannot be verified, report failure; never claim automatic Project-attachment installation, background work or universal cross-project memory.
- **Privacy and knowledge controls:** isolate personalities, branches and users; respect narrator/private-thought boundaries, consent, storage permissions, correction and retention controls; do not fabricate missing exact dialogue.

Evidence labels distinguish `DIRECT_USER_SUPPLIED`, `CHAT_VERBATIM`, `USER_DESIGNATED_CONVERSATION_REPLY`, `USER_CONFIRMED_SUBMITTED`, `EXTERNAL_PROVIDER_MATCH`, `INFERRED`, and `DRAFT_ONLY` as appropriate. A cryptographic hash proves bytes, not external-platform submission.

## 5. User-set decisions vs engineering defaults

**Confirmed user requirements:** configurable cross-personality platform; persistent canon and branch memory; four separate settings; no locked three-type taxonomy; permission to invent nonconflicting background only when enabled; appearance description and image-prompt generation not suppressed by that background flag; external character-persona export generated only for INTERMEDIATED builds; eligible visual identity can become canon; no single character is the platform default; rejected drafts are not conversation turns.

**Implementation choices awaiting design/acceptance:** exact enum names/depth granularity; how user-facing configuration UI works; storage vendor/database; interval and trigger for checkpoints; image rendering model; possible delegated canon authorization; per-user retention defaults and portability format. Examples above are defaults offered for review, not claims of installed runtime functionality.

## 6. Individual personality boundaries

Each personality owns its own authority files, approval queue, provenance, version, active branches and scoped release rules. Shared platform changes must not overwrite or silently modify these files. Branch-neutral runtime snapshots exclude writable canon stores, approval queues, private archives and prior conversation history. Adapter revisions require separate review and explicit approval.