# Personality — Multiple-Identity Build Guide (Draft)

The **Rudyblah Personality Generator** development workspace is an engine for building and maintaining *many* independent personalities. It is not a single personality and has no default character or conversation partner.

## Isolation

Each `personality_id` has its own approved canon, proposal queue, visual identity, configuration revision, active branches, evidence records and release history. The shared engine implements the four independent settings and storage interfaces, but carries no individual biography. The catalog is only an index and grants no canon authority.

Suggested logical layout (not a claim of existing storage):

```text
Rudyblah Personality Generator/
  platform/                # generic design references and Builder rules
  catalog.json             # namespaced registry, no default personality
  personalities/
    <personality_id>/
      configuration.json
      canon_ledger.json
      approval_queue.json
      visual_identity.md
      branches/<branch_id>/
      releases/<release_id>/
```

## New personality

1. Assign a new stable ID in `11_PERSONALITY_CATALOG.json` (do not overwrite a prior ID).
2. Fill `02_PERSONALITY_BUILD_WORKSHEET.md` and four independent configuration fields.
3. Enter only sourced or expressly approved permanent facts into its own canon ledger. Keep unknowns unknown and provisional additions outside canon.
4. Stage optional physical description and image prompt separately from biography; receive explicit approval before treating them as canon.
5. Create branch-only memory only when an actual conversation is designated; never prepopulate history from another identity.
6. For INTERMEDIATED, pair the final selected response and following external reply in working continuity, with provider proof separately labeled. For DIRECT, use confirmed visible dialogue. Do not convert unsent drafts into established events.
7. Derive character-persona exports only for INTERMEDIATED and only as the release target requires. DIRECT never generates character-persona text files/ZIPs.
8. Validate content, hashes, approvals, version/recovery boundaries, and installation/readback separately.

## Existing personality

To revise an existing personality, select its ID, reopen its **current authoritative** configuration, canon and approvals, and obey its exact approval gate. Changing the *shared engine* never automatically changes, renames, or rewrites its facts. Never claim a remote persistent write or runtime installation without independent readback.

## Project naming and status

Workspace/Project name: **Rudyblah Personality Generator**. This package does not create or rename a ChatGPT Project. Status is `READY_FOR_MANUAL_PROJECT_INSTALL`; first verify the Project after upload. No other workspace is affected.