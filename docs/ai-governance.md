# Public AI Safety Principles

**English** · [العربية](./ai-governance.ar.md)

> [Organization Overview](../README.md) · [Data Accuracy & Protection](./data-accuracy-and-protection.md) · [Brand Assets](https://github.com/mishkaah/brand)

---

## Core Stance

Mishkaah protects sacred texts and classical Islamic scholarship through strict boundary controls around automated tools. Technology may assist scholars with structural verification and discovery, but it may **never** replace scholarly authority or touch sacred wording unchecked.

---

## The Three Public AI Safety Principles

### 1. Zero Generative Authoring of Sacred Texts
- **No Text Generation**: Automated models are strictly prohibited from authoring, completing, summarizing, or paraphrasing primary religious texts (Holy Quran, Hadith, Tafseer, Adhkar, or classical primers).
- **No Diacritic Guessing**: Vowel marks (*tashkeel*) may never be guessed or auto-completed without an accredited printed witness.
- **No Fabricated Citations or Gradings**: Hadith authenticity gradings (*hukm*), transmission chains (*asanid*), and bibliographic coordinates (publisher, editor, volume, page) must come directly from accredited sources — never from model weights.

### 2. Closed-World Deterministic Filters
Where assistive computational tools support editorial workflows (such as read-only anomaly scanning or entity-link suggestions), they are bound by deterministic code contracts:
- **Closed-World Scope**: Link suggestions may only reference pre-existing, verified entity identifiers; invented identifiers are rejected automatically.
- **Character-for-Character Invariant**: Every proposed annotation must satisfy the deterministic invariant check before it can even be previewed for human review:
  ```text
  stripInlineRefs(annotatedText) === originalText
  ```
  Any discrepancy of a single letter, diacritic mark, or space discards the output immediately.
- **Read-Only Advisory Scans**: Anomaly scanners highlight potential typesetting slips for a scholar to inspect in the printed book; they never mutate primary Arabic texts automatically.

### 3. Mandatory Human Review & Provenance Disclosure
- **No Automated Approvals**: AI systems and bots can never act as peer reviewers or approve/merge changes.
- **Universal Two-Person Human Review Rule**: Every assisted contribution requires explicit provenance disclosure and independent verification by both an **Adder** and a **Mandatory Independent Human Reviewer** collated directly against the physical printed witness.
- **Quarantine of Unreviewed Seeds**: Any unreviewed or unverified entry stays outside production builds until independent human review completes.
