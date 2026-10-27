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

Once you have verified your reference against an approved source:

- **Documented textual discrepancy**: [Verified Textual or Reference Report Form](https://github.com/mishkaah/.github/issues/new?template=01-report-text-error.yml)
- **Qualify an accredited source**: [Scholarly Source Qualification Form](https://github.com/mishkaah/.github/issues/new?template=02-propose-new-source.yml)
- **Join the review team**: [Volunteer Reviewer Form](https://github.com/mishkaah/.github/issues/new?template=03-volunteer-or-contribute.yml)

---

### Reviewing texts with Mishkaah Studio

Scholars and reviewers who wish to inspect texts, commentaries, and biographies visually can launch the local web studio:

```bash
bun run studio
```

Open `http://localhost:4100` to browse texts alongside commentaries, inspect narrator biographies, and check inline references in real time.
