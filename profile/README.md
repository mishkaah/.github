<div align="center">

![Mishkaah](./assets/mishkaah-social-banner.png)

**English** · [العربية](./README.ar.md)

</div>

**Mishkaah (مِشْكَاة)** is an open-source effort to gather the core Islamic texts a Muslim needs — the Quran, Tafseer, Hadith, daily Adhkar, classical primers (*Mutun*) and their explanations, biographies, and Arabic dictionaries — into one clean, reliable dataset and a simple reading app for web and mobile.

We don't author or generate any religious content. We collect verified texts from trusted printed editions, format them consistently, link related passages and biographies together, and make them freely available to readers and developers.

---

### Where to go from here

- **Want to know how we verify the data?**
  Read [How We Check and Protect the Texts](https://github.com/mishkaah/.github/blob/main/docs/data-accuracy-and-protection.md) — where our texts come from, how the Quran text is locked with SHA-256 checksums so not a single letter can be changed, and how every edit requires both automated checks and review by a second person.

- **Spotted a mistake or want to help with reviewing texts? (No coding needed)**
  Read the [Contributor Guide for Readers & Reviewers](https://github.com/mishkaah/.github/blob/main/docs/non-technical-contributing.md), or open a form directly:
  [Report a text error](https://github.com/mishkaah/.github/issues/new?template=01-report-text-error.yml) · [Suggest a printed source](https://github.com/mishkaah/.github/issues/new?template=02-propose-new-source.yml) · [Join as a reviewer](https://github.com/mishkaah/.github/issues/new?template=03-volunteer-or-contribute.yml)

- **Looking for the code, schemas, or data format?**
  Read the [Technical Overview](https://github.com/mishkaah/.github/blob/main/docs/technical-architecture.md) for how the JSON corpus, TypeScript/Bun validation scripts, URN links, and offline SQLite search work.

---

### Repositories

| Repository | What it holds | Status |
| :--- | :--- | :--- |
| [`mishkaah/corpus`](https://github.com/mishkaah/corpus) | The Arabic JSON dataset (Quran, Tafseer, Hadith, Matns, Adhkar, biographies, dictionaries) and translations | Private (in review) |
| [`mishkaah/core`](https://github.com/mishkaah/core) | TypeScript & Bun scripts for schema validation, source checks, and building the SQLite search database | Private (in review) |
| [`mishkaah/app`](https://github.com/mishkaah/app) | Web and mobile reading apps | Private (in development) |
| [`mishkaah/sdk`](https://github.com/mishkaah/sdk) | TypeScript utilities (`@mishkaah/sdk`) for working with Mishkaah URNs and inline links | Private (in development) |
| [`mishkaah/brand`](https://github.com/mishkaah/brand) | Logos, mobile app icons, and color/typography tokens | Private (in development) |
| [`mishkaah/.github`](https://github.com/mishkaah/.github) | Public overview, documentation, and issue forms | **Public** |

> We are finishing initial data checks before opening `corpus` and `core` publicly. In the meantime, all documentation and feedback forms in [`mishkaah/.github`](https://github.com/mishkaah/.github) are open.
