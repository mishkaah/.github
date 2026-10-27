# Proof of Accuracy: How Mishkaah Protects Sacred Texts & Heritage Data

**English** · [العربية](./data-accuracy-and-protection.ar.md)

---

## 1. Introduction: The Invariant of Sacred Authenticity

When engaging with digitized religious texts and classical scholarly heritage, every reader, researcher, and scholar must ask a foundational question:

> **"How can I know with absolute certainty that this text is authentic, verified against trusted printed editions, and protected against human error, AI hallucination, or unauthorized modification?"**

Mishkaah is engineered around a non-negotiable architectural premise: **sacred scriptures and classical Islamic texts must never rely on blind trust.** Authenticity is not merely a policy; it is mathematically, cryptographically, and procedurally enforced through automated verification gates, cryptographic seals, and strict multi-person review.

---

## 2. Principle 1: We Are Stewards, Never Authors

Mishkaah never generates, paraphrases, or invents religious content:

1. **Zero Generative Text**: No machine learning model or artificial intelligence generates, edits, or alters Islamic texts in this corpus.
2. **Deterministic Source Provenance**: Every ayah, hadith, matn, explanation, and lexicon entry is strictly anchored to an authoritative critical printed edition recorded in `corpus/SOURCES_MANIFEST.json`.
3. **Documented Academic Metadata**: Each registered source records:
   - Full work title in Arabic and English.
   - Author and death year (Hijri and CE).
   - Critical editor (*Muhaqqiq*) who established the text from historical manuscripts.
   - Publisher (*Dar*), city of publication, and edition year.
   - Number of volumes and specific volume and page references.

If a text cannot be definitively traced to an authoritative critical edition, it is rejected by the corpus verifier.

---

## 3. Principle 2: Cryptographic Seal on the Holy Quran

The canonical text of the Holy Quran possesses the highest level of protection within Mishkaah (`Tier 2S - Sacred Scripture`):

- **Canonical Edition**: The text follows the King Fahd Glorious Quran Printing Complex (KFGQPC) Uthmani Hafs an Asim recension.
- **Canonical Cardinality**: Exactly 114 Surahs, 6,236 Ayahs, and 77,429 Words.
- **Cryptographic Seal (`quran_hafs_seal.json`)**:
  - Every single Surah is protected by two distinct SHA-256 cryptographic hashes:
    1. `text_ar_sha256`: Hash of the full classical Arabic text with complete Uthmani vocalization and diacritics.
    2. `text_clean_sha256`: Hash of the unvocalized Arabic text for structural shape invariance.
  - The master seal records the total word count, ayahs count, and combined SHA-256 digest of the entire revelation.
- **Directory & Riwayah Guard**:
  - The automated verifier strictly prohibits unauthorized subdirectories under `quran/`.
  - Only authorized and cryptographically sealed Qira'at editions (beginning with canonical Hafs) are permitted.
  - Any unauthorized character, altered vowel mark (*harakah*), or modified punctuation fails CI instantly.

---

## 4. Principle 3: Non-Disruptive Inline Linking

To enable modern search, entity recognition, and pedagogical exploration without defacing the classical heritage, Mishkaah utilizes a non-disruptive referencing architecture:

Mentions of historical figures, places, and scholarly terms are linked using Markdown link syntax:
```markdown
[Text](mishkah:domain:identifier)
```

This linking system is governed by a strict mathematical equality:
```ts
stripInlineRefs(text_annotated_ar) === text_ar
```

### The Invariance Guarantee:
- Stripping the reference link tags returns the exact original Arabic text byte-for-byte.
- Linking never adds, alters, or removes a single Arabic character, space, or diacritic.
- If an entity tag modifies even one letter of the source text, the verifier aborts with a validation error.

---

## 5. Principle 4: 3-Tier File Architecture & 5-Gate Verification

To prevent accidental corruption, all repository files are classified into three distinct security tiers:

| Tier | Category | Protection Mechanism |
| :--- | :--- | :--- |
| **Tier 1** | **Auto-Generated Artifacts**<br/>(`CORPUS_INTEGRITY_MANIFEST.json`, `_index.json`, clusters, graph links) | **Never edited by hand.** Strictly compiled via deterministic scripts. PRs modifying these files manually are rejected by CI gatekeepers. |
| **Tier 2** | **Scholarly Corpus Data**<br/>(Hadith, Tafseer, Matns, Lexicons, Biographies) | **Reviewed against printed editions.** Must pass all 5 verification gates and adhere to strict schemas. |
| **Tier 2S** | **Holy Quran**<br/>(`corpus/quran/hafs/`) | **Cryptographically sealed.** Locked by SHA-256 checksums in `quran_hafs_seal.json`. Zero tolerance for mutation. |
| **Tier 3** | **Schemas & Verifiers**<br/>(`tools/schemas/`, `tools/validators/`) | **Locked by SHA-256.** Guarded by `validator_lock.json` and validated by 28 synthetic poison-pill canaries on every run. |

### The 5 Automated Verification Gates

Every proposed change is evaluated by the forensic verification engine before merge:

1. **Gate 1 — Syntax, Encoding & Integrity**:
   - Validates 100% valid JSON and clean UTF-8 encoding without BOM markers.
   - Enforces the unauthorized Riwayah directory guard.
   - Verifies all file checksums against `CORPUS_INTEGRITY_MANIFEST.json`.
2. **Gate 2 — Strict Schema Uniformity**:
   - Every file must conform to TypeScript Zod schemas ending in `.strict()`.
   - Rejects extraneous keys, type mismatches, and unrecognized fields.
3. **Gate 3 — URN Grammar & Primary Keys**:
   - Validates canonical URN regex patterns (`mishkah:<domain>:<id>`).
   - Ensures global uniqueness of every identifier across the corpus.
4. **Gate 4 — Referential Graph & Provenance**:
   - Ensures no orphan entity or source references exist.
   - Validates every `source_urn` against the approved catalog in `docs/sources.md`.
5. **Gate 5 — Scholarly Authenticity & Seal Check**:
   - Scans for placeholder text (`TODO`, `Lorem ipsum`, unverified notes).
   - Validates the Holy Quran against the immutable cryptographic Hafs seal.

---

## 6. Principle 5: Layer 0 Meta-Validation (Verifying the Verifier)

How do we ensure that a contributor or workflow does not accidentally weaken or disable the verification tools themselves?

Mishkaah implements **Layer 0 Meta-Validation** (`verify_the_verifier.ts`):
- **AST Guard**: Parses all TypeScript code using the TypeScript Compiler API to detect and ban escape hatches (`any`, `unknown`, `z.any()`, `z.unknown()`, `.passthrough()`, `@ts-ignore`, `@ts-expect-error`).
- **Validator Lockfile (`validator_lock.json`)**: Computes SHA-256 hashes of all schema files and validation scripts. Any unauthorized modification to the rules triggers a build failure.
- **28 Poison-Pill Canaries**: A comprehensive suite of 28 synthetic corruptions (mutated Quran ayahs, invalid URNs, missing Tashkeel, broken graph edges, unauthorized sources) is injected into memory during test runs. The verifier must achieve **100.0% detection** (28/28 caught) or the build fails.
- **CI Unconditional Execution Guard**: Scans GitHub Actions workflow YAML files to ensure no verification steps contain suppression flags (`|| true`, `continue-on-error: true`, or conditional bypasses).

---

## 7. Principle 6: Independent Four-Eyes Peer Review

No matter how robust the automated tools are, human scholarly judgment is indispensable:

- **The Invariant**: `Reviewer != Author`.
- **CI Enforcement**: Automated gatekeepers inspect every pull request review. An author can never approve or merge their own pull request.
- **Printed Edition Corroboration**: Corrections to classical texts must cite the specific volume, page, and printed critical edition. Scholarly reviewers verify the suggested correction directly against the physical scan or printed volume before granting approval.

---

## 8. Summary

Through this combination of cryptographic sealing, deterministic provenance, mathematical invariants, multi-layered verification gates, and independent human review, Mishkaah ensures that the digital preservation of Islamic heritage remains uncompromised, transparent, and worthy of scholarly trust.
