# Wolfgang Rush — District Court Drafting

**MCPB Desktop Extension** for drafting pleadings before District Courts across India.

State-config-aware: 16 State exemplars covering ~25 grouped jurisdictions. Designed for Indian advocates using **Claude Desktop App**. Local-execution. Zero data collection.

> *Also available as a Claude Code Plugin (for developers using the Claude Code CLI):*
> *[github.com/Wolfgangrush/district-court-drafting-litigation](https://github.com/Wolfgangrush/district-court-drafting-litigation)*

---

## What this connector does

Exposes the Wolfgang Rush six-agent District drafting pipeline as MCP tools that Claude can orchestrate from a Claude Desktop chat. Drafts the following case types:

### Civil-side

| Case type | Statutory anchor |
|---|---|
| Specific Relief suit | Specific Relief Act 1963 |
| Plaint + Written Statement | CPC 1908 Order 6, 7, 8 |
| Petition | CPC / local rules |
| Application (interlocutory) | CPC Order 39 / Order 1 / Order 41 |
| Pleadings (generic) | CPC Order 6 |

### Criminal-side

| Case type | Statutory anchor |
|---|---|
| Criminal complaint | BNSS 2023 (replacing CrPC 1973) |
| Criminal revision | BNSS / Sessions / District Judge revisional jurisdiction |
| Bail application | BNSS Section 480 / 483 |
| Anticipatory bail | BNSS Section 482 |
| BNSS 313 / 351 statement | BNSS 2023 |

### State exemplars (16 grouped jurisdictions)

`andhra-pradesh-telangana` · `bihar-jharkhand` · `delhi` · `gujarat` · `jammu-kashmir-ladakh` · `karnataka` · `kerala` · `madhya-pradesh-chhattisgarh` · `maharashtra` · `north-east-states` · `odisha` · `punjab-haryana-chandigarh` · `rajasthan` · `tamil-nadu` · `uttar-pradesh-uttarakhand` · `west-bengal`

Each exemplar captures local Civil Manual conventions, Court-Fees Act values, Vakalatnama format, and language requirements.

---

## Install

1. Open **Claude Desktop App**
2. **Settings → Extensions → Install Extension**
3. Select `wolfgang-district-court-drafting.mcpb`
4. Enable the extension
5. Start a new chat

## System requirements

- macOS, Windows, or Linux with Claude Desktop App ≥ 0.10.0
- Python ≥ 3.10 (Claude Desktop App bundles uv runtime automatically)
- **`pandoc`** for `.docx` output (`brew install pandoc` on macOS · `apt-get install pandoc` on Linux · download from pandoc.org on Windows)
- **`pdftotext`** for PDF reading (`brew install poppler` on macOS · `apt-get install poppler-utils` on Linux)

## Usage

In a Claude Desktop chat, describe what you want to draft and specify the State. Claude will discover and call the connector's tools as needed.

Example prompts:

- *"Draft a Specific Relief suit for specific performance against [DEFENDANT] in Maharashtra. Sale agreement dated 2025-08-15 for ₹[SUM-X], defendant refusing execution since 2025-12. Plaintiff ready and willing. Court-fee for Maharashtra slab."*
- *"Draft a BNSS criminal complaint against [ACCUSED] for cheating under Section 318 BNSS in Karnataka, with five-paragraph factual matrix and prayer for cognisance."*
- *"Draft a regular bail application under BNSS Section 480 for [ACCUSED] arrested under Section 318 BNSS, in custody for 45 days, no prior conviction."*

## Tools

| Tool | Purpose |
|---|---|
| `list_case_types` | Discover the 10 available District Court case types |
| `get_case_type_format` | Retrieve the drafting template for a case type |
| `get_agent_instructions` | Retrieve instructions for a stage in the six-agent pipeline |
| `get_pleading_base` | Retrieve the universal District pleading skeleton |
| `list_states` | Discover the 16 State exemplars bundled |
| `get_state_exemplar` | Retrieve State-specific Civil Manual + Court-Fees Act content |
| `read_case_folder` | Read files in a case folder for fact extraction |
| `save_draft_as_docx` | Render markdown as filing-grade .docx |

## Privacy

This connector collects **zero** user data. All processing happens on the user's machine. The publisher (Wolfgang Rush) never receives any user data.

Three-layer privacy firewall: **L1 substitution** → **L2 LLM-blind** → **L3 re-substitution**.

Canonical privacy policy: **<https://wolfgangrush.github.io/privacy/>**

## Confidentiality and professional privilege

Case-folder contents passed to this connector may include material attracting attorney-client privilege under **Section 132 of the Bharatiya Sakshya Adhiniyam 2023** / **Section 126 of the Indian Evidence Act 1872**. The user remains professionally responsible consistent with Bar Council of India rules and client-engagement terms.


## ⚠️ AI verification disclaimer · 🔒 Pseudonymisation procedure

> **⚠️ AI can make mistakes — please verify the information before filing.**
> Every draft produced by this connector is a STARTING POINT. The Verifier
> agent runs an anti-hallucination firewall and the Overseer agent runs an
> opposing-counsel review, but neither replaces an advocate's independent
> verification of statutory references, citation accuracy, factual fidelity,
> and Registry-formatting compliance with the user's High Court / forum.
> The advocate filing the pleading remains responsible for the contents.
>
> **🔒 Protected by pseudonymisation procedure.** The Reader agent applies a
> domain-specific privacy firewall as the first step of the pipeline — party
> names, addresses, identifying numbers (FIR / CR / Crime / Suit / Diary /
> SLP / lower-court case numbers), PAN / Aadhaar references, financial
> figures, witness names, and statutory-notice references are substituted
> with structural placeholders BEFORE any downstream agent sees the facts.
> The Drafter, Verifier, Refiner, and Overseer agents process placeholders
> only. Real values are re-substituted at the final docx render step on the
> user's local machine. No real identifying data leaves the case folder.

## License

MIT. See LICENSE.

## Publisher

**Rushikesh R. Mahajan**, Advocate, Bombay High Court (Nagpur Bench), publishing as **Wolfgang Rush**.

Contact: advrushikeshravindramahajan@gmail.com

## Source

<https://github.com/Wolfgangrush/district-court-drafting-mcpb>

## Sample cases

See `SAMPLE-CASES/` for three anonymised fact patterns the reviewer can use to invoke the tools.
