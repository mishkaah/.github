# How We Check and Protect the Texts

**English** · [العربية](./data-accuracy-and-protection.ar.md)

---

### We collect and verify, never author

Mishkaah does not generate, synthesize, or paraphrase religious texts. No artificial intelligence or machine learning model is ever permitted to author, extrapolate, or alter any text in this corpus. Everything comes from trusted, accredited sources (critical printed editions and official scholarly portals), with documented publisher, editor (*Muhaqqiq*), publication year, volume, and page number or digital archive reference recorded in `corpus/SOURCES_MANIFEST.json`.

Every registered source or cited proof must be tangible, publicly accessible, and independently verifiable — such as circulated printed books and critical scholarly editions (*Tahqiq*), or recognized public digital libraries and official institutional archives with permanent references. Personal attributions, oral statements requiring contacting an individual, and ephemeral or mutable web pages (which can be silently modified or deleted) are strictly inadmissible. Contemporary published works by identifiable scholars may be qualified only if they exist in an immutable, permanently archived, and referenceable form, following prior deliberation and scholarly consensus in [Corpus Discussions](https://github.com/mishkaah/corpus/discussions).

Where assistive computational tools are used within **Mishkaah Studio** (such as read-only diacritic anomaly detection or closed-world entity linking), they operate under strict deterministic invariant filters (`stripInlineRefs(annotatedText) === originalText`), mandatory PR disclosure (`Gate C.2`), and required human collation before merge. For full details on our classification framework, see the [Regulated AI Governance Standard](./ai-governance.md).

---

### Cryptographic seal on the Holy Quran

The Quran text follows the King Fahd Complex Uthmani Hafs recension (114 Surahs, 6,236 Ayahs, 77,429 Words).

To ensure it can never be altered:
- Every Surah is locked with two SHA-256 cryptographic hashes: one for the fully vocalized Uthmani text, and one for the unvocalized text.
- If a single character, diacritic (*harakah*), or punctuation mark is modified, the build fails immediately.
- The Quran directory only allows verified, locked editions.

---

### Links never change the Arabic text

When we tag historical figures, places, or terms inside a passage, we use Markdown links: `[Text](mishkah:domain:id)`.

We enforce a strict rule: stripping the link tags must reproduce the original Arabic text byte-for-byte:

```ts
stripInlineRefs(annotatedText) === originalText
```

If adding a link changes even one letter or space of the original text, the verification script rejects the change.

---

### Automated checks on every change

Every contribution passes through automated checks before anyone can merge it:
- **Valid JSON and UTF-8**: Ensures clean encoding with no hidden formatting characters.
- **Strict schemas**: Every field must match predefined types; unexpected keys are rejected.
- **Source verification**: Checks that every cited work exists in our approved sources catalog.
- **Self-testing checker**: On every run, the checker tests itself against 28 intentional test errors (tampered verses, missing tashkeel, bad references) to confirm that the validator itself is active and functioning.

---

### Mandatory second-person review

Automated checks verify structure, links, and checksums, while scholarly review confirms every word against the approved source:
- The person who prepares a change cannot approve or merge it (`Reviewer != Author`).
- Any correction or revision must reference the approved source (critical printed edition, volume, and page, or accredited scholarly archive).
- A second reviewer checks the change against the verified source before approving.
