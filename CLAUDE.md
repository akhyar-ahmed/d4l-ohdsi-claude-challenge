# CLAUDE.md — Claude Challenge: OHDSI Summer School 2027

## 0. Hard rules for this session

- **All code is written in English.** Identifiers, function/variable/class names, file names,
  commit messages, comments, docstrings, JSDoc, log messages, error strings, and inline
  documentation — English only, no German, no mixed language.
- **All deliverable artifacts are written in English too** (the summer school is an
  international OHDSI event; faculty and applicants are Europe-wide).
- Conversation with the user may be in German; everything written to disk is English.
- **Every artifact must carry the banner:** `WORKSHOP EXERCISE — not an announced D4L event`
  (visible at the top of documents, in the subject/first line of e-mail drafts, on the title
  slide of decks, and in the footer/header of the quiz dashboard).

## 1. The challenge

Data4Life AI Days · Day 1 · 60 minutes · teams of five.
Build a **launch package for the OHDSI Summer School 2027**.

Source brief: [ClaudeChallenge_print 1.pdf](data/ClaudeChallenge_print%201.pdf)

### Context
- D4L co-leads the **OHDSI Germany national node** (with TU Dresden and Medical University
  Lausitz / Carl Thiem Cottbus) and is driving the founding of **OHDSI Germany e.V.**
- Two real events are in planning: **OHDSI Summer School 2027** and **OHDSI Europe
  Symposium 2028**.
- Existing infrastructure: Slack `#ohdsi-events-internal-orga`, an empty Confluence space
  ("OHDSI Events 2027 & 2028"), a speaker list that is close to empty.

### Planning assumptions
- **Five days in Potsdam**, **30 places**.
- **Target group:** PhD students, early-career researchers, clinicians.
- **Purpose = adoption of Data2Evidence (D2E).**
  - At least **half the faculty must be external** (non-D4L).
  - **Success = participants leave with D2E running on data they control.**
- D4L **hosts** the school but **does not run** it.

## 2. Deliverables

| # | Deliverable | What good looks like |
|---|---|---|
| 1 | **Curriculum & agenda** | Lectures in the morning, hands-on lab in the afternoon, **one use case running through the whole week**, final day for participant presentations, external speaker list |
| 2 | **Call for applications** | Landing-page copy + application form (eligibility, what applicants submit, selection criteria, deadline, fee/funding model). Criteria must select for **data access** and **institutional weight** — adoption is the goal |
| 3a | **External faculty e-mail (draft)** | To an OHDSI partner: what we ask (one lecture, one lab, mentoring one project group), the hours, what to prepare, what they get, why the week is worth their time |
| 3b | **Internal D4L e-mail (draft)** | Short mail to the D4L colleague giving one session; makes clear D4L hosts but does not run the school |

### Stretch
| # | Deliverable | Notes |
|---|---|---|
| 4 | **Teaching slides (5–8)** | One session: why health data has to be standardised before it can answer anything |
| 5 | **Participant handbook** | One-pager: schedule, prerequisites, what to install before day 1, what to bring |
| 6 | **End-of-school quiz** | 8–10 questions, **interactive dashboard quiz** (this is the main code deliverable → English code, English comments) |

## 3. Guardrails (non-negotiable)

- Every artifact carries `WORKSHOP EXERCISE — not an announced D4L event`.
- **No real person is contacted.** Both faculty mails stay **drafts** on disk. Do not send
  mail, do not post to Slack, do not write to Confluence without explicit user approval.
- **No external logos** in anything shareable. **Nothing on a public URL** — do not publish
  Artifacts or otherwise expose material publicly unless the user explicitly asks.
- **Authentic material only**: real photos, real project stories, real numbers, real partner
  names, real past-event pictures. Do not invent statistics, partners, or quotes. If a number
  is not in the material, mark it as `[TBC]` rather than fabricating it.
- **Data protection note is required** for the application form (it collects CVs and research
  topics = personal data). Write down explicitly:
  - whether the data **may enter the scoring agent**,
  - the **lawful basis** (GDPR),
  - **retention period**,
  - **who can see it**.

## 4. Where output goes

Final packages are destined for Slack `#ohdsi-events-internal-orga` and the Confluence space
"OHDSI Events 2027 & 2028" — but only when the user explicitly triggers it. Default is: write
files into this repository.

## 5. Repository layout

```
data/                 Source material (read-only, do not modify)
deliverables/
  01-curriculum/      Agenda, week plan, external speaker list
  02-call-for-applications/  Landing-page copy, application form, selection criteria, DPIA note
  03-faculty-briefing/       external-faculty-invite.md, internal-d4l-session.md
  04-teaching-slides/        Stretch: standardisation session
  05-participant-handbook/   Stretch: one-pager
  06-quiz/                   Stretch: interactive dashboard quiz (code)
```

## 6. Background facts from the material (use these, don't invent)

### Data2Evidence (D2E) — [2-pager](data/2025_D2E%20for%20OHDSI%20(2-pager).pdf)
- Open-source, license-free platform by Data4Life, **released April 2025**, built for the
  **OMOP CDM**, FAIR principles at its core. On GitHub. `www.data2evidence.org`.
- Integrated OHDSI tools: **White Rabbit** and **Rabbit in a Hat** (scanning, metadata, ETL
  design), **DQD** (data quality), **Achilles** (characterization), **PHOEBE** (concept set
  recommendations), **ATLAS** (cohort definitions, study design).
- **Prefect** orchestrates and monitors ETL pipelines.
- **Jupyter Enterprise Gateway** integrated → interactive Python and R exploration.
- Cohort builder with real-time feasibility checks; cohorts exportable to ATLAS.
- Federated / privacy-preserving: **global collaboration without data transfer**.
- **Deployment: Docker + npm containerized; runs on macOS and Ubuntu; local or cloud.**
  → This is the basis for the "what to install before day 1" section of the handbook.

### OHDSI background — [K4L_OHDSI.pptx](data/K4L_OHDSI.pptx)
- OHDSI = Observational Health Data Sciences and Informatics, pronounced "Odyssey".
  Vision: *"A world in which observational research produces a comprehensive understanding of
  health and disease."*
- Three question types: **characterization**, **population-level effect estimation**,
  **patient-level prediction**.
- Building blocks: **OMOP CDM** (structure) · **Standardized Vocabulary** (semantics,
  `athena.ohdsi.org`, coordinated at Columbia University) · **HADES / methods** (engine) ·
  **community & conventions** (glue) · **the network effect**.
- Vocabulary example: "Diabetes mellitus type 2" → ICD-9-CM `250.00`, ICD-10 `E11`,
  SNOMED CT `44054006` all map to OMOP concept ID **201826**. *(Great slide-4 material.)*
- **Strategus** orchestrates HADES modules across sites: one analysis spec, executed
  identically at every node; only aggregated results leave the site.
- **EHDEN**: launched 2018, IMI public-private partnership; as of Sept 2024 **210 harmonized
  data sources from 30 countries**, **>70 publications**; **EHDEN Academy: >5,350 learners
  in >100 countries**, free and open.
- **DARWIN EU®**: established by EMA and the European Medicines Regulatory Network; ~250
  million patients, >100 research topics assessed, 88 studies completed or ongoing.
- Standards comparison: **OMOP** = analysing data at scale · **FHIR** = moving data between
  systems (dominant interoperability standard in Germany) · **openEHR** = capturing data at
  source. They complement, they do not compete.
- **OHDSI Germany**: founded spring 2021 (one of the oldest European nodes), ~130 community
  members, ~8 data partners, monthly community calls. Co-leadership: **Ben Illigens** (D4L),
  **Ines Reinecke** (TU Dresden / Med. Univ. Lausitz), **Gennadi Rabinovitch**,
  **Michèle Zoch** (TU Dresden).
- German landscape: **MII** = 38 university + 3 non-university DIZ = **41 sites**;
  **NUM-DIZ**: 22 sites committed to OMOP translation.
- Strategic trajectory: 2025 D4L becomes OHDSI Germany co-lead → 2026 OHDSI Germany e.V. +
  first network study → **2027 OHDSI Summer School (Berlin/Potsdam)** → 2028 OHDSI Europe
  Symposium (Berlin/Potsdam, >350 participants).
- D4L people already engaged in international summer schools (candidate faculty leads /
  contacts): Seolhwa (Oxford), Mario (Sweden), Martin (Columbia), Tim, Peter, Karthik
  (NUS Singapore), Tim & Ben (OHDSI APAC, AHDEN Australia, OHDSI Africa), Nicole Pratt,
  Cynthia Sung, Pablo (OHDSI LatAm).
- Data4Life is a **nonprofit** healthtech organization, supported by the **Hasso Plattner
  Foundation**. `www.data4life.care`

### D4L brand (from the master deck theme)
- Navy `#000080` (primary text/brand), white `#FFFFFF`, coral accent `#FF5F5A`,
  light blue `#BDD4F0` / `#EBF2FB`, warm `#FFD2C3`.
- `2026_D4L Master_Final (1).pptx` is an **empty layout master** — no content, use it only as
  a styling reference.

## 7. Working conventions

- Markdown for documents; one file per deliverable; kebab-case English file names.
- Prefix each generated file with the workshop banner as the first line.
- Any code (the quiz dashboard in particular): self-contained, English throughout, no
  external logos, runnable locally without a network dependency.
- Mark every unverified fact as `[TBC]` instead of guessing.
- 60-minute time box: deliverables 1–3 first and complete, stretch goals 4–6 only afterwards.

## 8. Coding conventions

- Commit messages: `<feat|fix|docs|refactor>: <sentence>` — the shortest English sentence that
  names the change and its purpose, e.g. `docs: Add git conventions to keep commits uniform`.
  `refactor` covers moving, renaming and deleting without a change in behaviour.
  Work happens on `main`; no branches for now.
- **Every commit Claude makes carries its session ID as a trailer**, so a commit can be traced
  back to the conversation that produced it. Read the ID from the environment — never guess it:

  ```bash
  git commit -m "docs: Add git conventions to keep commits uniform" \
    --trailer "Claude-Session-Id=$CLAUDE_CODE_SESSION_ID" \
    --trailer "Co-Authored-By=Claude Opus 5 (1M context) <noreply@anthropic.com>"
  ```

  Use `--trailer`, not a second `-m`: repeated `-m` puts a blank line between the blocks, and
  Git parses only the last paragraph as trailers — the session ID then degrades to prose and
  `git log --format='%(trailers:key=Claude-Session-Id,valueonly)'` finds nothing.
  Commits made by hand do not need it.
- **Everything written to this repository is in English** — code and documentation alike:
  identifiers, comments, docstrings, log and error messages, README files, commit messages,
  regardless of the language of the conversation.
- **Chat tone: scientific.** Factual, precise, short. No filler words, no apologies, no praise.
  Hold that register even when the user's own messages are casual or padded.
  Answer in whatever language the user is currently writing in.
- **Ask when the task, its goal or the direction of the session is unclear** — a question beats
  a guess. The user often dictates via a microphone app, so prompts can also carry unusual
  transcription errors; ask likewise when a passage is garbled or contradicts its context.
