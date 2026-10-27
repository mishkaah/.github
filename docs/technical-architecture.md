# Technical Architecture & Verification Engine Guide

**English** · [العربية](./technical-architecture.ar.md)

---

## 1. Architectural Philosophy

The Mishkaah software and data ecosystem is designed for extreme durability, cryptographic verifiability, and zero runtime compromise. Islamic texts must be preserved with digital immutability while remaining effortlessly queryable, interconnected, and accessible across modern devices.

Our technical stack is built on three core pillars:
1. **Zero-Escape-Hatch Strict TypeScript**: Absolute type safety with Bun 1.4.0 runtime.
2. **Defensive Layer 0 Meta-Validation**: The testing framework verifies its own verification engine before inspecting corpus data.
3. **Stand-Off Knowledge Graph**: Dense intertextual links and multilingual translations exist as non-disruptive overlays that never alter canonical Arabic originals.

---

## 2. The 6-Repository Modular Ecosystem

The project is structured into six focused repositories with explicit separation of concerns:

| Repository | Purpose | Primary Stack | Visibility |
| :--- | :--- | :--- | :--- |
| **`mishkaah/.github`** | Public organization portal, documentation guides, issue templates, and shared CI actions | Markdown, YAML | **Public** |
| **`mishkaah/brand`** | Calligraphic vectors, iOS 18 & Android adaptive app icon suites, and design tokens | SVG, PNG, JSON Tokens | Private (Prep) |
| **`mishkaah/corpus`** | Open, structured JSON dataset of authentic Islamic texts (Quran, Tafseer, Hadith, Matns, Lexicons) | 100% Arabic JSON | Private (Prep) |
| **`mishkaah/core`** | TypeScript validation suite, SQLite FTS5 compiler, Studio GUI, and issue automation | TypeScript, Bun 1.4, Zod, SQLite | Private (Prep) |
| **`mishkaah/sdk`** | `@mishkaah/sdk` library for parsing URNs, stripping inline links, and graph traversal | TypeScript, npm package | Private (Prep) |
| **`mishkaah/app`** | Unified web and mobile reader applications with offline-first local database | Flutter, SQLite, Web | Private (Prep) |

---

## 3. Strict Engineering & Type Contracts

All tooling, scripts, validators, and compilers in `mishkaah/core` must adhere to rigorous engineering standards:

- **Runtime**: Bun 1.4.0 (`bun`).
- **Forbidden Constructs**: The codebase strictly forbids `any`, `unknown`, `z.any()`, `z.unknown()`, `.passthrough()`, `@ts-ignore`, and `@ts-expect-error`.
- **Zod Schema Invariant**: Every object schema must end with `.strict()`, disallowing arbitrary or unrecognized fields.
- **Explicit Literal Unions**: Enumerations use explicit string literal unions (`z.enum([...])`) or template literal regexes to enforce strict formatting at compilation and validation time.

---

## 4. Layer 0 Meta-Validator: Verifying the Verifier

To guarantee that continuous integration cannot be compromised by subtle test regressions or disabled assertions, `mishkaah/core` implements an automated **Layer 0 Meta-Validator** (`tools/meta_validator/verify_the_verifier.ts`):

```
┌─────────────────────────────────────────────────────────────┐
│                 Layer 0: Meta-Validator                    │
├─────────────────┬─────────────────┬─────────────────────────┤
│   Gate 0.1      │    Gate 0.2     │        Gate 0.3         │
│ AST Code Guard  │ Cryptographic   │ 28 Poison Canaries      │
│ (Bans `any`)    │ Hash Lockfile   │ (100.0% Catch Rate)     │
└─────────────────┴─────────────────┴─────────────────────────┘
                              │
                              ▼
┌─────────────────────────────────────────────────────────────┐
│             Layer 1: 5-Gate Forensic Verifier               │
├───────────┬───────────┬───────────┬───────────┬─────────────┤
│  Gate 1   │  Gate 2   │  Gate 3   │  Gate 4   │   Gate 5    │
│ Syntax &  │ Strict    │ URN & PK  │ Graph &   │ Hafs Seal   │
│ Riwayah   │ Schemas   │ Grammar   │ Provenance│ & Anti-Fake │
└───────────┴───────────┴───────────┴───────────┴─────────────┘
```

1. **Gate 0.1: AST Guard**:
   Scans all TypeScript source files using the TypeScript Abstract Syntax Tree (AST) Compiler API. It flags any usage of `any`, `unknown`, `@ts-ignore`, or loose schemas.
2. **Gate 0.2: Cryptographic Validator Lock (`validator_lock.json`)**:
   Maintains SHA-256 digests of all validator scripts and schema definitions. Modifying a rule requires regenerating the lockfile explicitly via `--update-lock`.
3. **Gate 0.3: 28-Pill Poison Canary Suite**:
   A comprehensive suite of 28 synthetic corruptions injected into memory (e.g. tampered Quran words, non-existent sources, schema violations, invalid URNs). The verifier must achieve **100.0% detection** (28/28 caught) or CI aborts.
4. **Gate 0.4: Workflow Protection**:
   Audits GitHub Actions workflow files to verify that test and verification suites are invoked unconditionally without fallback suppression (`|| true`, `continue-on-error: true`).

---

## 5. The 6 Universal Entity Domains

Mishkaah organizes all historical, geographical, and conceptual entities into six immutable domains governed by canonical Uniform Resource Names (URNs):

1. **`mishkah:figure:<id>`**: Biographies of Prophets, Companions, Hadith narrators, and classical scholars with birth/death years and relationships.
2. **`mishkah:place:<id>`**: Historical cities, mountains, valleys, and sacred locations with historical names and coordinates.
3. **`mishkah:event:<id>`**: Historical milestones, expeditions (*Maghazi*), and foundational assemblies.
4. **`mishkah:term:<id>`**: Technical definitions across Usul, Fiqh, Aqeedah, Balaghah, and Hadith terminology.
5. **`mishkah:group:<id>`**: Historical tribes, scholarly schools (*Madhahib*), and lineages.
6. **`mishkah:object:<id>`**: Historical artifacts, manuscripts, and physical objects referenced in authentic traditions.

---

## 6. The 3-Layer Connected Arabic Lexicon System

Mishkaah connects every obscure or classical word in the Quran, Hadith, and poetry across three distinct lexical strata:

```
[ Classical Word in Matn or Ayah ]
               │
               ▼
┌───────────────────────────────────────────────┐
│ Layer 1: Root Dictionary (Roots & Etymology)  │
│ Lisan al-Arab & Maqayis al-Lughah             │
└──────────────────────┬────────────────────────┘
                       │
                       ▼
┌───────────────────────────────────────────────┐
│ Layer 2: Contextual Scripture Lexicon         │
│ Al-Mufradat fi Gharib al-Quran (Al-Isfahani)  │
└──────────────────────┬────────────────────────┘
                       │
                       ▼
┌───────────────────────────────────────────────┐
│ Layer 3: Technical Terminological Lexicon     │
│ Kitab al-Ta'rifat (Al-Jurjani)                │
└───────────────────────────────────────────────┘
```

---

## 7. Stand-Off Multilingual Localization

Foreign translations (English, Urdu, French, Indonesian) are architected as **stand-off overlays**:
- The classical Arabic text remains pristine and unpolluted by multilingual metadata.
- Translation files live in `corpus/translations/{lang}/...`.
- Each translation unit maps 1-to-1 to an Arabic canonical URN via `target_urn`.
- Translators can enrich or revise translations without risk of generating merge conflicts in the core Arabic corpus.

---

## 8. Offline SQLite FTS5 Compilation Engine

For high-speed, local-first search across web and mobile apps, `mishkaah/core` compiles the entire 935-file JSON corpus into an optimized, self-contained SQLite database:
- **Full-Text Search (FTS5)**: Custom Arabic tokenizer stripping tashkeel, normalizing alefs, and indexing morphological root links.
- **Trigram & Prefix Indexing**: Enables instant searching across 62,000+ hadiths and 37,000+ tafseer entries in under 15 milliseconds on mobile devices.
- **Zero Network Dependency**: Complete offline functionality for readers in low-connectivity environments.

---

## 9. Getting Started for Engineers

To run the full suite locally:

```bash
# Clone the core repository
git clone https://github.com/mishkaah/core.git
cd core

# Initialize submodules (corpus)
git submodule update --init --recursive

# Install dependencies via Bun
bun install

# Run static type-checking
bun x tsc --noEmit

# Run Layer 0 Meta-Validator
bun test tools/meta_validator/verify_the_verifier.test.ts

# Run Markdown link & documentation audit
bun run tools/validators/verify_markdown_links.ts

# Run full 5-Gate Corpus Forensic Verifier
bun run tools/validators/verify_corpus.ts

# Launch the Visual Studio GUI
bun run studio
```
