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

## B. Set up the ChatGPT Builder Project

### For a **new** ChatGPT Project

1. In ChatGPT, select **New project** in the sidebar. Name it **Rudyblah Personality Generator**.
2. Open the project's **••• menu → Project settings** and add Builder-specific instructions. Use the content of `01_BUILDER_AGENT_INSTRUCTIONS.md` as the design-time starting point, subject to any text limits or stricter existing instructions. The primary charter, protocol, schema, catalog, and approval requirements still govern.
3. In the project's source/files area, add the **15 baseline source files individually** (not just the ZIP and not the GitHub URL). If your plan has a lower source-file limit, do not falsely report a complete installation: identify files not uploaded, and prioritize `01`, `11`, `14`, `15`, `16`, `08`, and `09` for review before proceeding.
4. Open and inspect the four mandatory files in the Project: `14_PERSONALITY_PLATFORM_PRODUCT_CHARTER.md`, `15_PERSONALITY_PLATFORM_DEVELOPMENT_READ_PROTOCOL.md`, `16_PERSONALITY_CONFIGURATION_SCHEMA.md`, and `11_PERSONALITY_CATALOG.json`. Confirm they are current and readable.
5. Keep `personality_ids` empty, `personalities` `{}`, and `default_personality_id` `null` until a separately authorized personality build/import and write/readback process exists.
6. Start a new project chat and ask for a **read-only Builder installation audit**: list the accessible files and versions, confirm the empty catalog, explain the four settings, and report gaps without creating any personality or mutating sources.

### For an **existing** ChatGPT Project

- **Do not blindly replace** Project instructions or duplicate source files. Compare existing Project instructions and all mandatory source versions against this package first.
- Current baseline source headings are: `14` version **1.0**, `15` version **1.0**, and `16` version **1.1** (dated 2026-11-19). Those are *package versions*, not proof that another Project's copy is current.
- Use the Project source list to verify each existing document; when replacing any authoritative source, follow its staged-patch approval policy. Source files in GitHub and ChatGPT Projects are not automatically synchronized.

## C. Verify integrity and boundaries

From the extracted package root, check original file bytes:

```bash
sha256sum -c SOURCE_CHECKSUMS.sha256
```

On systems without `sha256sum`, calculate equivalent SHA-256 hashes using another trusted utility. Hashes detect byte changes but do not prove semantic correctness, factual truth, user approval, or installation.

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
