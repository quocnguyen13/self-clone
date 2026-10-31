# self-clone

A research wiki that Claude Code compiles and maintains inside an Obsidian vault. You collect the sources and Claude writes the pages. Every fact on a page traces to a source file and carries that source's trust level. It follows Andrej Karpathy's [LLM Wiki](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) pattern.

This repository is a public copy of a private vault, built on 2026-10-31 from commit `1e15ff7`. It shows the system and what it produced. **It is not legal, regulatory or financial advice.** The wiki is a study aid compiled by an AI from public sources, and parts of it are marked unverified or contested.

## How it works
| Layer | Where | Who writes it |
|---|---|---|
| Sources | `raw/` | You add them. Claude reads them and never edits them |
| Wiki | `wiki/` (`sources/`, `entities/`, `concepts/`, `analyses/`, `overview.md`), `index.md`, `log.md` | Claude |
| Your thinking | `mine/` | You. Claude may only draft, in `mine/drafts/` |
| Input zones | `inbox/` | You, one door per operation |
| Rules and records | `CLAUDE.md`, `.claude/`, `system/` | The schema and skills; Claude writes the records |

The rules that make it trustworthy, all in `CLAUDE.md`:
- Every claim on a wiki page cites a file in `raw/`. A wiki page is never evidence for another.
- A page with an unsourced claim is `unverified`. When two sources disagree, the page is `contested` and shows both positions until you decide.
- Each source has a trust level: primary, secondary, commentary or AI. A claim backed only by a Claude output is marked `· AI` and counts as unsourced.
- Nothing runs on its own. Each operation waits for its command, Claude commits only after your review, and you do the push.

## The commands
| Command | What it does |
|---|---|
| `/research <topic>` | The only command that uses the web. Writes a report in `system/research/` in which every fact names its source, and lists sources for you to clip. Changes nothing in the wiki |
| `/import` | Checks new files in `inbox/sources/` against `raw/` for duplicates and newer versions. Given links, it downloads the PDFs behind them |
| `/ingest` | Compiles a set of sources into wiki pages and writes one review to `system/ingest/`. A document over 150 PDF pages is mapped first and then compiled one part per run |
| `/ask <question>` | Answers from the wiki and cites the raw file behind each claim. Writes nothing |
| `/file-answer` | Files the last answer as a page in `wiki/analyses/` |
| `/lint` | Checks citations, status, links, the index and trust levels, and compares claims across pages. Writes a report to `system/lint/` and fixes only the findings you name |
| `/drafts` | Checks Claude's insight drafts in `mine/drafts/` against `raw/` before you decide on them |

## What's in this copy
| Path | In this copy |
|---|---|
| `CLAUDE.md`, `.claude/` | The schema, the settings and the seven skills |
| `wiki/`, `index.md`, `log.md` | 87 pages on two subjects: knowledge systems (5 sources) and UK financial regulation (17 sources, including the whole Financial Services and Markets Act 2000). 71 are `verified`, 7 `contested` and 9 `unverified` |
| `system/` | Conventions, page templates, an Obsidian Bases review view, 10 ingest reviews, 12 lint reports, a research report with its capture list, and the test results. `context.md` is a blank template for you to fill in |
| `mine/projects/thinking-system/` | The project record: vision, charter, requirements, roadmap, backlog, decision log, architecture, operating instructions, module handovers and two retrospectives |
| `raw/` | Empty. The sources are other people's work, so they aren't republished. Links into `raw/` don't resolve here; the list below says where each source is |
| `mine/` (the rest) | Empty: these are personal notes |

A few personal and workplace details have been generalised in this copy.

## What the tests showed
- **MVP 1**, the core loop of ingest, ask and lint plus a thinking layer, closed on 2026-09-25 with all 6 exit criteria met.
- **MVP 2**, the research assistant, closed on 2026-10-31 after 55 of 55 tests, including a rerun of MVP 1's 21 tests.
- **The side-by-side.** Five questions went to both `/ask` and a default Claude chat. All 63 facts in the five `/ask` answers traced to `raw/`. The default chat searched the web each time and gave answers that were broader and more current, but none of its extra facts could be traced to a file in the vault.
- **Lint.** Running lint after each large set found errors that the set reviews had passed.

The details are in `system/test-results.md` and in the two retrospectives, `mine/projects/thinking-system/87 MVP Retrospective.md` and `91 MVP 2 Retrospective.md`.

## Sources
| Source | Publisher | Where |
|---|---|---|
| llm-wiki | Andrej Karpathy | [gist](https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f) |
| As We May Think (1945) | Vannevar Bush, *The Atlantic Monthly* | [PDF](https://web.mit.edu/sts.035/www/PDFs/think.pdf) |
| The PARA Method | Tiago Forte, Forte Labs | [blog](https://fortelabs.com/blog/para/) |
| Evergreen notes | Andy Matuschak | [notes](https://notes.andymatuschak.org/z5E5QawiXCMbtNtupvxeoEX) |
| Contextual Retrieval in AI Systems | Anthropic | [blog](https://www.anthropic.com/engineering/contextual-retrieval) |
| Financial Services and Markets Act 2000, whole Act and Part 1A | UK Parliament, legislation.gov.uk | [contents](https://www.legislation.gov.uk/ukpga/2000/8/contents), [PDF](https://www.legislation.gov.uk/ukpga/2000/8/data.pdf), [Part 1A](https://www.legislation.gov.uk/ukpga/2000/8/part/1A) |
| About the FCA | Financial Conduct Authority | [page](https://www.fca.org.uk/about/what-we-do/the-fca) |
| FCA Handbook: DISP 1.6, 2.7, 2.8 and 3.7 | Financial Conduct Authority | [1.6](https://handbook.fca.org.uk/handbook/disp1/disp1s6), [2.7](https://handbook.fca.org.uk/handbook/disp2/disp2s7), [2.8](https://handbook.fca.org.uk/handbook/disp2/disp2s8), [3.7](https://handbook.fca.org.uk/handbook/disp3/disp3s7) |
| FCA Glossary: micro-enterprise, small business | Financial Conduct Authority | [G2623](https://handbook.fca.org.uk/glossary/G2623), [G1095](https://handbook.fca.org.uk/glossary/G1095) |
| Final Notice to TSB Bank plc (2022) | Financial Conduct Authority | [PDF](https://www.fca.org.uk/publication/final-notices/tsb-bank-plc-2022.pdf) |
| Memorandum of Understanding (2024) | FCA and Bank of England | [PDF](https://www.fca.org.uk/publication/mou/mou-pra.pdf) |
| The PRA's approach to banking supervision (2023) | Bank of England, PRA | [PDF](https://www.bankofengland.co.uk/-/media/boe/files/prudential-regulation/approach/banking-approach-2023.pdf) |
| Prudential regulation | Bank of England | [page](https://www.bankofengland.co.uk/prudential-regulation) |
| How to complain | Financial Ombudsman Service | [page](https://www.financial-ombudsman.org.uk/consumers/log-ombudsman-connect/how-to-complain) |
| Financial Conduct Authority, Briefing Paper 7448 (2016) | House of Commons Library | commonslibrary.parliament.uk |
| Financial Conduct Authority | Wikipedia | [article](https://en.wikipedia.org/wiki/Financial_Conduct_Authority) |
| Who regulates what (2026-09-27) | A Claude chat, entered as an AI source | Not published |

Pages change, so a source may no longer match the version that was clipped. Each source page in `wiki/sources/` gives the date of the version that was used.

## Use it yourself
You need [Obsidian](https://obsidian.md), [Claude Code](https://claude.com/claude-code) and git. To read PDF pages, Claude Code needs Poppler (`pdftoppm`) on your PATH.
1. Clone the repo and open the folder as a vault in Obsidian.
2. Fill in `system/context.md`.
3. Start Claude Code in the folder by running `claude`.
4. Put a source in `inbox/sources/` and run `/ingest`. Ask questions with `/ask` and check the wiki with `/lint`.

If you run `/lint` on this copy as it is, it will report every citation as missing, because `raw/` is empty. To start from an empty wiki, first clear `wiki/`, `index.md`, `log.md` and the records in `system/ingest/`, `system/lint/` and `system/research/`.

## Licence
The text and files written for this project are licensed under [CC BY-NC 4.0](LICENSE): you can share and adapt them with credit, for non-commercial purposes. Quoted passages belong to their owners; see the list above. UK legislation is Crown copyright and is quoted under the Open Government Licence v3.0.

## Credits
The LLM Wiki pattern is Andrej Karpathy's. The vault is built with Claude Code and Obsidian. Its owner set the goals and made every decision. Claude wrote most of the files, and the decision log in `mine/projects/thinking-system/03 Decision Log.md` records who decided what.
