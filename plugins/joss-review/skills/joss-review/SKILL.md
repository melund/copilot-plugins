---
name: joss-review
description: >-
  Guide for reviewing Journal of Open Source Software (JOSS) submissions. Use
  this skill whenever the user is reviewing a JOSS paper, preparing a JOSS
  review, drafting review comments for a JOSS submission, evaluating research
  software against JOSS criteria, or checking whether a software paper is ready
  for JOSS. Also use it if the user mentions "openjournals/joss-reviews",
  a JOSS review issue, or wants help writing constructive reviewer feedback for
  a scientific software submission.
license: BSD-3-Clause
---

# JOSS Review Guidelines

This skill condenses the official [JOSS review criteria](https://joss.readthedocs.io/en/latest/review_criteria.html) and [review checklist](https://joss.readthedocs.io/en/latest/review_checklist.html) into an actionable guide. JOSS reviews are checklist-driven — a review is incomplete until every item is checked off.

## How to Conduct a JOSS Review

Work through the review in this order. The sequence matters because early checks can save significant time — there's no point doing a deep paper review if the repository was made public last week (that's a desk rejection).

1. **Screen first.** Check the repository URL, license file, and commit history. If the project was made public days before submission or all commits are concentrated in a few weeks, flag it to the editor immediately rather than continuing with a full review. These are pre-review screening gates.

2. **Install and test.** Clone the repo, follow the installation instructions, and verify the core functionality works. This is your most valuable contribution as a reviewer — you're the real-world user test. Note any friction, missing dependencies, or unclear steps.

3. **Read the paper.** Check that all required sections are present and substantive (see checklist below). The paper should be short and focused — it is not software documentation.

4. **Evaluate the documentation.** Walk through the README, examples, and API docs as if you were a new user trying to adopt this software. Can you understand what it does and how to use it without reading the source code?

5. **Write constructive feedback.** Grade as Accept, Minor Revisions, or Major Revisions. JOSS doesn't reject outright for major revisions — authors get the time they need. Frame comments as suggestions with reasoning, not demands.

### Review Output Format

Structure your review as a checklist comment on the JOSS review issue. Use this template:

```markdown
## Review checklist for @<author>

### General
- [x] **Repository**: Source code is available at the stated URL.
- [x] **License**: Repository contains a plain-text LICENSE file with an OSI-approved license.
- [x] **Authorship**: Submitting author has made substantial contributions. Author list appears appropriate.
- [ ] **Scope**: <comment if any concern, otherwise check>

### Development History
- [x] **Timeline**: <brief note on what you observed>
- [x] **Open development**: <brief note>
- [ ] **Collaboration**: <concern or note>
- [x] **Good practices**: <brief note>

### Functionality
- [x] **Installation**: Installed successfully on <OS/environment>.
- [x] **Functionality**: Core claims verified.
- [x] **Performance**: No performance claims / claims verified.

### Documentation
- [x] **Statement of need**: Present and clear.
- [ ] **Installation instructions**: <issue if any>
- [x] **Example usage**: Examples present and functional.
- [x] **API documentation**: <level of coverage>
- [x] **Tests**: Automated test suite with CI.
- [x] **Community guidelines**: CONTRIBUTING.md present.

### Paper
- [x] **Summary**: Clear and accessible.
- [x] **Statement of need**: Present with clear problem and audience.
- [ ] **State of the field**: <missing comparison with X, or sufficient>
- [x] **Software design**: Thoughtful discussion of trade-offs.
- [x] **Research impact**: <evidence cited>
- [x] **AI disclosure**: <present / absent>
- [x] **Writing quality**: Well written.
- [x] **References**: Complete and properly formatted.

### Overall recommendation
<Accept / Minor Revisions / Major Revisions>

### Comments
<Constructive feedback organized by topic. Explain what you'd like to see changed and why.>
```

## Review Checklist

Each item below maps to a checkbox in the JOSS review issue. The explanations describe what "good", "acceptable", and "unacceptable" look like so you can calibrate your judgment.

### General Checks

- [ ] **Repository**: Source code available at the repository URL.
- [ ] **License**: A plain-text `LICENSE` or `COPYING` file with an [OSI-approved](https://opensource.org/licenses/alphabetical) license. A phrase like "MIT license" in a README doesn't count — there needs to be an actual license file because downstream users need to copy and include it.
- [ ] **Contribution and authorship**: The submitting author has made major contributions (check the commit history). The author list seems appropriate and complete. Purely financial contributions don't qualify for co-authorship, but authorship norms vary by community — raise questions rather than making judgments.
- [ ] **Scope and significance**: The software demonstrates research impact or credible scholarly significance rather than being a one-off tool for a single analysis. Look for publications citing the software, adoption by other groups, integration into research workflows, or novel capabilities. Flag questionable scope to the editor — the final call on scope is theirs.

### Development History and Open-Source Practice

These criteria double as **pre-review screening gates**. If something clearly fails here (repository made public days before submission, all commits in a two-week window), stop and flag it to the handling editor for a potential desk rejection. This saves everyone time.

The reason JOSS cares about development history is that it distinguishes sustained research software from code dumps. A healthy project shows iterative refinement, community interaction, and a trajectory of improvement — signals that the software will continue to be maintained.

- [ ] **Development timeline**: Look for commits distributed over 6+ months showing gradual feature development. Sporadic or bursty patterns over that period are fine — research software often develops in bursts around paper deadlines or grant cycles. But if all commits are concentrated in the last few weeks, that's a red flag.
- [ ] **Open development**: The repository should have been public from early on, with evidence of releases/tags, public issues/PRs, and ideally external engagement. At minimum, 6 months of public history. Software developed privately can still pass if the authors demonstrate substantial effort and 6+ months of public availability with evidence of use.
- [ ] **Collaborative effort**: Multiple contributors with code review through PRs is ideal. Single-author projects are common in research and are acceptable when the paper or author list shows evidence of community engagement or collaborative context (e.g., co-authors who are domain experts, publications describing community use, or a long track record of external adoption).
- [ ] **Good practices**: OSI license (required), documentation, automated tests or CI, tagged releases, contribution guidelines, and support channels. All elements present and well-maintained is ideal. Core elements present is acceptable. Missing critical elements or what looks like a one-time code dump is not.

### Functionality

Install the software and verify it works. This is the part of the review that authors value most — real user testing.

- [ ] **Installation**: Does installation proceed as documented?
- [ ] **Functionality**: Do the functional claims hold up?
- [ ] **Performance**: If performance claims exist, can you confirm them? (If none, check this off.)

### Documentation

Evaluate documentation from the perspective of a researcher who wants to adopt this software. Can they understand what it does, install it, and use it for their own work?

- [ ] **Statement of need**: Authors clearly state what problems the software solves, who the target audience is, and how it relates to other work.
- [ ] **Installation instructions**: Dependencies documented and installation automated. Python packages should be pip-installable with proper packaging. For languages without mature packaging (e.g., Fortran with a Makefile), a clear dependency list plus build script is acceptable.
- [ ] **Example usage**: Examples showing how to use the software, ideally solving real-world analysis problems.
- [ ] **API documentation**: All functions/methods documented with examples is ideal. Core API documented is acceptable. Completely undocumented API is not — use your judgment on what level of coverage is reasonable for the project's size and scope.
- [ ] **Automated tests**: An automated test suite with CI (GitHub Actions, etc.) is ideal. Documented manual verification steps are acceptable. No way to verify whether the software works is not.
- [ ] **Community guidelines**: Clear guidelines for contributing, reporting issues, and seeking support.

### Software Paper

The JOSS paper is intentionally short and focused. It should contain only: authors/affiliations, a summary for non-specialists, statement of need, comparison with related work, mentions of research use, and key references. It should not contain API documentation or software tutorials — those belong in the software's own docs.

Verify all required sections are present and substantive:

- [ ] **Summary**: Clear description of high-level functionality for a diverse, non-specialist audience.
- [ ] **Statement of need** (required section): Clearly labeled section stating what problems the software solves, the target audience, and relation to other work. This should make a compelling case for why the software is needed. Vague problem descriptions or missing audience are not acceptable.
- [ ] **State of the field** (required section): Compares with commonly-used packages. When related tools exist, the authors need a clear "build vs. contribute" justification — why they created a new tool instead of contributing to an existing one. Ignoring existing similar tools is not acceptable.
- [ ] **Software design** (required section): Discusses architectural trade-offs, the design chosen and why, and why these choices matter for the research application. This should show meaningful design thinking, not just "we used Python with Flask" — the reader should understand *why* the architecture suits the problem.
- [ ] **Research impact statement** (required section): Evidence of realized impact (publications, external users, integrations) or credible near-term significance (benchmarks, reproducible materials, community-readiness signals). The evidence should be concrete and specific — vague statements about future potential don't count.
- [ ] **AI usage disclosure** (required section): Transparent disclosure of any generative AI use in software creation, documentation, or paper authoring. If no AI was used, state it explicitly. Evasive or missing disclosure is not acceptable.
- [ ] **Quality of writing**: Well written, no structural or language issues.
- [ ] **References**: Complete list with proper [citation syntax](https://rmarkdown.rstudio.com/authoring_bibliographies_and_citations.html#citation_syntax). Point out relevant published work that isn't cited — especially prior similar tools.

## Quality Calibration Tables

Use these tables to calibrate your assessment. "Good" means you can check the box without comment. "OK" means you can check it but may want to suggest improvements. "Not acceptable" means leave it unchecked and explain what's needed.

### Development History

| Criterion | Good | OK | Not Acceptable |
|---|---|---|---|
| Timeline | 6+ months gradual development | 6+ months sporadic/bursty | All commits in last few weeks |
| Openness | Public from inception, releases, community interaction | Public 6+ months, ongoing development | Public immediately before submission |
| Collaboration | Multiple devs, PRs, code review | Single author + community engagement evidence | Single author, no engagement at all |
| Practices | License, docs, tests, releases, contrib guidelines | Core elements present | Missing critical elements or code dump |

### Documentation

| Criterion | Good | OK | Not Acceptable |
|---|---|---|---|
| Installation | Simple install following language conventions | Dep list + install script | Unclear deps, no automation |
| API docs | All functions documented with examples | Core API documented | Undocumented |
| Tests | Automated suite with CI | Documented manual verification | No way to verify functionality |

### Paper Sections

| Section | Good | OK | Not Acceptable |
|---|---|---|---|
| Statement of need | Clear problem, well-defined audience, broad context | Key elements present, less specific | Vague problem, unclear audience |
| State of the field | Thorough comparison, clear justification | Identifies related work, explains differences | Ignores existing tools |
| Software design | Thoughtful discussion of decisions and trade-offs | Clear architecture with some rationale | Generic description, no reasoning |
| Research impact | Multiple citations, external users, strong benchmarks | Evidence beyond authors' group | Only aspirational statements |
| AI disclosure | Specific disclosure with verification methods | No-AI statement or general disclosure | Missing or evasive |

## Additional Guidance

### Submissions That Reimplement Existing Work

Software that re-implements solutions from other packages is accepted as long as it meets all criteria and cites similar prior work. If you know of relevant published work the authors missed, point it out.

### Proprietary Languages

Submissions using proprietary/closed-source languages are acceptable if they meet all other criteria and you can install and verify the software. Suggest compatibility with open-source variants where possible.

### Repository Hosting

Repositories must be on platforms where outside users can freely open issues and propose changes (GitHub, GitLab, Bitbucket, etc.). Platforms requiring manual account approval or payment are not acceptable.

### AI Policy

JOSS has a [detailed AI policy](https://joss.theoj.org/about#ai-policy) covering acceptable use by both authors and reviewers. Familiarize yourself with it before starting.

## Resources

- [JOSS Review Criteria](https://joss.readthedocs.io/en/latest/review_criteria.html)
- [JOSS Review Checklist](https://joss.readthedocs.io/en/latest/review_checklist.html)
- [JOSS Reviewer Guidelines](https://joss.readthedocs.io/en/latest/reviewer_guidelines.html)
- [JOSS Submission Guidelines](https://joss.readthedocs.io/en/latest/submitting.html)
- [OSI Approved Licenses](https://opensource.org/licenses/alphabetical)
- [JOSS AI Policy](https://joss.theoj.org/about#ai-policy)
