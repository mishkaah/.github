# Non-Technical Contribution & Scholarly Review Guide

**English** · [العربية](./non-technical-contributing.ar.md)

---

> ### 🧭 Quick Links
> [Mishkaah Studio](https://github.com/mishkaah/studio) · [Founding Reviewers Playbook](https://github.com/mishkaah/corpus/blob/main/docs/onboarding-and-workflow.md) · [Regulated AI Governance](./ai-governance.md) · [Scholarly Stewardship Dashboard](https://github.com/mishkaah/corpus/blob/main/docs/stewardship-dashboard.md) · [Approved Sources](https://github.com/mishkaah/corpus/blob/main/docs/sources.md) · [Corpus Kanban Board](https://github.com/orgs/mishkaah/projects/1/views/2) · [Corpus Discussions](https://github.com/mishkaah/corpus/discussions)

---

## Welcome to Islamic Scholars & Arabic Linguists

We warmly welcome researchers, Islamic studies specialists, and Arabic linguists to help safeguard and review the classical texts in [`mishkaah/corpus`](https://github.com/mishkaah/corpus).

**You do not need any coding, Git, or command-line experience.** You can perform all review and collation tasks visually in your browser—either via **Mishkaah Studio** on desktop and mobile, or directly through GitHub's standard web forms.

---

## Core Stewardship Foundations

To maintain the highest level of textual integrity and protect sacred heritage:

1. **Sacred Trust (*Amanah*), Not Authorship**:
   - We do not author or synthesize religious content. Every word and diacritic mark (*tashkeel*) is collated strictly against accredited critical printed editions (*Tahqiq*) or verified scholarly archives registered in [`SOURCES_MANIFEST.json`](https://github.com/mishkaah/corpus/blob/main/SOURCES_MANIFEST.json).
2. **Consensus-First Culture & Zero Solo Approvals (`Reviewer != Author`)**:
   - No collaborator may approve or merge their own contribution.
   - Textual discrepancies, ambiguous readings, or questionable sources are discussed first in **[Corpus Discussions](https://github.com/mishkaah/corpus/discussions)** so the team can reach scholarly consensus before merging.
3. **Mandatory Accredited Proof**:
   - Every submission must cite an exact approved source (Publisher, Editor, Volume, and Page). Submissions lacking proof are closed immediately (`status:rejected-no-proof`).
4. **3-Zone Regulated AI Standard**:
   - Generative authoring or rewriting of religious texts is strictly forbidden. Assistive tools in Mishkaah Studio operate under closed-world invariants, mandatory PR disclosure, and human sign-off. See the [Regulated AI Governance Standard](./ai-governance.md).
5. **Automated Verification Pipeline**:
   - Our automated continuous integration (CI) pipeline runs 5 verification gates on every contribution. It checks schema validity, verifies pure Arabic diacritics, and recalculates integrity digests automatically on your pull request branch.

---

## Primary Workspace: Mishkaah Studio (Desktop & Mobile Browser)

The recommended environment for scholarly review is **[Mishkaah Studio](https://github.com/mishkaah/studio)**:

- **Effortless Access**: Sign in with your GitHub account directly from your desktop browser, iPad, or mobile phone with zero software installation.
- **Visual Task Management**: Browse your assigned tasks, claim items from the live Kanban board, and track progress without managing branches or repositories manually.
- **Side-by-Side Collation**: Compare digital Arabic texts side-by-side with your physical printed edition, inspect commentaries (*tafseer*), and view narrator biographies.
- **Closed-World Entity Linking**: Highlight text spans and link them to canonical persons or places with automatic verification that underlying Arabic characters remain unperturbed (`stripInlineRefs(annotatedText) === originalText`).
- **Regulated AI Assistance**: Run read-only anomaly scans to catch typesetting slips and receive advisory pre-flight briefings safely under our 3-Zone framework.
- **Visual Peer-Review Inbox**: Review colleagues' contributions with clean, vocalized Arabic Before/After comparison cards and approve changes with one click (`Reviewer != Author`).

---

## Alternative Workspace: Direct GitHub.com Web Interface

Reviewers can also complete all tasks directly using standard GitHub.com web tools:

### 1. Structured Issue Forms (Zero JSON Editing)
Ideal for large compendiums like *Sahih al-Bukhari* or proposing source additions:
- **Report a documented textual discrepancy**: [Verified Textual Discrepancy Report](https://github.com/mishkaah/corpus/issues/new?template=01-verified-discrepancy-report.yml)
- **Propose qualifying an accredited source**: [Scholarly Source Qualification Proposal](https://github.com/mishkaah/corpus/issues/new?template=02-source-qualification.yml)
- **Submit a complete text revision**: [Complete Text Revision Task Form](https://github.com/mishkaah/corpus/issues/new?template=03-complete-text-revision.yml)

Fill in the form with your accredited citation and vocalized reading. Once validated with `status:approved-revision-task`, automated tools prepare a pull request for peer review.

### 2. Direct Browser Pencil Editor
For compact primers, single-surah exegesis files, daily supplications, and documentation:
1. Navigate to the target file in [`mishkaah/corpus`](https://github.com/mishkaah/corpus).
2. Click the **Pencil Icon (`Edit this file`)** at the top right of the file view.
3. Edit the text with verified classical diacritics.
4. Select **"Create a new branch for this commit and start a pull request"** and submit.
5. Request review from a fellow reviewer (`Reviewer != Author`). CI regenerates all integrity manifests automatically.

---

## Detailed Step-by-Step Playbook

For an in-depth walkthrough of the complete review workflow, Kanban lifecycle, cohort training curriculum, and quality scoring, read the dedicated **[Founding Reviewers Onboarding & GitHub Web Workflow Playbook](https://github.com/mishkaah/corpus/blob/main/docs/onboarding-and-workflow.md)**.
