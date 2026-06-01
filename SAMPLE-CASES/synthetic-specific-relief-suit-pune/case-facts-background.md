# Case Facts Background — Suit for Specific Performance (Maharashtra)

All party names, addresses, monetary figures, property descriptions, and ancillary dates are fictional placeholders.

## Parties

- **Plaintiff:** [Plaintiff-A], aged about [Plaintiff-Age-Placeholder] years, resident of [Plaintiff-Address-Placeholder]. Purchaser under the Sale Agreement.
- **Defendant:** [Defendant-A], aged about [Defendant-Age-Placeholder] years, resident of [Defendant-Address-Placeholder]. Vendor / owner of the suit property.

## Suit property

- Residential property at [Property-Address-Placeholder], Pune, Maharashtra.
- Area: [Property-Area-Placeholder] sq. ft. carpet area.
- Survey / CTS No.: [Survey-CTS-Placeholder].

## Contract terms

- Agreed consideration: Rs. [Sum-A-Placeholder]/-
- Earnest money paid: Rs. [Sum-B-Placeholder]/- (paid 15 August 2025 — see `02-earnest-money-receipt-2025-08-15.docx`)
- Balance payable: Rs. [Sum-Balance-Placeholder]/- (due on or before 30 November 2025)
- Time-essence clause present (Clause 4 of Agreement)
- Specific-performance default clause present (Clause 7)

## Chronology

- **15 August 2025** — Sale Agreement executed (see `01-sale-agreement-2025-08-15.docx`); earnest money of Rs. [Sum-B-Placeholder]/- paid (see `02-earnest-money-receipt-2025-08-15.docx`).
- **15 August 2025 – 30 November 2025** — Plaintiff repeatedly demanded execution of the Sale Deed; communicated readiness and willingness to pay the balance via emails dated [Email-1-Date-Placeholder], [Email-2-Date-Placeholder].
- **01 December 2025** — Defendant issues refusal letter demanding additional Rs. [Sum-C-Placeholder]/- over the agreed consideration (see `03-vendor-refusal-letter-2025-12-01.docx`).
- **[Date-Placeholder]** — Plaintiff issues legal notice through counsel calling upon Defendant to execute and register the Sale Deed at the originally agreed consideration. No response.
- **[Suit-Filing-Date-Placeholder]** — Plaintiff approaches the Civil Judge Sr. Div., Pune for specific performance.

## Forum and case type

- **Forum:** Civil Judge Sr. Div., Pune (pecuniary jurisdiction satisfied by sale-consideration value).
- **Case type:** `specific-relief-suit`.
- **State:** Maharashtra (court-fee per Bombay Court-Fees Act 1959).
- **Statutory framework:** Sections 10, 16, 20 of the Specific Relief Act 1963 (as amended in 2018 — specific performance is now a rule, not a discretionary remedy, subject to readiness-and-willingness + non-applicability of bars under Section 16).

## Reliefs sought

1. Decree of specific performance directing the Defendant to execute and register the Sale Deed in favour of the Plaintiff in respect of the suit property at the originally agreed consideration of Rs. [Sum-A-Placeholder]/- against payment of the balance consideration.
2. In the alternative — refund of earnest money of Rs. [Sum-B-Placeholder]/- with interest at [Interest-Rate-Placeholder]% per annum from 15 August 2025 till payment + damages of Rs. [Damages-Placeholder]/- for breach of contract.
3. Permanent injunction restraining the Defendant from alienating, encumbering, or parting with possession of the suit property pending disposal of the suit.
4. Costs of the suit.

## Ingredient check (Verifier-stage)

- ✅ Concluded contract proved — written Sale Agreement on record.
- ✅ Consideration proved — Rs. [Sum-A-Placeholder]/- (Clause 1 of Agreement).
- ✅ Earnest money paid — receipt at `02-earnest-money-receipt-2025-08-15.docx`.
- ✅ Plaintiff's readiness and willingness — to be averred in plaint (Section 16(c) SR Act 1963) + supported by emails and notice.
- ✅ Defendant's refusal — written letter at `03-vendor-refusal-letter-2025-12-01.docx`.
- ✅ Limitation — Article 54 Limitation Act 1963 (3 years from date fixed for performance / refusal). Filing well within time.
- ✅ Court-fee — ad valorem on the consideration under Bombay Court-Fees Act.

## How to use this fixture

1. Point `read_case_folder(path)` at this directory.
2. Reader extracts facts from the 3 `.docx` files plus this `case-facts-background.md`.
3. Call `get_case_type_format("specific-relief-suit")` for the SR Act drafting template.
4. Call `get_state_exemplar("maharashtra")` for Maharashtra Civil Manual + Bombay Court-Fees Act conventions.
5. The remaining 5 agents (Format → Drafter → Verifier → Refiner → Overseer) run end-to-end to produce `final-draft.docx` containing the Plaint (Cause Title, Parties, Plaint Paragraphs, Cause of Action, Reliefs, Verification, List of Documents).
