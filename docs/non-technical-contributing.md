# Non-Technical Contribution & Scholarly Review Guide

**English** · [العربية](./non-technical-contributing.ar.md)

---

> ### 🧭 Quick Links
> [Founding Reviewers Playbook](https://github.com/mishkaah/corpus/blob/main/docs/onboarding-and-workflow.md) · [Scholarly Stewardship Dashboard](https://github.com/mishkaah/corpus/blob/main/docs/stewardship-dashboard.md) · [Approved Sources](https://github.com/mishkaah/corpus/blob/main/docs/sources.md) · [Corpus Kanban Board](https://github.com/orgs/mishkaah/projects/1/views/2) · [Corpus Discussions](https://github.com/mishkaah/corpus/discussions)

---

## Welcome to Islamic Scholars & Arabic Linguists

We warmly welcome researchers, Islamic studies specialists, and Arabic linguists to help safeguard and review the classical texts in [`mishkaah/corpus`](https://github.com/mishkaah/corpus).

**You do not need any coding, Git, or command-line experience.** Every contribution step can be performed directly through your web browser on GitHub.com using structured issue forms, collaborative discussions, and the browser-based editor.

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
4. **Automated Verification Pipeline**:
   - Our automated continuous integration (CI) pipeline runs 5 verification gates on every contribution. It checks schema validity, verifies pure Arabic diacritics, and recalculates integrity digests automatically on your pull request branch.

---

## How to Contribute via the GitHub Web Interface

### 1. Join Discussions & Pick a Task
- Browse the [Corpus Kanban Board](https://github.com/orgs/mishkaah/projects/1/views/2) to find active milestone tasks (`M01`–`M04`).
- Participate in [Corpus Discussions](https://github.com/mishkaah/corpus/discussions) to review questions raised by fellow researchers on variant readings or narrator attributions.

### 2. Submit a Discrepancy or Proposal (Zero JSON Editing)
Select the appropriate structured form:
- **Report a documented textual discrepancy**: [Verified Textual Discrepancy Report](https://github.com/mishkaah/corpus/issues/new?template=01-verified-discrepancy-report.yml)
- **Propose qualifying an accredited source**: [Scholarly Source Qualification Proposal](https://github.com/mishkaah/corpus/issues/new?template=02-source-qualification.yml)
- **Submit a complete text revision**: [Complete Text Revision Task Form](https://github.com/mishkaah/corpus/issues/new?template=03-complete-text-revision.yml)

Fill out the form fields with your citation and verified vocalized text. Once a second reviewer validates the citation and applies `status:approved-revision-task`, automated tools prepare a pull request branch for final peer verification.

### 3. Direct Browser Edits for Compact Texts
For short primers, single-surah exegesis files, daily supplications, and documentation:
1. Navigate to the file in [`mishkaah/corpus`](https://github.com/mishkaah/corpus).
2. Click the **Pencil Icon (`Edit this file`)** at the top right of the GitHub file view.
3. Make your corrections with verified classical diacritics.
4. Select **"Create a new branch for this commit and start a pull request"** and submit.
5. Request review from a fellow reviewer (`Reviewer != Author`). The CI pipeline automatically handles all hash regenerations for you.

---

## Detailed Step-by-Step Playbook

For an in-depth walkthrough of the complete review workflow, Kanban lifecycle, cohort training curriculum, and quality scoring, read the dedicated **[Founding Reviewers Onboarding & GitHub Web Workflow Playbook](https://github.com/mishkaah/corpus/blob/main/docs/onboarding-and-workflow.md)**.

---

## Optional Local Visual Companion (For Technical or Assisted Setups)

> **Note**: This local tool is **entirely optional**. You do not need to install or run it to contribute; all scholarly review work can be done completely on GitHub.com.

For contributors with Bun installed who wish to inspect texts, commentaries, and narrator chains in an interactive split-view interface, you can launch **Mishkaah Studio**:

```bash
# In mishkaah/core:
bun run studio
```

Open `http://localhost:3333` in your browser to inspect texts side by side, trace narrator chains, and test entity annotations visually.
