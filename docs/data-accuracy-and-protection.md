# Data Accuracy, Source Trust & Text Protection

**English** · [العربية](./data-accuracy-and-protection.ar.md)

> [Organization Overview](../README.md) · [AI Safety Principles](./ai-governance.md) · [Brand Assets](https://github.com/mishkaah/brand)

---

## 1. Mission: Preservation, Never Authorship

Mishkaah exists to preserve and present foundational Islamic texts with rigorous scholarly fidelity. We do not author, synthesize, or paraphrase religious content, and no automated model is permitted to alter or invent sacred wording, chains of transmission (*asanid*), or scholarly rulings.

---

## 2. Strict 5-Point Trusted Source Criteria

Every primary text, commentary, lexicon, or biographical entry must trace to a source that satisfies all five non-negotiable qualification criteria:

1. **Tangible & Publicly Accessible Medium**: The work must exist as a circulated printed book or critical scholarly edition (*Tahqiq*), or in a recognized public institutional digital archive open to independent inspection. Oral attributions and private claims are inadmissible.
2. **Complete Bibliographic Coordinates**: Every entry records the canonical title, author, critical editor (*Muhaqqiq*), publisher, publication year, and exact volume/page or stable archive reference.
3. **Immutability & Permanence**: Sources must be physically fixed or permanently archived. Mutable blogs, social media posts, and unarchived web pages that can be silently edited or deleted are strictly rejected.
4. **Scholarly Consensus & Accreditation**: New editions and contemporary works are admitted only after deliberate scholarly evaluation and consensus; flawed or misprinted editions are deprecated and replaced.
5. **Traceable Provenance & Clear Standing**: Licensing or public-domain status and direct witness provenance are documented before any text unit enters verified production builds.

---

## 3. Universal Two-Person Human Review Rule

Automated checks verify structure, invariants, and cryptographic seals, while scholarly accuracy is protected by human accountability:

- **Adder + Mandatory Independent Human Reviewer**: Every new source qualification, text addition, or correction requires two distinct human participants — the **Adder** who prepares the change and a **Mandatory Independent Human Reviewer** who collates it against the accredited printed witness.
- **Zero Solo or Automated Approvals**: No contributor may approve or merge their own submission, and no bot or AI system may act as a reviewer.

---

## 4. 5-Layer External Trust & Digital Sanad Architecture

To make textual authenticity verifiable by any scholar or reader outside Mishkaah, trust is structured across five transparent layers:

### Layer 1: Direct Printed Page Witness + Archive Link
Every record binds directly to its accredited printed edition (publisher, editor, volume, and page) and, where available, a stable public digital archive link so anyone can open the physical or archived page and compare word for word.

### Layer 2: Honest 4-Tier Maturity Badges
Every text and source carries an honest verification tier rather than masking unreviewed material as finished:

| Tier | Meaning | Production Build Inclusion |
| :--- | :--- | :--- |
| **Tier 1 — Cryptographically Sealed** | Sacred Quranic text locked by immutable per-Surah SHA-256 digests | **Included** |
| **Tier 2 — Dual-Verified Edition** | Source and text collated and approved under the Two-Person Human Review Rule | **Included** |
| **Tier 3 — Under Scholarly Review** | Seeded or undergoing active collation; awaiting independent human sign-off | **Excluded** |
| **Tier 4 — Quarantined / Untrusted** | Unverified, disputed, or flagged for source replacement | **Strictly Excluded** |

Quarantined and untrusted data is **never** shipped in production builds.

### Layer 3: Immutable Two-Person Audit Trail
Every accepted change preserves permanent attribution for both the Adder and the Independent Human Reviewer in version history, ensuring clear chain-of-custody (*Sanad*) accountability from printed edition to published release.

### Layer 4: Cryptographic SHA-256 Ratchet Seals & Open Verifier
- **Holy Quran Protection**: The Quran follows the King Fahd Complex Uthmani Hafs recension (114 Surahs, 6,236 Ayahs, 77,429 Words). Each Surah is sealed with dual SHA-256 checksums (fully vocalized Uthmani text and unvocalized text). Altering a single letter or diacritic (*harakah*) fails verification immediately.
- **Non-Destructive Cross-Linking**: Inline entity links never alter underlying Arabic letters or diacritics:
  ```text
  stripInlineRefs(annotatedText) === originalText
  ```
- **Monotonic Ratchet Seals & Open Verifier**: Verified records are sealed with cryptographic SHA-256 ratchet digests audited by an open, reproducible verifier that includes built-in tamper-detection checks.

### Layer 5: Public Printed-Proof Errata Process
Any scholar or reader who spots a discrepancy may submit an erratum backed by direct printed-edition proof (title, editor, publisher, volume, and page, or permanent institutional archive witness). Claims lacking verifiable printed proof are closed without modifying the text, and valid errata proceed through the Universal Two-Person Human Review Rule.
