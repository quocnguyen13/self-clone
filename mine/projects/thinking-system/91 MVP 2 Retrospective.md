---
type: project-doc
project: thinking-system
status: active
trust: ai-draft
origin: claude
created: 2026-10-31
reviewed: 2026-10-31
tags: [project/thinking-system, retrospective]
---

# 91 MVP 2 Retrospective

Back to [[00 Project Home]] · Plan in [[21 Roadmap]] · Backlog in [[22 Product Backlog]] · Previous: [[87 MVP Retrospective]] · Owned by M0 – Project Management ([[03 Decision Log]] D-070, D-117)

> [!abstract] What this is
> The retrospective at the end of MVP 2, the research assistant (M7–M9 and the exit run in M0), with the showcase gate that ends every MVP (D-082).
> - **§1–§3, the record:** compiled from handovers 88–90, `system/test-results.md` Runs 4–7 and the decision log.
> - **§4–§6, your view:** your input, wording tightened by Claude.
> - **§7, what it means next:** themes, the showcase gate, the tensions with current decisions, and the decisions to take.
> - **§8, the outcome:** filled in by M0 once you decide.

## 1. What was built
| Module | Dates | Delivered | Exit evidence |
|---|---|---|---|
| M7 – Batch Ingest and Trust | 2026-09-30 → 10-06 | `/ingest` takes a set of up to 8, with one brief, one move and one review; trust levels (primary, secondary, commentary, AI); conflicts where Claude proposes and you decide; Claude commits after your review. UK set: 7 sources | I1–I7: 7 of 7 |
| M8 – Research and Import | → 2026-10-14 | `/research` writes a report in which every fact has a source, a quote and its place; the capture list; `/import` checks the zone for duplicates and new versions and downloads PDFs on one approval; a Claude output enters as an AI source. UK set: 16 sources | IM1–IM6, RS1–RS4, AI1–AI4: 14 of 14 |
| M9 – Large Documents | → 2026-10-20 | A large document stays whole in `raw/`: mapped first, then compiled one part per run, with a resume path; the contents companion; the verdict **part** and the compare; citations with page and section. FSMA 2000, 1,263 pages: 49 Parts and 36 Schedules mapped, Parts II, 4A and XVI compiled, Part 1A compared | LD1–LD8: 8 of 8 |
| Exit, in M0 | 2026-10-20 → 31 | Criterion 6, the regression of MVP 1's 21 tests, and criterion 5, the side-by-side against a default Claude chat | Run 7: 21 of 21 after three fixes; 5 of 5 |

**Outcome:** MVP 2 complete on 2026-10-31, 6 of 6 criteria in [[11 Project Charter]] §11 met, 31 days after its scope was accepted (D-084, 2026-09-30). The exit was planned for 21–26 October and took eleven days, not six.

**The vault at MVP 2's close (2026-10-31):**
- 23 files in `raw/`: 22 sources and the FSMA contents companion. 5 on knowledge systems, 17 on UK regulation, among them the whole FSMA 2000.
- 87 wiki pages: 71 `verified`, 7 `contested` (MVP 1's two disagreements of view), 9 `unverified` (8 hold `· AI` leads, 1 a general-knowledge name). 3 analysis pages.
- 10 set reviews, 12 lint reports, 1 research report and the capture list.
- 7 skills: `research`, `import`, `ingest` (with `ai-source.md` and `large-source.md`), `ask`, `file-answer`, `lint`, `drafts`.
- 14 drafts, all checked, none decided. 5 insights, still the five Claude wrote in MVP 1.

**The project record:** MVP 2's tests: 55 of 55 across Runs 4–7, with reruns. Decisions D-072 to D-122 since MVP 1 closed. The backlog moved to Jira (KAN-1 to KAN-50). About 65 vault commits since 2026-09-30.

## 2. What the system caught in itself
- **Lint after a set catches what the set review passes.** After M7's set, 6 high errors; after the Ombudsman set and the Claude output, 5 more. The reviews had passed all of them, which led to D-103: `/lint` after every large set. In M9, lint after each FSMA part found 0, 1, 2 and 0 high errors, among them a wiki page cited as evidence and wording stronger than the Act.
- **Conflicts surfaced and settled in the open.** Three in the set of five (two firm counts, "renamed" or "abolished"), two on complaint deadlines (the FOS guide against DISP), one of scope on Part 4A against the MoU. Each was resolved by you, with the claim set aside still on the page.
- **AI claims stay leads until a source backs them.** The Claude study note gave 108 statements: 28 backed, 67 kept as `· AI` leads, 1 contradicted. The FSMA parts later turned the leads on ss. 19, 23 and 55E–55F into primary citations. Asked to mark TSB Bank `verified`, Claude declined and listed the claims that lacked a source.
- **The regression found three gaps the module tests had missed:** `/ask` misreporting the wiki's own state (KAN-48), an offer to delete "as an exception" (KAN-49), and lint reports overstating what they read (KAN-50). Each was fixed in the thread that owns the skill and rerun.
- **Drafts.** 12 of the 14 drafts had problems, and every flag M0 traced held against `raw/`.
- **The side-by-side.** Every one of the 63 facts in the five `/ask` answers traced to `raw/` with its level. The default chat, which searched the web every time, contradicted `raw/` nowhere, but 25 of its facts were nowhere in `raw/`, most of them current practice.
- **Pattern:** as in MVP 1, the errors sit in Claude-written synthesis (drafts, claims across pages, summaries of the wiki itself), not in the sources, and the checks that open `raw/` catch them.

## 3. Where the plan changed
| Decision | Change | Why |
|---|---|---|
| D-085, D-022 | A set per run replaced one source per run | Your §5.1 in doc 87: ingest was too heavy for research |
| D-090, D-008 | Claude commits after your review; the push stays yours | Fewer steps, still under your approval |
| D-103 | `/lint` recommended after every large set | Set reviews passed errors lint caught |
| D-102 | An AI lead stays on the AI source page, not on the subject's page | A judgement call in AI2, written down |
| D-104, D-105 | The backlog moved to Jira; new items take their key | Your control of status and sprints |
| D-106 | Skills keep to Glob, Grep and Read; the shell is for git and `/import`'s download | Shell use in runs, harmless but against the rules |
| D-114 | Claude's files reach the vault through the staging folder | Stray copies in the vault |
| D-115 | A PDF without contents pages is mapped from the publisher's contents page | The whole-Act PDF has none |
| D-117 | MVP 2's exit ran in M0, with dates | No build module was left |
| D-121 | A batch names the commit it was built on, and its deploy stops if any of its files changed since | Two batches overwrote another thread's work |
| D-119, D-120, D-122 | `/ask`'s path when no page covers the subject; no offer to delete; lint's scope between full runs | The regression |

### 3.1 What Claude observed while building
| Observation | Your view |
|---|---|
| **Deploys are the weak point.** Two batches overwrote another thread's work (M4's over change log 1.62, M2's over doc 40 §4), one deploy missed the zipped skill, and one batch was deleted before it was deployed. D-121 stops the first kind; the zip step and the order of batches still rest on you | |
| **Mirrors, still.** Doc 40 copies every skill, so each skill change is two edits, and the M2 overwrite hit exactly that copy. Open since doc 87 §3.1 | |
| **The environment matters.** Poppler went missing and blocked five drafts until it was reinstalled and Claude Code restarted with the new PATH | |
| **The thinking layer is still Claude's.** `mine/` holds no page you wrote. 14 checked drafts wait for your decision; the 5 insights are MVP 1's (B-015) | |
| **Traceable, but not current.** The side-by-side shows the vault wins on traceability and loses on currency: targets, Bills and procedures the web knows and `raw/` doesn't. The answers named the gaps: the regulators' service standards and authorisations performance report, the Glossary's "PSD complaint" and "EMD complaint", the Treasury's s. 23(1B) order | |
| **Jira without sprints.** Sprints, releases and the statuses Refined, Ready and Dropped were never enabled, so modules ran without sprints | |

## 4. What worked for you
*Your input, 2026-10-31:* you want more time using the system before you judge it. §4 stays open until the usage period on your domains ends (D-124).

## 5. What didn't fit how you work
*Your input, 2026-10-31:* no preference yet; open with §4. The candidates Claude observed are in §3.1.

## 6. What you want next
*Your input, 2026-10-31, at a public level (D-018).*
- **A deeper domain:** more of the domains you work in, at a public level, in the wiki. The UK set so far covers the regulators, the perimeter, permission and complaints, not the conduct rules for your products.

## 7. What this means next
Claude's reading of §1–§3. Nothing here is decided until §8 records it.

### 7.1 Themes
| # | Theme | From | What it would change |
|---|---|---|---|
| T1 | **Keep provenance at the core** | §2 | Nothing. It is the test every other change must pass |
| T2 | **Safer, lighter deploys** | §3.1 | One deploy script per batch: unzip, the D-121 check, copy, `git add`, commit. Related to B-026, project docs written straight into the vault |
| T3 | **Keep the wiki current** | §2, §3.1 | Dated facts refreshed on a schedule (the award cap changes every 1 April); the side-by-side's gaps onto the capture list |
| T4 | **Your thinking layer** | §3.1 | Decide the 14 drafts; your first own insight (B-015) |
| T5 | **The work assistant** | D-081 | MVP 3 as planned: a standards library and a PRD job (E-06) |
| T7 | **A deeper domain** | §6 | Your domains into the wiki with the loop MVP 2 built; no new capability needed (KAN-51) |
| T6 | **Fewer mirrors** | §3.1 | Doc 40 points to the skills instead of copying them, or a check that the copy matches |

### 7.2 The showcase gate (D-082)
**The bar (D-083):** a chat answer from the vault beats a default Claude answer through its fact guarantee, while Claude keeps its ability to research, with the four capabilities it names. All four are built and tested, and the side-by-side measured the guarantee: 63 of 63 `/ask` facts traced, against a default chat that was broader and more current but traceable to nothing in the vault. On the bar as written, it is met.

| Option | What it means | For | Against |
|---|---|---|---|
| **a. Showcase now, lean** | Release S1 in M0 before MVP 3: the public copy (B-029, with the D-018 check of every file), the case study (doc 01, B-028) and a short demo (B-030) | The bar is met and the evidence is fresh (Run 7); a finished story to point to | Delays MVP 3; the data-boundary check and the writing take time |
| **b. MVP 3 first** | Showcase after the work assistant | A PRD job is closer to a product owner's daily work, so a stronger story | The research story waits, and its evidence ages |
| **c. Both, in parallel** | MVP 3's scoping in M0 while the lean showcase is built | Nothing waits | Two streams for one person; the risk of neither finishing |

**Claude's lean: a,** with MVP 3's scoping started in M0 while you review the showcase drafts. The bar you set is met and documented; the other E-09 items (docs 04, 12, 13, 50, 60, 71) can follow later.

### 7.3 Tensions with current decisions
| Decision | Says today | Pull | Options |
|---|---|---|---|
| D-079 | The public copy leaves out `raw/`, `mine/` and anything personal | The case study must show traced facts | Show citations and short quotes only; FSMA itself is Crown copyright under the Open Government Licence, but the rule can stay as it is |
| D-104 | Each module is a Jira sprint | Sprints were never enabled | Enable them for MVP 3, or drop sprints from the mapping in doc 22 §1.3 |
| D-071 | Every module thread stays open | Seven threads now maintain skills, and two of them overwrote others | D-121 covers it; or route all doc 40 edits through M0 |

### 7.4 Decisions to take
1. **The showcase gate:** a, b or c.
2. **If a or c:** the E-09 items in the lean showcase (B-028, B-029, B-030 at least).
3. **MVP 3's scope:** the standards library and the PRD job as D-081 set, or another first job.
4. **Deploys:** a backlog item for one deploy script per batch (T2).
5. **Currency:** the side-by-side's gaps onto the capture list now, or in MVP 3 (T3).
6. **The 14 drafts and B-015:** your decisions, when you choose (T4).
7. **Jira sprints:** enable them, or change D-104's mapping.

## 8. Outcome
Filled in 2026-10-31.
- **The showcase gate (decision 1): yes, a lean Release S1** (D-123). M0 builds the public copy (B-029), the case study, doc 01 (B-028), and a short demo (B-030), each for your acceptance; the other E-09 items wait. KAN-28 to KAN-30 moved to To Do.
- **What comes next: a deeper domain** (D-124). After S1, a usage period puts your domains into the wiki with MVP 2's loop as built (KAN-51, from public sources only). §4 and §5 are completed after it, from use rather than memory, and MVP 3's scope is set then: D-081's work assistant, or another first job (decision 3).
- **Decisions 4–7** stay open: deploys (T2), currency (T3, folded into KAN-51's first topics), the drafts and B-015 (yours, when you choose), and Jira sprints.
