# Technical Overview

**English** · [العربية](./technical-architecture.ar.md)

---

### Architecture & Repositories

Mishkaah divides its work across seven focused repositories:

- **`mishkaah/corpus`**: Structured JSON files containing classical Arabic texts (Quran, Tafseer, Hadith, Matns, Adhkar, dictionaries, biographies) and foreign language translations.
- **`mishkaah/core`**: Tooling repo containing TypeScript validation scripts, the SQLite search compiler, and GitHub issue automation.
- **`mishkaah/studio`**: Cloudflare Pages dark-mode-first responsive web workspace consuming `@mishkaah/sdk`, backed 100% by GitHub APIs with zero external database, plus regulated BYOK/org-fallback AI co-pilot.
- **`mishkaah/app`**: Web and mobile reader applications with offline-first search.
- **`mishkaah/sdk`**: TypeScript helper library (`@mishkaah/sdk`) for resolving URNs, parsing inline links, and navigating references.
- **`mishkaah/brand`**: Vector logos, mobile app icons for iOS and Android, and design tokens.
- **`mishkaah/.github`**: Public documentation, onboarding guides, and issue forms.

---

### Code quality and validation rules

All scripts, validators, and compilers in `mishkaah/core` run on **Bun 1.4.0** with strict TypeScript:
- **No loose types**: The codebase forbids `any`, `unknown`, `z.any()`, `z.unknown()`, and `.passthrough()`.
- **Strict Zod schemas**: Every object schema ends with `.strict()`, rejecting unmodeled keys.
- **Self-testing checker**: On every test run, the validator runs 28 intentional error cases to ensure that all validation checks are working and have not been bypassed.
- **Validator lock**: A cryptographic lockfile (`validator_lock.json`) hashes all schemas and scripts to prevent unreviewed changes to validation rules.

---

### How data is structured

- **Canonical URNs**: Every text, person, place, and term has a unique identifier (e.g. `mishkah:figure:umar_ibn_al_khattab`, `mishkah:source:sahih_bukhari_tawq`).
- **Clean Arabic text**: Arabic files live under `corpus/` with complete diacritics. Translations live in separate files (`corpus/translations/{lang}/...`) and link back 1-to-1 via `target_urn`.
- **Three-layer dictionaries**: Classical vocabulary connects from root dictionaries (*Lisan al-Arab*) to scripture meanings (*Gharib al-Quran*) to technical definitions (*Al-Ta'rifat*).
- **Offline search**: The JSON corpus compiles into a compact, single-file SQLite database with custom Arabic normalization (stripping tashkeel, normalizing alefs) and FTS5 full-text search for instant offline queries.

---

### Running the tools locally

To run the checks or open the studio locally:

```bash
# Clone the core repo with submodules
git clone --recurse-submodules https://github.com/mishkaah/core.git
cd core

# Install dependencies via Bun
bun install

# Run static type-checking
bun x tsc --noEmit

# Run the test suite and self-tests
bun test tools/meta_validator/verify_the_verifier.test.ts

# Run the full 5-gate corpus verifier
bun run tools/validators/verify_corpus.ts
```
