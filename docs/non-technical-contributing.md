# Guide for Non-Technical Contributors, Scholars & Proofreaders

**English** · [العربية](./non-technical-contributing.ar.md)

---

## 1. Welcome to the Mishkaah Contributor Circle

You do not need to be a software engineer, programmer, or Git expert to contribute to Mishkaah. 

The greatest need of this project is scholarly precision: verifying classical Arabic texts against printed editions, checking diacritical marks (*tashkeel*), ensuring narrator names and chains (*asanid*) are accurate, proposing authoritative critical editions, and translating classical terminology into global languages.

If you are a scholar, student of knowledge (*Talib Ilm*), Arabic proofreader, translator, or conscientious reader, this guide explains how you can contribute effortlessly.

---

## 2. Path A: Spotting and Reporting an Error

If you discover a typo, a missing vowel mark (*harakah*), a dropped word, or an inaccurate attribution anywhere in our apps or datasets:

1. **Open the Text Issue Form**:
   - Navigate to our [**Report a Text or Data Issue Form**](https://github.com/mishkaah/.github/issues/new?template=01-report-text-error.yml).
2. **Fill in the Required Details**:
   - **Domain**: Choose the field (e.g. *Hadith*, *Tafseer*, *Mutun*, *Adhkar*).
   - **Work Title**: Name of the book or primer (e.g. *Sahih al-Bukhari*, *Al-Ajrumiyyah*).
   - **Exact Reference**: Surah and Ayah number, hadith number, or poem line number.
   - **Current Text**: Paste the text as it currently appears.
   - **Suggested Correction**: Provide the accurate reading with complete vocalization (*tashkeel*).
   - **Printed Critical Edition**: Provide the publisher (*Dar*), editor (*Muhaqqiq*), volume, and page number where your correction is verified.
3. **Automated Triage & Human Review**:
   - Our automated triage bot verifies the formatting and applies the `status:awaiting-triage` label.
   - A qualified scholarly reviewer inspects the physical printed edition.
   - Once corroborated, the issue is marked `status:approved-revision-task`.
   - The automated engine generates the scoped correction, updates all derivative indexes, and requests an independent peer review before merging.

---

## 3. Path B: Proposing an Authoritative Printed Source

Before any new classical work, hadith collection, or explanation is added to the corpus, its critical edition must be vetted and approved.

1. **Submit a Source Proposal**:
   - Open the [**Propose a New Scholarly Source Form**](https://github.com/mishkaah/.github/issues/new?template=02-propose-new-source.yml).
2. **Provide the Scholarly Pedigree**:
   - Title of the work in Arabic and English.
   - Classical author and Hijri death year.
   - Editor (*Muhaqqiq*) who collated the manuscripts.
   - Publishing house, city, and publication year.
   - Information on historical manuscripts consulted.
   - Copyright and public domain confirmation.
3. **Scholarly Review & Registration**:
   - Maintainers evaluate the academic standing of the edition.
   - Once approved with the label `governance:source-approved`, automated tooling creates the canonical source entry in `corpus/SOURCES_MANIFEST.json` and updates `corpus/docs/sources.md`.

---

## 4. Path C: The Visual Contributor Studio GUI

For contributors who want to browse, inspect, and enrich texts visually without editing JSON files directly, Mishkaah provides an interactive browser-based application: **Mishkaah Studio**.

```bash
bun run studio
```

Opening `http://localhost:4100` launches a clean, distraction-free interface where you can:

1. **Live Corpus Browser**:
   - Browse through all Surahs, Hadith collections, Tafseer entries, Scientific Matns, and Adhkar.
   - View Arabic text with vocalization side-by-side with translations and commentary.
2. **Visual Entity Inspector**:
   - View connected companions, scholars, geographic locations, and historical battles.
   - Check narrator biographies and relationships within transmission chains.
3. **Inline Reference Linker**:
   - Highlight any scholar or place name in a classical text and attach its canonical identifier (e.g. `mishkah:figure:umar_ibn_al_khattab`) visually.
   - The Studio automatically validates the invariant `stripInlineRefs(text_annotated_ar) === text_ar` in real-time, preventing textual alterations.
4. **Instant Diagnostic Validation**:
   - Test proposed text modifications against the 5-Gate verification engine directly inside the browser before creating a submission.

---

## 5. Path D: Volunteering as a Regular Reviewer or Proofreader

If you would like to join the active circle of scholarly reviewers or Arabic proofreaders:

1. Submit a [**Volunteer Issue**](https://github.com/mishkaah/.github/issues/new?template=03-volunteer-or-contribute.yml).
2. Mention your background, areas of specialization (e.g. *Hadith Asanid*, *Shafi'i Fiqh*, *Arabic Grammar & Morphology*), and weekly availability.
3. You will be tagged as an official reviewer on incoming issues and revisions in your area of expertise.

---

## 6. Scholarly Waqf Ethics & Guiding Principles

Every contribution to Mishkaah is treated as a continuous scholarly endowment (*Sadaqah Jariyah* and *Waqf*):
- **Accuracy Precedes Speed**: We prefer taking days to verify a single diacritic against three manuscript editions over rushing an unverified correction.
- **Humility & Reverence**: We are humble transmitters of sacred knowledge handed down by generations of venerable scholars.
- **Transparency**: Every single correction, citation, and review discussion is publicly archived and preserved for historical accountability.
