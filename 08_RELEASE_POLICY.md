# Release policy — mode-gated outputs (Draft)

**Do not treat this starter template as a deployable release.** A particular personality release must be derived from verified approved canon and a complete configuration, with explicit user-approved installation where applicable.

## Always keep separate

1. **Builder-only writable authority:** approved canon ledger, approval queue, versioned patch history and evidence.
2. **Runtime read-only canon:** branch-neutral derived snapshot (if runtime requires one), paired with checksum/size/version/source manifest.
3. **Active conversation memory:** per-branch records and working caches, never a substitute for global canon.
4. **Optional visual identity:** physical description and image prompt with approval trail; allowed in both modes.

## External character-persona export gate

- `INTERMEDIATED`: destination-specific character-persona text/card exports are **eligible** only when a release contract or the user needs them. Apply the destination's word/character and privacy requirements. Separate them from a runtime import ZIP.
- `DIRECT`: **zero** external character-persona text/card exports, **zero** empty placeholder persona ZIPs. Internal canon, read-only runtime snapshot, normal backup and image prompts may still be produced under their own policies.
- Derive this rule from `interaction_mode` alone, not roleplay vs conversation, canon depth or background invention. Switching modes is a new reviewed release decision, not a destructive rewrite of approved canon.

## BLIND / privacy and continuity

Never copy Builder's writable master, approval queue, old transcript, abandoned drafts, hidden narrator knowledge, unapproved fact proposals or controlled-test private data into ordinary runtime canon. If private-data controlled testing is authorized, separate, label, and review it; do not call it BLIND.

## Minimum receipt

Record personality ID, config version, canon version, approval states, mode, all issued artifacts and intentional omissions, raw SHA-256 values and sizes for each final file, validation results, and whether remote/project installation or readback actually succeeded. A hash confirms bytes, not semantic correctness or platform-provider submission.

## Deployment status labels

`DRAFT` → `CONTENT_REVIEWED` → `READY_FOR_MANUAL_INSTALL` → `INSTALLED_READBACK_VERIFIED`. Do not skip to the last state on the basis of packaging alone. No background persistence, Drive sync or cross-Project access is assumed.

**Personality-specific contracts:** Existing personalities may have stricter approved import formats, approval gates, privacy rules, or release sequences. Apply those rules only to the personality that owns them; never generalize one character’s contract to the shared engine.
