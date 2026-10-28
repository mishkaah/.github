# Regulated AI Governance & Textual Integrity Standard

**English** · [العربية](./ai-governance.ar.md)

---

> ### 🧭 Quick Navigation
> [Organization Overview](https://github.com/mishkaah/.github) · [Text Verification & Protection](./data-accuracy-and-protection.md) · [Contribution Guide](./non-technical-contributing.md) · [Technical Architecture](./technical-architecture.md) · [Mishkaah Studio](https://github.com/mishkaah/studio)

---

## 1. Core Philosophy: Standardized Regulation Over Blind Trust or Illusory Bans

The Mishkaah Open Islamic Corpus protects sacred texts and classical heritage. In the era of large language models (LLMs), two flawed extremes exist:

1. **Unregulated Generative Adoption**: Letting models hallucinate, summarize, or alter religious texts from probabilistic weights, which corrupts sacred wording and fabricates scholarly citations.
2. **Unenforceable Blanket Bans**: Declaring a total ban on AI while offering no verified workflows, which inevitably breeds "shadow AI"—collaborators silently copy-pasting unchecked chatbot outputs through web interfaces without technical safeguards or provenance trails.

Mishkaah adopts a rigorous, institutional third way: **Standardized Architectural Regulation**. 

Rather than allowing unmonitored external prompts, assistive capabilities are embedded directly inside **Mishkaah Studio** (`mishkaah/studio`). They run under locked `temperature: 0` prompt parameters, deterministic invariant filters enforced by `@mishkaah/sdk`, mandatory provenance disclosure trailers on every Pull Request, and absolute human peer review (`Reviewer != Author`).

---

## 2. The 3-Zone Regulated AI Classification Framework

Every algorithmic capability is classified into one of three strict operational zones:

```text
+-------------------------------------------------------------------------------+
|                       MISHKAAH 3-ZONE AI GOVERNANCE                           |
|                                                                               |
|  [ZONE 1: RED]    Strictly Prohibited & Hard-Blocked in Code and CI           |
|  [ZONE 2: AMBER]  Regulated Invariant-Checked Assistance (Human Sign-Off)     |
|  [ZONE 3: GREEN]  Read-Only Scholarly Auditing & Discovery (Zero Mutation)     |
+-------------------------------------------------------------------------------+
```

### Zone 1: Strictly Prohibited (Hard-Blocked in Code & CI)

The following activities are categorically banned across all tools, scripts, and workflows. Violations trigger immediate Pull Request rejection and maintainer escalation:

- **Generative Synthesis of Religious Texts**: Generating, completing, paraphrasing, or altering primary Arabic texts (`matns/quran/**`, `matns/hadith/**`, `matns/scientific_matns/**`, `adhkar/**`, `explanations/**`) from model memory.
- **Unverified Tashkeel Guessing**: Auto-filling or predicting vowel marks (*tashkeel*) without an accredited critical printed witness.
- **Fabricated Scholarly Metadata**: Inventing Hadith gradings (*hukm*), narrator chains (*asanid*), or printed-edition volume/page citations.
- **Autonomous Approvals or Merges**: AI models, bots, or automated agents acting as peer reviewers or approving/merging Pull Requests. Every merge requires an independent human reviewer (`Reviewer != Author`).

### Zone 2: Regulated Invariant-Checked Assistance (Human-Verified Sign-Off)

Zone 2 features assist scholars with tedious structural mapping. They operate under deterministic code contracts and require per-item human verification:

#### Tool 1: Closed-World Entity & Narrator Link Suggester
- **Target Fields**: `text_annotated_ar` and `content_annotated_ar`.
- **Closed-World Constraint**: The model can only propose links to entities that already exist as canonical URNs in `corpus/entities/`. Hallucinated slugs are blocked immediately.
- **Deterministic Invariant Filter**: Every proposed annotation is validated by `@mishkaah/sdk`:
  ```ts
  stripInlineRefs(outputAnnotatedText) === originalBaseArabicText
  ```
  If even a single letter, vowel mark, or space differs from the base text, the entire suggestion is discarded instantly.
- **Forced Disambiguation**: When multiple historical personalities share a name (e.g., *Sufyan al-Thawri* vs. *Sufyan b. 'Uyaynah*), the system forces the reviewer to select the correct narrator by displaying generation tier (*tabaqah*) and year of death (*wafat*).

#### Tool 3: Source-Excerpt Structured Field Extractor
- **Target Files**: `entities/**` and `SOURCES_MANIFEST.json`.
- **Verbatim Excerpt Input**: The reviewer pastes a verbatim citation excerpt directly from an accredited printed biographical dictionary alongside volume and page.
- **Schema Extraction**: The model extracts structured JSON fields (death year, full patronymic, teachers, students) strictly from the provided text excerpt. The reviewer manually collates each field before saving.

*(Note: Stand-off translation draft assistance in `translations/{lang}/` for non-Quran texts is planned for Milestones `M11`–`M12` under a locked Islamic terminology glossary.)*

### Zone 3: Read-Only Scholarly Auditing & Discovery (Zero Corpus Mutation)

Zone 3 tools provide advisory insights without ever writing to corpus files:

#### Tool 2: Read-Only Text & Diacritic Anomaly Scanner
- Analyzes classical text passages and flags potential OCR transcription typos, typesetting errors (*tashif*), or unusual vocalization sequences.
- Surfaces advisory cards in Mishkaah Studio pointing the scholar to the exact verse or sentence to inspect in the physical printed volume. It **never** alters `text_ar` automatically.

#### Tool 4: Reviewer Pre-Flight Diff Briefing
- Prepares a structured pre-flight summary for Peer Reviewer B when opening a Pull Request.
- Highlights subtle diacritic modifications, verifies narrator generational continuity, and checks citation completeness. It assists the human reviewer but never approves or blocks the PR autonomously.

---

## 3. Provisioning, Privacy & Collaborative Access

To guarantee accessibility for scholars while protecting confidentiality:

1. **Dual Provisioning (BYOK + Organization Fallback Key)**:
   - **Bring Your Own Key (BYOK)**: Reviewers can configure personal API keys (`Z.ai GLM Coding Plan (Flash)` as primary/default, `Google Gemini`, `OpenAI`, or `Anthropic Claude`) stored exclusively in their own browser's encrypted local storage (`localStorage`). Keys are never sent to external servers or committed to Git.
   - **Organization Fallback Key**: Verified members of the Mishkaah Review Team (`mishkaah/corpus` collaborators) can seamlessly utilize the organization's sponsored API gateway with zero personal setup. The organization fallback gateway currently routes requests via the high-throughput Z.ai GLM Coding Plan Flash endpoint (`https://api.z.ai/api/coding/paas/v4/chat/completions`).
2. **Deterministic Sampling**:
   - All prompts run at `temperature: 0` with top-p minimization to ensure reproducible, non-speculative outputs.
3. **Zero Retention Policy**:
   - Commercial models are invoked solely through enterprise and developer API tiers that explicitly contract against using input prompts for model training.

---

## 4. PR Provenance Disclosure & Accountability Enforcement

Every contribution to the corpus remains fully transparent and accountable:

### Pull Request Provenance Trailer (`Gate C.2`)
Every Pull Request generated via Mishkaah Studio or GitHub Web must declare its algorithmic assistance level in the commit body and PR description:

```markdown
AI-Assistance: none | entity-linking | anomaly-scan | excerpt-extraction | diff-briefing
AI-Model: vendor/model-identifier (or "none")
Collation-Witness: Dar Ihya al-Turath, Vol 1, p. 42
```

The automated CI gatekeeper (`Gate C.2`) audits this trailer. If an AI tool was declared, CI verifies that only eligible Zone 2 files were modified and that invariant tests pass with zero character differences.

### Anti-Pollution Scoring Protection
The [Scholarly Stewardship Dashboard](https://github.com/mishkaah/corpus/blob/main/docs/stewardship-dashboard.md) evaluates contributors strictly on verified scholarly outcomes, never on raw tag counts or automated line diffs:
- Points are awarded **only after passing all 5 automated CI gates and receiving approval from a distinct human reviewer (`Reviewer != Author`)**.
- If any AI-assisted contribution is found to contain hallucinations, unverified diacritics, or inaccurate attributions and is subsequently reverted or rejected, an elevated **`-15 point penalty`** is deducted from the contributor's stewardship score.

This combination of deterministic code invariants, transparent disclosure, and personal accountability ensures that technology serves the sacred text—never compromising its authenticity.
