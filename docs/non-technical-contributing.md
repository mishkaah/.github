# Contribution & Verification Guide

**English** · [العربية](./non-technical-contributing.ar.md)

---

### Maintaining the corpus

We welcome thoughtful suggestions and help in maintaining the collection of Islamic texts in [`mishkaah/corpus`](https://github.com/mishkaah/corpus). Having a background in Islamic studies or Arabic sciences is especially valuable for reviewing texts, checking diacritics (*tashkeel*), and verifying narrator chains.

Because all materials go through careful multi-stage automated and scholarly verification against accredited sources, any remaining discrepancy is rare.

---

### Mandatory proof policy

To maintain accuracy and prevent unsubstantiated claims:
- **Every report requires proof**: We do not accept casual opinions or unverified reports. Every submission must be backed by an exact citation to an approved, accredited source (whether a critical printed edition with volume and page, or an accredited scholarly portal and archive).
- **Required information**: You must specify the book or text, the exact location (Surah and verse, Hadith number, or section), the accredited source reference, and clear proof.
- **Immediate closure**: Any issue opened without solid proof and an exact reference to an accredited source will be closed immediately.

---

### Curated curriculum: qualifying sources

Mishkaah does not accept arbitrary requests to add books:
- Texts are added strictly according to our planned scholarly curriculum.
- Qualifying a new source requires formal evaluation of its critical edition or digital scholarly archive, including editor pedigree, manuscript witnesses, and open licensing.

---

### Submitting a report or proposal

Once you have verified your reference against an approved, accredited source:

- **Documented textual discrepancy**: [Verified Textual Discrepancy Report](https://github.com/mishkaah/corpus/issues/new?template=01-verified-discrepancy-report.yml)
- **Qualify an accredited source**: [Scholarly Source Qualification Proposal](https://github.com/mishkaah/corpus/issues/new?template=02-source-qualification.yml)
- **Complete text revision task**: [Complete Text Revision Task Form](https://github.com/mishkaah/corpus/issues/new?template=03-complete-text-revision.yml)

> **Corpus Discussions**: Proposing a new source or resolving complex textual or attribution questions should first be discussed in [Corpus Discussions](https://github.com/mishkaah/corpus/discussions) before a source is formally qualified and recorded in `SOURCES_MANIFEST.json`.
>
> *Note*: While `mishkaah/corpus` is in private preparation, these issue forms and discussions are accessible to invited reviewers and will open to all visitors as soon as initial verification completes.

---

### Reviewing texts with Mishkaah Studio

Scholars and reviewers who wish to inspect texts, commentaries, and biographies visually can launch the local web studio:

```bash
bun run studio
```

Open `http://localhost:3333` to browse texts alongside commentaries, inspect narrator biographies, and check inline references in real time.
