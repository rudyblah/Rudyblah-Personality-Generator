# Template acceptance and first-build checklist

This is an engineering review checklist, not evidence that runtime tests have run.

- [ ] **Four independent settings:** each valid and intentional; changing one does not change the others.
- [ ] **No fixed taxonomy:** builds are not limited to a fixed three-type taxonomy or a hard-coded reference character.
- [ ] **No borrowed biography:** the new personality contains no other personality’s background, past conversations, private data or equipment unless independently supplied and approved for that personality.
- [ ] **Background flag:** when false, no invented history; when true, suggestions remain PENDING until approval.
- [ ] **Approval trail:** user-confirmed facts, user-authorized defaults and AI proposals have separate provenance; no unapproved fact is in active permanent canon.
- [ ] **Visual identity:** proposal permitted with background flag false; description/prompt coherent; approved traits preserved; style-only edits do not mutate identity.
- [ ] **DIRECT + RICH_BACKGROUND + ROLEPLAY + true:** zero external character-persona files, despite rich backstory and invention permission.
- [ ] **INTERMEDIATED + MINIMAL_BEHAVIORAL + CONVERSATION + false:** external character-persona export only when required by target, with no invented history.
- [ ] **Intermediated pairing:** selected final response and later external turn may be working dialogue; superseded drafts excluded; last unpaired output stays pending; external submission proof not fabricated.
- [ ] **Direct history:** direct visible exchanges become working active history without external mediation.
- [ ] **Roleplay knowledge boundaries:** private thoughts, narrator-only facts and third-party decisions are not leaked into character knowledge.
- [ ] **Memory separation:** permanent canon, branch facts, working continuity, pending drafts and provenance are independent.
- [ ] **Persistence:** checksum, content readback, stale-version/conflict handling and rollback behavior demonstrated for any claimed storage integration; failures preserve prior verified state.
- [ ] **Release:** correct artifact gate, privacy audit, manifest integrity, installation state and manual delivery instructions.
- [ ] **No unapproved writes:** staged/preview/template work did not mutate Library, Projects, or any existing personality’s canon.

- [ ] **Multiple identities:** two distinct `personality_id` values can coexist in the catalog without sharing canon, approval IDs, branch history, or release artifacts.

## Suggested first regression examples

1. DIRECT + MINIMAL_BEHAVIORAL + CONVERSATION + false → no invented backstory or character-card export; optional visual proposal allowed.
2. DIRECT + RICH_BACKGROUND + ROLEPLAY + true → may suggest history but cannot auto-approve it; no external character-card export.
3. INTERMEDIATED + LIGHT_BACKGROUND + ROLEPLAY + false → may package target-required external persona text; rejected drafts excluded from active transcript.
4. INTERMEDIATED + CUSTOM + CONVERSATION + false → no compulsory roleplay or invented lore; approval and export gates still work.