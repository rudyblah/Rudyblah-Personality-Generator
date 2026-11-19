# 16 — Personality Configuration Schema and Visual Identity Lifecycle (Design Reference)

**Version:** 1.1 — 2026-11-19 (CANONICAL VISUAL FIELD NAME CLARIFIED). **Status:** STANDALONE STARTER SCHEMA; runtime implementation requires separate deployment and tests. **Scope:** platform-generic, not any individual master canon.

## Core independently configurable dimensions

| Field | Values proposed | Decides | Does NOT decide |
|---|---|---|---|
| `interaction_mode` | `INTERMEDIATED`, `DIRECT` | Who manages inputs/outputs and how conversation replies become active records | Whether the personality roleplays or has a biography |
| `canon_depth` | `MINIMAL_BEHAVIORAL`, `LIGHT_BACKGROUND`, `RICH_BACKGROUND`, `CUSTOM` | Desired amount of established background | Permission to invent, mandatory visual identity, or approval bypass |
| `interaction_type` | `ROLEPLAY`, `CONVERSATION` | Style/scene conventions and character knowledge rules | Directness, background richness, biography invention |
| `can_invent_background_canon` | `true`, `false` | Whether to propose new nonconflicting biography/history/world facts | Permission to create a physical description or image prompt |

These settings are orthogonal. Do not represent the system as exactly three permanent classes; optional presets may derive from individual choices, with independent user-editability. Presets may exist but do not lock combinations.

## Derived character-persona export policy (NOT a fifth setting)

`external_character_persona_export_eligible = (interaction_mode == "INTERMEDIATED")`.

- `DIRECT`: no external-system character persona text/card outputs, no Standard/Compact/Complete-style export files, and no empty ZIP. The internal personality definition, canon store, approved background, physical description, and image prompt remain available and versioned.
- `INTERMEDIATED`: external character-persona text exports may be built when a destination/release contract calls for them. Apply destination-specific requirements, review source authority, and count characters where needed. Any individually approved export formats belong solely to that INTERMEDIATED adapter, not every personality.
- Keep `visual_identity.image_prompt` distinct from a *character persona for external export*: the image prompt can exist in either mode and be approved as visual canon. Likewise canonical backups or neutral portability formats can have their own unrelated export processes.
- Record actual effective `interaction_mode` and persona-artifact output/omission in release receipts. Do not infer mode from `interaction_type`, `canon_depth`, or background invention. Reject unrecognized modes rather than silently producing personas.

## Proposed JSON configuration example

```json
{
  "schema_version": "0.2-proposal",
  "personality_id": "example-personality-new",
  "configuration_revision": 1,
  "interaction_mode": "DIRECT",
  "canon_depth": "MINIMAL_BEHAVIORAL",
  "interaction_type": "CONVERSATION",
  "can_invent_background_canon": false,
  "background_canon": {"status": "NOT_REQUIRED", "facts": []},
  "visual_identity": {
    "creation_allowed_independent_of_background_flag": true,
    "physical_description": {"status": "UNSET", "text": null, "revision": 0},
    "image_prompt": {"status": "UNSET", "text": null, "revision": 0},
    "approval_policy": "USER_REVIEW_REQUIRED",
    "last_approved_revision": null
  },
  "memory": {"canon_version": null, "active_branch_id": null, "storage_status": "UNCONFIGURED"}
}
```

The example depicts an initial configuration only, not a saved user identity or actual system connection. `creation_allowed_independent_of_background_flag` is the required *logical separation*; do not conflate it with unconditional permission to ignore an explicit user refusal or content restrictions. The actual production schema should model user capability controls separately if the UI needs an appearance-off preference.

**Canonical JSON field:** `visual_identity.creation_allowed_independent_of_background_flag` is the required name in configuration documents and validators. The prior alternate field spelling is not part of this schema. This boolean records that visual-identity proposals are independent of permission to invent biographical background; it does not bypass approval.

## Rules for background invention and visual identity

1. **Unknown facts stay unknown** when `can_invent_background_canon=false` (e.g., no invented hometown, parents, career history, world mythology). The personality can still speak conversationally, accrue supported branch events, follow user-provided facts, and *propose* its own physical description and linked image prompt.
2. With invention enabled, new nonconflicting background details may be generated only in relevant scope, using provenance `PERSONALITY_GENERATED_PROPOSAL`, status `PROPOSED`. Compare candidate against all currently approved facts and timeline before offering it; conflicts require correction or review. `true` is not approval to silently make permanent canon.
3. Physical identity is a **separate canonical domain**, e.g. `VISUAL_IDENTITY`, and its *proposal capability* does not depend on background invention or richness. This domain may include hair, build, eyes, face, distinctive markings and other non-sensitive appearance traits as applicable. Each fact requires source/approval tracking. Do not invent biographical events to justify an appearance detail.
4. The **image prompt** is an associated canonical render specification, not a substitute for the approved physical description and not evidence of an actual generated image. Organize `identity_constraints` (stable traits) separately from `render_style` and `scene_variant` (changeable). E.g., lighting, medium, background, attire for a scene should not rewrite approved physical identity unless separately approved.
5. The default **promotion flow** is `UNSET` → `PROPOSED` → (`APPROVED` / `REJECTED` / `PROVISIONAL`) → versioned replacement as needed. Store proposal ID, origin, exact text, conflicts checked, approving actor/instruction, timestamp, version and SHA-256 where applicable. A paired description + prompt can be approved together or separately with explicit dependency metadata; never label one as approved if it depends on unapproved traits.
6. When a canon description is updated, flag linked image prompts requiring review; preserve previously approved versions. Don't silently change the physical traits inside an allegedly style-only image prompt edit.
7. Existing personalities retain their own review/approval queues and exact separate-apply gates. Generic product work may propose a user-delegated authorization setting **later**; it is not active by default and cannot supersede any established personality-specific governance.

## Example behavior checks

| Configuration | Expected behavior |
|---|---|
| DIRECT + MINIMAL_BEHAVIORAL + CONVERSATION + false | May propose appearance and portrait prompt; no invented biography; ordinary chat memory operates normally |
| DIRECT + RICH_BACKGROUND + ROLEPLAY + false | Uses supplied/approved backstory; leaves unspecified historical facts unknown; may propose visual identity |
| DIRECT + RICH_BACKGROUND + ROLEPLAY + true | May suggest nonconflicting backstory candidates and appearance; both require configured canon authorization |
| INTERMEDIATED + MINIMAL_BEHAVIORAL + CONVERSATION + false | User mediates outputs, final selected response pairs with later external message; no backstory invention; optional visual identity |
| INTERMEDIATED + RICH_BACKGROUND + ROLEPLAY + false | Rich roleplay adapter, with branch separation and independent canon gate |

## Schema acceptance and migration

- Parse the four settings independently; validating any setting must not coerce the others.
- Convert any chosen preset into separate independent fields without forcing a fixed taxonomy. Verify explicit user choices are not overwritten by defaults.
- Keep `physical_description` and `image_prompt` independently writable **as proposals** when background invention is false; approval is a separate operation.
- Test proposal provenance, contradictory attributes, prompt consistency, approved-state protection, revision rollback and retrieval after a new chat.
- Cross-product mode gate: for any DIRECT configuration (including RICH_BACKGROUND + ROLEPLAY + background invention true), persona export count = 0; for INTERMEDIATED mode, only release-requested/contract-required persona text exports may be created. Check a DIRECT → INTERMEDIATED switch can derive fresh exports without mutating canon. Confirm visual description/image prompt remain available in both.
- Validate branch specificity of conversation events, separate identity authorization, and optional visual identity in non-roleplay personalities.
- Do not imply the platform has implemented the schema, persistent database, automatic checkpoints, image generation or Connector writes until separately deployed and tested.