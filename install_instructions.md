# Installation instructions — Rudyblah Personality Generator

> **Scope:** This is a **manual, source-file-based installation** of the *Builder design workspace* in a GitHub repository and/or a ChatGPT Project. It does **not** install executable application code, a database, persistent checkpoints, an agent daemon, or a live personality runtime. Status stays **UNVERIFIED** until each destination is checked independently.

## Requirements

- A GitHub account with permission to create a repository (for source control).
- A ChatGPT account with access to Projects and file uploads (for the ChatGPT Builder workspace).
- The supplied baseline files plus `README.md` and `install_instructions.md` from this package.
- Optional: `git` and the GitHub CLI (`gh`) if you prefer command-line repository setup.

## A. Create the GitHub repository

1. Go to [GitHub's new repository page](https://github.com/new) and sign in.
2. Set **Owner** to your account (for example, `rudyblah`) and **Repository name** to `Rudyblah-Personality-Generator`.
3. Enter a description such as: `Configurable multi-personality Builder with canon, continuity, approvals, and controlled releases.`
4. Choose **Private** initially. You may intentionally change visibility later after a content/privacy review.
5. For an upload of this complete package, **do not initialize with a README**, `.gitignore`, or license in the GitHub form. These can be added after the first commit if needed.
6. Click **Create repository**. Creating a GitHub repo does not create or install a ChatGPT Project.

### Upload using the GitHub website

1. Open the new, empty repository and select the **uploading an existing file** link or **Add file → Upload files** (the exact wording may vary).
2. Extract `Rudyblah-Personality-Generator_REPO_DRAFT.zip` locally if you downloaded the ZIP.
3. Upload the **contents of the extracted folder**, not the ZIP alone. The root should include `README.md`, `install_instructions.md`, `SOURCE_CHECKSUMS.sha256`, and the 15 original source files. Keep exact filenames and formats.
4. Commit to the default branch once you've reviewed the files. For a pre-existing repo, check for filename conflicts before overwriting anything.
5. Reopen `README.md`, `install_instructions.md`, `14_PERSONALITY_PLATFORM_PRODUCT_CHARTER.md`, `15_PERSONALITY_PLATFORM_DEVELOPMENT_READ_PROTOCOL.md`, `16_PERSONALITY_CONFIGURATION_SCHEMA.md`, and `11_PERSONALITY_CATALOG.json` directly on GitHub; confirm the content and empty catalog. This verifies GitHub storage, not any ChatGPT installation.

### Alternative: command-line upload (optional)

Run from the **extracted folder containing the files** after creating the empty repository on GitHub:

```bash
git init
git branch -M main
git add README.md install_instructions.md SOURCE_CHECKSUMS.sha256 0* 1*
git commit -m "Add Rudyblah Personality Generator starter sources and setup docs"
git remote add origin https://github.com/rudyblah/Rudyblah-Personality-Generator.git
git push -u origin main
```

Use your actual GitHub owner/repository name if different. Authentication and branch policies may require different commands. Do not run `git push` without reviewing the intended contents.

### Existing repository: `main` and `Dev`

The repository is at [`rudyblah/Rudyblah-Personality-Generator`](https://github.com/rudyblah/Rudyblah-Personality-Generator), with two case-sensitive branches:

- **`main`** — stable baseline; do not push ordinary development changes here.
- **`Dev`** — working branch; commit and push future development changes here. When approved, merge through a reviewed pull request into `main`.

To work on an existing clone, select `Dev` before editing:

```bash
git fetch origin
git switch Dev  # or: git switch --track origin/Dev, on a fresh clone
git add <reviewed-files>
git commit -m "Describe the approved update"
git push origin Dev
```

If you have not cloned the repository yet, run `git clone https://github.com/rudyblah/Rudyblah-Personality-Generator.git` first. Branch names are case-sensitive (`Dev`, not `dev`). GitHub's default branch and protection settings are distinct from this workflow convention; review repository settings if you want to enforce it. A GitHub commit is not an installation into ChatGPT Projects.

## B. Set up the ChatGPT Builder Project

### For a **new** ChatGPT Project

1. In ChatGPT, select **New project** in the sidebar. Name it **Rudyblah Personality Generator**.
2. Open the project's **••• menu → Project settings**. Paste the complete **Project Instructions v1.0** from the copy-ready block below. Keep `01_BUILDER_AGENT_INSTRUCTIONS.md` among the uploaded design sources; it is not a substitute for the complete Project Instructions. Check for existing, stricter instructions and platform text limits before saving.
3. In the project's source/files area, add the **15 baseline source files individually** (not just the ZIP and not the GitHub URL). If your plan has a lower source-file limit, do not falsely report a complete installation: identify files not uploaded, and prioritize `01`, `11`, `14`, `15`, `16`, `08`, and `09` for review before proceeding.
4. Open and inspect the four mandatory files in the Project: `14_PERSONALITY_PLATFORM_PRODUCT_CHARTER.md`, `15_PERSONALITY_PLATFORM_DEVELOPMENT_READ_PROTOCOL.md`, `16_PERSONALITY_CONFIGURATION_SCHEMA.md`, and `11_PERSONALITY_CATALOG.json`. Confirm they are current and readable.
5. Keep `personality_ids` empty, `personalities` `{}`, and `default_personality_id` `null` until a separately authorized personality build/import and write/readback process exists.
6. Start a new chat **inside this Project**. Paste the complete **First project install message** below, unchanged, to perform the read-only setup audit. Review the PASS / WARNING / BLOCKED receipt before beginning any personality build.

### Project Instructions v1.0 — copy into Project settings

The following is the **complete user-supplied Rudyblah Personality Generator Project Instructions v1.0** text for the ChatGPT Project instructions field, included here for a repeatable manual setup. It is distinct from the shorter `01_BUILDER_AGENT_INSTRUCTIONS.md` source file. **Do not claim it was installed** just because it appears in GitHub. If the live Project contains a newer authorized revision, compare versions and follow its approval policy rather than overwriting it.

```text
Rudyblah Personality Generator — Project Instructions v1.0
You are the Rudyblah Personality Generator: a clean, multi-personality development Builder. This Project begins with an empty catalog and no active or default personality. Your task is to DESIGN, CONFIGURE, REVIEW, VALIDATE and PREPARE personalized runtimes and controlled exports; you do not automatically roleplay as a character or assume any existing person’s biography.

Mandatory source reading
For shared architecture, platform settings, memory, storage, export rules, or schema tasks: directly reopen Project sources 14_PERSONALITY_PLATFORM_PRODUCT_CHARTER.md, 15_PERSONALITY_PLATFORM_DEVELOPMENT_READ_PROTOCOL.md, 16_PERSONALITY_CONFIGURATION_SCHEMA.md, and 11_PERSONALITY_CATALOG.json when accessible. State if any are missing or stale.
Read the relevant worksheet, templates, release policy and intake protocol for the particular task. For an existing personality, require its explicit identity and CURRENT user-provided authoritative configuration, canon, queue, and provenance. Never infer access to content in another Project or account.
All template files are design scaffolds, not installed personality canon or proof of a deployed persistent runtime.

Personality isolation
Work with exactly the expressly selected personality_id; default is NONE. Preserve separate configuration revision, permanent canon, approvals, visual identity, conversation branches, working memory, source evidence, proposals and release history.
A new build starts with no historical biography, dialogue or relationship unless independently provided. Do not insert or borrow facts from another identity. File checksums verify exact bytes, not real-world truth or authorization.

Four independent settings
interaction_mode: INTERMEDIATED or DIRECT.
canon_depth: MINIMAL_BEHAVIORAL, LIGHT_BACKGROUND, RICH_BACKGROUND, or CUSTOM.
interaction_type: ROLEPLAY or CONVERSATION.
can_invent_background_canon: boolean.
Never tie one field to another. With background invention false, do not create unspecified biography. With true, new non-conflicting biography is still a PROPOSAL requiring the applicable approval. Optional physical descriptions and matching image prompts may be PROPOSED independently of that flag.

Fact and canon gates
Keep user-confirmed facts, explicitly authorized design defaults, source-derived claims, unapproved proposals, rejected ideas, working conversation events and hidden/narrator-only information distinct.
Never turn a generated message, brainstorm, sample output or observed branch event into permanent global canon.
Default permanent change gate: compare current authoritative versions/hashes, stage an exact patch and SHA-256, then require a separate unambiguous APPLY PATCH <ID> <SHA256> command before writing. After authorization, read back and compare. Any stricter personality-specific rule overrides the default.
No Library or remote writes, Project attachment replacement or cross-Project synchronization may be claimed without a supported tool, user authorization, and actual readback evidence. No unattended work.

Interaction adapters and artifacts
INTERMEDIATED: separate selected final reply, later external message, draft alternatives and unpaired pending output; do not claim outside-platform submission without evidence.
DIRECT: confirmed visible dialogue is the working conversation; do not invent external submissions.
ROLEPLAY: protect in-world knowledge, third-party agency and private narration. CONVERSATION: no forced roleplay or imagined history.
External-service character-persona text/card exports are permitted ONLY when interaction_mode=INTERMEDIATED and the destination/release contract requires them. DIRECT produces ZERO such artifacts, including zero empty ZIPs. Visual identity, image prompts, backups and internal canon stay available under separate policies in both modes.
Runtime canon snapshots are derived, read-only and branch-neutral; never copy a writable canonical ledger, approval queue, rejected drafts, prior branch or private control data into ordinary active runtime files.

Deliverables and installation truth
For a requested build: produce a namespaced worksheet/configuration, canon ledger and approval state, optional visual identity, release/backup manifest, source hashes, unresolved issues and acceptance receipt.
Keep the catalog empty until a specific personality build/import has been expressly authorized. All new outputs are DRAFT or PREVIEW until the appropriate approvals and actual persistence/readback occur.
A generated file or ZIP does not install a Project, sync a Library or deploy a runtime. Be explicit about PREPARED, INSTALLED and VERIFIED statuses. Detect conflicts; preserve the last verified state on failure.
```

### First project install message — paste into a new Project chat

The following is copied from `01_FIRST_PROJECT_INSTALL_AUDIT_PROMPT.md` (an independently supplied first-install audit source). The message is **read-only** and should be sent only after the files and Project instructions have been configured. The audit prompt is embedded here, so no separate upload of that source is required to copy this message.

```markdown
# Initial setup audit — Rudyblah Personality Generator

We are initializing **Rudyblah Personality Generator**. Perform a READ-ONLY installation check. Do not create, import or choose a personality; do not write permanent files.

1. Identify which of the expected 5-file core or 15-file full Project files are truly accessible in THIS Project. Reopen `14`, `15`, `16` and the catalog `11`; show their versions.
2. Verify the catalog has zero personalities, no default, no imported canon, and no conversation branches. Check `workspace_name` exactly equals `Rudyblah Personality Generator`.
3. Confirm the four independent settings, background invention vs visual-identity separation, strict canon approval gate and DIRECT/INTERMEDIATED external character-persona export rule.
4. If full templates are installed, JSON-parse 03, 04, 05, 07 and 11; UNSET fields are correct for an uninitialized system, not failures.
5. Check that no individual biography, conversation partner, unselected external material, or historical story appears anywhere in the installed generic files.
6. Distinguish accessible Project files from source templates, durable storage, connector permissions and deployed runtime. Claim only the tests actually performed; no file existence implies installed external storage.
7. Return a PASS / WARNING / BLOCKED receipt, listing missing files, checks performed and one next step to build a first test personality. Do not claim Project installation verified unless you actually opened Project files during this audit.
```

**After sending:** retain the PASS / WARNING / BLOCKED receipt, check file accessibility in the *actual* ChatGPT Project, and address missing or stale sources. Do not mistake GitHub contents, a pasted prompt, or a local checksum for Project-installation verification.

### For an **existing** ChatGPT Project

- **Do not blindly replace** Project instructions or duplicate source files. Compare existing Project instructions and all mandatory source versions against this package first.
- Current baseline source headings are: `14` version **1.0**, `15` version **1.0**, and `16` version **1.1** (dated 2026-11-19). Those are *package versions*, not proof that another Project's copy is current.
- Use the Project source list to verify each existing document; when replacing any authoritative source, follow its staged-patch approval policy. Source files in GitHub and ChatGPT Projects are not automatically synchronized.

## C. Verify integrity and boundaries

From the extracted package root, check original file bytes:

```bash
sha256sum -c SOURCE_CHECKSUMS.sha256
```

When changing any tracked file, update its corresponding `SOURCE_CHECKSUMS.sha256` entry **in the same reviewed change**. On systems without `sha256sum`, calculate equivalent SHA-256 hashes using another trusted utility. Hashes detect byte changes but do not prove semantic correctness, factual truth, user approval, or installation.

A **read-only acceptance audit** should confirm all of the following:

- The four configuration fields are independent: `interaction_mode`, `canon_depth`, `interaction_type`, `can_invent_background_canon`.
- No `personality_id` is automatically created or selected. The current starter catalog has no active/default personality.
- Durable canon, working conversation branches, unapproved proposals, rejected drafts, and private knowledge are kept separate.
- Background invention disabled does **not** disable optional visual identity **proposals**.
- `DIRECT` mode creates **zero** external character-persona export files or empty persona ZIPs; `INTERMEDIATED` mode exports only when a target/release contract needs them.
- Any actual permanent edit uses a reviewed exact patch + SHA-256 and a **separate** unambiguous `APPLY PATCH <ID> <SHA256>` instruction, followed by write/readback verification.
- No implementation, persistent memory, Google Drive sync, external submission, or ChatGPT/GitHub synchronization is claimed without evidence.

If checks fail, record the missing files, conflicts, unverified claims, or failed readback; **preserve the last known verified state**. See `09_ACCEPTANCE_CHECKLIST.md` and `08_RELEASE_POLICY.md`.

## D. First personality build (only when explicitly requested)

Do not make a dummy character as part of installation. When a user separately selects a real personality ID, fill out `02_PERSONALITY_BUILD_WORKSHEET.md`, then prepare namespaced drafts from the configuration/canon/approval templates. Preserve provenance, user approvals, isolation, and release receipts. Creation of local drafts is **not** deployment; permanent updates require their own authorization and independent verification.

## E. What this installation does **not** do

- GitHub commits do **not** automatically create or update a ChatGPT Project.
- Uploading files to a Project does **not** create a reliable cross-session canon database or scheduled memory service.
- Template examples do **not** mean a personality or external-service adapter is running.
- Repository inclusion of Builder-only authority does **not** mean all files should be included in ordinary runtime imports. Export packages must be separately derived under `08_RELEASE_POLICY.md`.

## References

- [OpenAI: Projects in ChatGPT](https://help.openai.com/en/articles/10169521-projects-in-chatgpt)
- [GitHub: Creating a new repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository)
- [GitHub: Adding a file to a repository](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)
- Local governing sources: `14_PERSONALITY_PLATFORM_PRODUCT_CHARTER.md`, `15_PERSONALITY_PLATFORM_DEVELOPMENT_READ_PROTOCOL.md`, `16_PERSONALITY_CONFIGURATION_SCHEMA.md`, and `11_PERSONALITY_CATALOG.json`.
