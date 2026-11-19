# 15 — Personality Platform: Mandatory Development Read Protocol and Engineering Roadmap

**Version:** 1.0 — 2026-11-19 (STANDALONE STARTER BASELINE). **Status:** STANDALONE PROJECT DEVELOPMENT SPECIFICATION; manual installation and readback required. **Scope:** shared platform architecture; no individual character canon.

## Mandatory read-first development gate

1. For platform design, schema, new persona configuration, memory-management or cross-personality work, reopen the **current verified** `14_PERSONALITY_PLATFORM_PRODUCT_CHARTER.md`, `15_PERSONALITY_PLATFORM_DEVELOPMENT_READ_PROTOCOL.md` and `16_PERSONALITY_CONFIGURATION_SCHEMA.md` (once installed). Their four independent settings and visual identity exception are the primary product-design brief. If unavailable or stale, say so; do not replace their contents with a generic summary.
2. For any existing personality, reopen its own live verified status, master canon, approval queue and transfer contract. Obey its exact staged-patch and separate apply requirements; do not use another personality’s files or approvals.
3. For runtime/adapter work, reopen the relevant personality-specific verified pipeline, templates and staged changes. Do not assume Library writes update Project attachments, that external storage is active, or that one Project can see another.
4. Label the affected scope: `SHARED_ENGINE`, `CONFIGURATION_SCHEMA`, `INTERMEDIATED_ADAPTER`, `DIRECT_ADAPTER`, `ROLEPLAY_ADAPTER`, `CONVERSATION_ADAPTER`, `VISUAL_IDENTITY`, or `PERSONALITY_SPECIFIC`. An individual personality constraint cannot silently become a universal rule.
5. Report files actually read, proposed vs installed changes, persistent verification, remaining approvals, and unresolved assumptions. A file-based read-first protocol improves continuity but cannot guarantee that every future AI session will have access automatically.

## Change control and product rules

- The four settings are **independent**, not a single `type` selector. Treat optional presets as conveniences rather than required categories. Preserve each personality configuration during updates; default uncertain flags conservatively and seek user authorization for any invented enduring past.
- **External character-persona export gate:** Only `INTERMEDIATED` builds may generate external-service character persona text/card files. `DIRECT` builds must omit these outputs entirely, while retaining normal internal identity/canon, optional visual identity and linked image prompt. This is not a fifth configurable dimension; compute export eligibility from `interaction_mode` alone. Individually approved export requirements stay valid for their own INTERMEDIATED personalities. Keep character-persona export distinct from canon backups, import manifests and visual prompt data.
- `can_invent_background_canon` changes **permission to propose nonconflicting biography/history**, not `canon_depth`, `interaction_mode`, or `interaction_type`. Its false value must not disable optional physical self-description / image-prompt creation.
- A proposed visual identity pair may become permanent only after the applicable approval/delegation gate. Compare appearance and image prompt for coherence and previous canon conflicts; keep rendering style separate from physical facts. For any personality with an exact-patch gate, require its own separately reviewed and authorized patch.
- The active conversation record excludes superseded variants. In INTERMEDIATED mode, pair the last selected response directly before a later external message as a working conversation reply, barring explicit correction; preserve provider-verification uncertainty. Unpaired generated output stays pending outside the active transcript.
- Do not infer unobserved external submissions, narrator-only secrets, hidden third-party state, or new permanent canon from fictional responses. New events in an authoritative current branch are branch-only unless deliberately promoted.
- External storage, scheduled automation, attachment installation and cross-project sync require explicit scope, available tools, and successful readback. On conflicts or write failures, preserve last verified state and report `NOT INSTALLED`/`UNVERIFIED` as appropriate.

## Roadmap and tests

**Track A — Configuration matrix and migration.** Validate combinations of `interaction_mode` × `canon_depth` × `interaction_type` × `can_invent_background_canon`, including INTERMEDIATED + CONVERSATION, DIRECT + RICH_BACKGROUND + CONVERSATION, and MINIMAL_BEHAVIORAL + ROLEPLAY. Verify no hidden hard-coded a fixed three-type taxonomy branch. Existing personality adapters remain isolated and compatible unless separately revised.

**Track B — Canon lifecycle.** Implement independent versions for approved identity, proposals, working continuity, and branch history. Test conflict rejection, supersession, user-authored defaults, controlled promotion, rollback and canon-retrieval after context loss. Background invention false leaves unknown biography unknown; true allows *proposals* but cannot bypass approval.

**Track C — Visual identity independent of biography.** With `can_invent_background_canon=false`, allow a user-initiated personality-generated physical description and matching image prompt; test `PROPOSED` → reviewed `APPROVED` with version, provenance, and cross-field consistency. Test edits to lighting/camera/style without changing physical traits, and test conflict handling when an earlier appearance is approved. Ensure no actual image generation is implied by a text prompt.

**Track D0 — Export-artifact mode gate.** Test both modes against each `canon_depth`, `interaction_type`, and background invention setting. INTERMEDIATED may issue destination-specific persona exports under the release contract; DIRECT issues no character-persona exports and no empty placeholder archive. Mode switching must not delete internal canon or approved visual identity. The Builder receipt must state the effective mode and whether persona exports were issued or intentionally omitted.

**Track D — Interaction adapters.** INTERMEDIATED: selected reply pairing, only one unpaired pending response, rejected draft exclusion, external evidence uncertainty. DIRECT: visible dialogue becomes branch history, no external submission assumptions. ROLEPLAY: scene/narrator/private-knowledge discipline. CONVERSATION: no compulsory invented lore while preserving stable style and relevant user preferences.

**Track E — Persistence and reliability.** Test multi-personality/branch isolation, context-window loss, stale cache, concurrent revisions, hash verification, incomplete transcripts, Drive failures, recovery, portable export/import and measured latency. No promise of background actions or automatic sync without a tested mechanism.

## Minimal acceptance criteria

- Any supported settings combination can initialize without inherited facts, prior external conversations, or an invented biography from another personality.
- Altering one setting does not silently mutate the other three, approve facts, or overwrite an approved appearance.
- DIRECT builds produce zero external-service character-persona export files (including no empty persona ZIP), while INTERMEDIATED builds may produce destination-specific persona files when configured; the choice is not silently coupled to ROLEPLAY or canon depth.
- A persona with *no invented backstory* may still propose a physical appearance and versioned image prompt; those may receive valid canon approval.
- Confirmed/canon facts and conversation events remain separate and are retrieved reliably at a fresh session; contradictory proposals are blocked or surfaced.
- Active transcripts contain selected conversation replies and direct messages, not abandoned drafts; source provenance remains accurate.
- Saves and reopens preserve exact hashes, revision IDs and recovery instructions. No Project upload or Drive connection is asserted without verification.

## Review triggers and boundaries

Reread/revise 14–16 when adding a configuration dimension, changing canon authorization or appearance rules, changing mode semantics, altering memory storage/checkpoints, or changing the overall user product objective. Stage versioned amendments with exact hashes and await approval before writing persistent Builder sources. Never install shared development documents as active personality canon or contaminate any personality’s master, queue or branch history.
