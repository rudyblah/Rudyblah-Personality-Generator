# Rudyblah Personality Generator

**A configurable, multi-personality design and development workspace for AI personalities with controlled canon, scoped conversation continuity, and auditable releases.**

> **Project status (2026-11-19):** Design/specification starter package — **not** an installed autonomous runtime, persistent-memory backend, or cross-project sync service. No personality is created or selected by default. The catalog starts empty.

## What this project is

Rudyblah Personality Generator is a **Builder**, not a specific character. It provides reusable instructions, architecture, configuration schema, worksheets, templates, and release/acceptance rules to create and manage multiple distinct personalities. Each expressly selected personality has its own stable `personality_id`, configuration revision, approved canon, proposals, conversation branches, visual identity, and release history.

**Goals:**
- Design personalities without inheriting another identity's biography or conversations.
- Distinguish approved durable facts from proposals, branch events, drafts, and private/narrator-only information.
- Specify memory checkpoints, source provenance, conflict checks, and readback verification, with storage integration as future implementation work.
- Support both mediated external conversations and direct in-app conversations.
- Prepare controlled, mode-appropriate exports without silently installing or deploying them.

## Four independent settings

| Field | Values | Controls |
| --- | --- | --- |
| `interaction_mode` | `DIRECT` / `INTERMEDIATED` | Direct chat vs. user-mediated external replies and pairing |
| `canon_depth` | `MINIMAL_BEHAVIORAL` / `LIGHT_BACKGROUND` / `RICH_BACKGROUND` / `CUSTOM` | Amount of background expected |
| `interaction_type` | `CONVERSATION` / `ROLEPLAY` | Ordinary conversation vs. in-world roleplay conventions |
| `can_invent_background_canon` | `false` / `true` | Whether new, nonconflicting biographical facts may be **proposed**, never auto-approved |

The settings are orthogonal: changing one does not silently change another. There are no compulsory three-type presets.

## Canon, visual identity, and export safeguards

- The **approved canon ledger** is separate from the **approval queue**, the **active branch history**, and temporary drafts/working context. Generated content is not automatically permanent canon.
- A visual description and related image-generation prompt can be **proposed even when** `can_invent_background_canon` is `false`; appearance proposals still require applicable approval.
- For `DIRECT` builds, **never** produce external-service character-persona text/card exports or placeholder persona ZIPs. `INTERMEDIATED` builds may produce a target-specific persona export **only** when a release contract requires it.
- In `INTERMEDIATED` mode, selected replies and subsequent external messages may form *working* continuity, but do not prove provider submission. Rejected alternatives and unpaired output remain outside the active transcript.
- Roleplay knowledge boundaries, third-party agency, and private narration are respected. A Builder-only master or approval queue must not leak into a branch-neutral runtime snapshot.
- Default permanent-write policy: review the exact proposed patch and SHA-256, then separately authorize `APPLY PATCH <ID> <SHA256>`. Verify any write by reading back; never treat a checksum alone as evidence of factual truth or installation.

## Contents

This repo starter keeps the project's original filenames, without changing the supplied source content.

| Files | Purpose |
| --- | --- |
| `01_BUILDER_AGENT_INSTRUCTIONS.md` | Design-time Builder behavior and boundaries |
| `02_PERSONALITY_BUILD_WORKSHEET.md` | Intake for each new, explicitly selected personality |
| `03_PERSONALITY_CONFIGURATION_TEMPLATE.json` | Initial unconfigured personality JSON scaffold |
| `04_CANON_LEDGER_TEMPLATE.json` | Approved fact ledger scaffold |
| `05_APPROVAL_QUEUE_TEMPLATE.json` | Proposals, approvals, and patch authorization scaffold |
| `06_VISUAL_IDENTITY_TEMPLATE.md` | Physical description and image-prompt review |
| `07_BRANCH_CONTINUITY_TEMPLATE.json` | Branch-only turns, working continuity, and checkpoints |
| `08_RELEASE_POLICY.md` | Mode-gated exports, privacy, and release receipts |
| `09_ACCEPTANCE_CHECKLIST.md` | Engineering and release verification criteria |
| `11_PERSONALITY_CATALOG.json` | Empty, isolated personality registry (no default) |
| `12_PERSONALITY_ISOLATION_AND_BUILD_GUIDE.md` | Multi-identity build and isolation guide |
| `13_IMPORT_EXISTING_PERSONALITY_PROTOCOL.md` | Optional intake for an existing personality |
| `14_PERSONALITY_PLATFORM_PRODUCT_CHARTER.md` | Authoritative platform product charter |
| `15_PERSONALITY_PLATFORM_DEVELOPMENT_READ_PROTOCOL.md` | Mandatory read-first protocol and roadmap |
| `16_PERSONALITY_CONFIGURATION_SCHEMA.md` | Configuration and visual-identity schema |
| `SOURCE_CHECKSUMS.sha256` | Byte-integrity hashes of source and documentation files |
| `install_instructions.md` | How to set up a GitHub repo and a ChatGPT Project |

The numbering reflects the supplied baseline; no `10_...` file was supplied and none is inferred.

## Start here

1. Read [`install_instructions.md`](install_instructions.md) to make the GitHub repository and optionally configure a ChatGPT Project.
2. For any architecture, settings, canon, memory, export, or schema work, first reopen **`14_...`**, **`15_...`**, **`16_...`**, and **`11_PERSONALITY_CATALOG.json`**.
3. Choose **one explicit `personality_id`** before designing any personality; don't modify the empty catalog merely because a template exists.
4. Fill out the worksheet and prepare a **draft** namespaced configuration, canon ledger, proposal queue, and optional visual identity. Keep them separate from the shared platform files.
5. Review the exact changes, approvals, hashes, privacy boundaries, and acceptance checklist before any authorized persistent update or deployment.

## Suggested logical organization for future, separately authorized builds

```text
platform/                     # Shared design references, not personality canon
personalities/
  <personality_id>/
    configuration.json
    canon_ledger.json
    approval_queue.json
    visual_identity.md
    branches/<branch_id>/
    releases/<release_id>/
```

This is a **proposed layout**, not evidence that such folders, storage, or personalities already exist. Do not create an identity, branch, or canon from a template without separate user authorization.

## Safety and privacy

Prefer a **private repository**, especially if later versions contain identity data, personal conversation records, controlled-test information, or nonpublic canon. Do not commit API keys, tokens, private chats, external-party records, or unapproved personality claims. Review individual export contents before release. GitHub is version control, **not** automatically the active runtime's memory database or ChatGPT Project storage.

## Development status and verification

The platform charter and development protocol are design baselines; the configuration schema is a design reference. An actually deployed persistent-memory runtime, automated checkpoint system, adapters, and external-provider submission verification remain **unimplemented/unverified by this starter**. A successful GitHub commit verifies repository persistence only; it does not prove ChatGPT Project upload, personality installation, or active external-service behavior.

See `09_ACCEPTANCE_CHECKLIST.md` for the test matrix and `08_RELEASE_POLICY.md` for deployment status definitions (`DRAFT` → `CONTENT_REVIEWED` → `READY_FOR_MANUAL_INSTALL` → `INSTALLED_READBACK_VERIFIED`).

## License

No license has been supplied. Until the owner chooses a license, do not assume an open-source grant or permission to redistribute.
