# Contributor Guide for Readers & Reviewers

**English** · [العربية](./non-technical-contributing.ar.md)

---

### You don't need to write code to help

The most valuable contribution to Mishkaah is careful proofreading: checking classical texts against printed editions, catching missing diacritics (*tashkeel*), verifying narrator names in Hadith chains, and suggesting reliable printed editions.

If you know Arabic, study Islamic texts, or simply spot a mistake while reading, you can contribute directly through simple forms without knowing Git or programming.

---

### Reporting a mistake in a text

If you spot a typo, a missing vowel mark, or an incorrect attribution:

1. Open our [Report a text error form](https://github.com/mishkaah/.github/issues/new?template=01-report-text-error.yml).
2. Tell us:
   - Which book or science (e.g. *Hadith*, *Tafseer*, *Adhkar*).
   - The exact location (Surah and verse, Hadith number, or page).
   - What the text currently says and what it should say with full diacritics.
   - The printed edition, editor (*Muhaqqiq*), volume, and page where your correction is confirmed.
3. A reviewer will verify the change against the printed edition before merging it.

---

### Suggesting a printed edition

Before we add a new classical book or commentary, we verify the quality of the printed critical edition:

1. Open our [Suggest a printed source form](https://github.com/mishkaah/.github/issues/new?template=02-propose-new-source.yml).
2. Share the book title, author, editor (*Muhaqqiq*), publishing house, and publication year.
3. Once approved, the book is added to our sources registry so contributors can begin formatting it.

---

### Browsing texts in Mishkaah Studio

If you prefer viewing and editing texts in a visual interface rather than looking at raw files, you can run the local web studio:

```bash
bun run studio
```

Open `http://localhost:4100` in your browser to:
- Browse all Quran Surahs, Hadith collections, and Matns with their translations and commentaries.
- Inspect biographies of Companions and scholars.
- Highlight names in the text to attach person or place links visually, with live checks that make sure the original Arabic text isn't altered.

---

### Joining as a regular reviewer

If you would like to help review incoming reports and text submissions regularly:
- Fill out the [Join as a reviewer form](https://github.com/mishkaah/.github/issues/new?template=03-volunteer-or-contribute.yml).
- Let us know your areas of study (e.g. *Hadith*, *Fiqh*, *Arabic grammar*) and your availability.
