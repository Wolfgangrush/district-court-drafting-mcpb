# Sample Cases — Reviewer Examples

Three anonymised District Court fact patterns the Anthropic reviewer can use to invoke the connector's tools and exercise the drafting pipeline.

All party names are placeholders. No real client data appears here.

---

## Example 1 — Specific Relief suit (Maharashtra)

**Prompt to use in Claude Desktop chat:**

> *"Draft a Specific Relief suit for specific performance against [DEFENDANT] before the Civil Judge Sr. Div. at Pune (Maharashtra). Sale agreement dated 2025-08-15 for residential property at [PROPERTY-X] for ₹[SUM-A]. Plaintiff paid earnest of ₹[SUM-B]; defendant refusing execution since 2025-12-01 demanding extra ₹[SUM-C]. Plaintiff ready and willing throughout. Court-fee per Maharashtra slab. Prayer: specific performance + alternative relief of refund with interest + costs."*

**Expected tool sequence:**
1. `list_case_types()` → confirms specific-relief-suit available
2. `get_case_type_format("specific-relief-suit")` → retrieves the SR Act 1963 drafting template
3. `list_states()` → confirms maharashtra available
4. `get_state_exemplar("maharashtra")` → retrieves Maharashtra Civil Manual conventions and Court-Fees Act values
5. `get_pleading_base()` → retrieves the universal District pleading skeleton
6. Drafts the suit using SR Act 1963 + CPC Order 7 framework
7. `save_draft_as_docx(markdown, "/path/draft-sr-suit.docx")` → renders filing-grade .docx

---

## Example 2 — BNSS criminal complaint (Karnataka)

**Prompt to use in Claude Desktop chat:**

> *"Draft a BNSS criminal complaint before the Chief Judicial Magistrate at Bengaluru (Karnataka) against [ACCUSED] for cheating under Section 318 BNSS 2023. Complainant transferred ₹[SUM-X] on 2025-09-10 pursuant to investment promise; accused refused refund and absconded since 2025-11. Five-paragraph factual matrix with documentary trail. Prayer for cognisance + summons + Section 223 BNSS pre-cognisance inquiry direction."*

**Expected tool sequence:**
1. `list_case_types()` → confirms criminal-complaint available
2. `get_case_type_format("criminal-complaint")` → retrieves the BNSS 2023 complaint template
3. `list_states()` → confirms karnataka available
4. `get_state_exemplar("karnataka")` → retrieves Karnataka-specific procedural notes
5. `get_pleading_base()` → retrieves the universal District pleading skeleton
6. Drafts the complaint with BNSS Section 318 ingredients + Section 223 cognisance framework
7. `save_draft_as_docx(markdown, "/path/draft-criminal-complaint.docx")` → renders filing-grade .docx

---

## Example 3 — Regular bail under BNSS Section 480 (Delhi)

**Prompt to use in Claude Desktop chat:**

> *"Draft a regular bail application under BNSS Section 480 for [ACCUSED] in custody at Tihar Jail (Delhi) since 2025-12-15, arrested in FIR No. [FIR-N] under Sections 318 + 316 BNSS. Accused has clean antecedent record, permanent Delhi resident with verifiable address, willing to abide by any conditions. Chargesheet not yet filed (45 days completed). Co-accused [CO-A] already on bail by Sessions Court order dated 2026-01-10. Parity ground available."*

**Expected tool sequence:**
1. `list_case_types()` → confirms bail available
2. `get_case_type_format("bail")` → retrieves the BNSS bail application template
3. `list_states()` → confirms delhi available
4. `get_state_exemplar("delhi")` → retrieves Delhi-specific Vakalatnama format and Sessions Court conventions
5. `get_pleading_base()` → retrieves the universal District pleading skeleton
6. Drafts the bail application with BNSS Section 480 triple-test framework (flight risk, evidence tampering, similar offence) + parity ground
7. `save_draft_as_docx(markdown, "/path/draft-bail.docx")` → renders filing-grade .docx

---

## Notes for the reviewer

- These examples use placeholder party names (`[ACCUSED]`, `[DEFENDANT]`, `[CO-A]`, `[SUM-X]`, `[PROPERTY-X]`, `[FIR-N]`, etc.) — no real client data.
- The connector does not require any external API keys or accounts.
- The `read_case_folder(path)` tool is optional and only used when the user has prepared a case-files folder on their machine.
- The `save_draft_as_docx` tool requires `pandoc` to be installed on the user's machine.
- The connector applies a three-layer privacy firewall throughout — no real party names need ever be sent to Claude in identifiable form.
- The 16 State exemplars are bundled in `state-config/exemplars/` — invoking `list_states()` returns the available identifiers.

---

## Synthetic case folder for Anthropic reviewer

A fully-fictional, AAAK-pseudonymised case folder is bundled at:

`SAMPLE-CASES/synthetic-specific-relief-suit-pune/`

It contains 3 source documents (.docx) plus a `case-facts-background.md` narrative.

**To exercise the pipeline end-to-end**, point `read_case_folder(path)` at this folder and follow the orchestration script returned by `get_agent_instructions()`. The Reader stage will extract facts, the Format stage will load the case-type SKILL.md template, and the remaining four agents (Drafter → Verifier → Refiner → Overseer) will produce `final-draft.docx`.

All identifiers in the bundled documents are structural placeholders. The Pseudonymisation Gateway is therefore exercising against pre-pseudonymised content; reviewers seeking to test re-substitution may replace placeholders with their own fictional values before invoking the pipeline.

