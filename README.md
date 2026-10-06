# DSAN 6725 Final Project Proposals

Applied Generative AI for AI Developers, Fall 2026. Georgetown University.

Every team submits a final project proposal here as a pull request. The proposal is
your project title and abstract. The professor approves it before you start building.

**Due: Tuesday, October 6, 2026.**

## Team repositories, and what to do today

We create a separate project repository for each team in this organization. That
happens once every team composition is in Canvas.

**If you have not submitted your team composition in Canvas, do it now.** Every team
waits on the last one, so a single missing submission holds up the whole class.

Teams run 2 to 4 members. Five needs separate explicit approval from the professor,
and an approved five-person project has to carry enough work for all five to show a
real contribution.

Do not wait on us to start collaborating. Use any GitHub repository your team already
has, and move the code across when we hand you the real one.

## Overview

DSAN 6725 is an applied AI course. Your final project is production-quality software
that solves a real problem.

The proposal is the first gate. Write it so the professor can tell you two things:
whether the scope fits eight weeks, and whether the architecture holds up. Vague
proposals come back with change requests.

## Project ideas

Four areas to set some ideas in motion.

- **Semantic layer for agents over enterprise data.** Give agents a governed,
  business-aware view of enterprise data, so they work with data you already
  understand. Look at emerging open standards such as Open Semantic Interchange (OSI).
- **AI-powered code transformation.** Turn Python into Go or Rust for performance.
  Picture millions of agents optimized this way, and the aggregate compute saving is
  enormous.
- **Memory MCP server for coding assistants.** A persistent memory layer for AI coding
  tools, holding context across sessions.
- **Agent evaluations framework.** Benchmark multi-step agent tasks, and measure tool
  use and reasoning.

You can choose other topics that interest you. We review every proposal before
approving it, so bring us the idea your team wants to build.

The [DSAN 6725 Final Project](https://github.com/gu-dsan6725/spring-2026-georgetown-university-dsan6725-applied-genai-for-ai-developers-spring-2026-final-project)
repository has what students built last semester.

## Deliverables

These are due at the end of the semester. Your proposal commits you to the project
that produces them.

| Deliverable | What it is |
| ----------- | ---------- |
| Paper | A conference-style write-up of the problem, the design, and your results |
| Poster | A one-sheet visual summary you can stand next to and talk through |
| Demo video | A recording of your system working end to end |
| Code repository | The working system, documented well enough for a stranger to run |
| Slide deck | The talk you give at the final presentation |

Build all five for an audience outside this classroom. Students have taken this work
to industry meetups, company showcases, and academic workshops. Good projects end up
on LinkedIn and in front of prospective employers, so write the paper like a paper and
make the repository run on someone else's machine.

Grading weights for the individual pieces will come in due course.

## What the software must do

Every project is an agentic AI application, unless the professor approves another
approach. One agent or several is your call. Agents have to do the work.

- **Deployment.** The agents run on a VM, local or in the cloud.
- **Models.** Use local models, hosted models, or both, and say why.
- **Inference.** Decide how you serve and call the model, and report what it costs.
- **Agentic search.** Your agents go and retrieve what they need instead of carrying
  everything in the prompt.
- **Guardrails.** Constrain what the system says and does, and show the constraints
  working.
- **Performance.** Measure latency, throughput, and cost per task.
- **Evaluations.** Build an eval set and report your numbers against it.

Evaluations carry more weight than any other part of the build, and your submission has
to show the proof. Hand us the eval set, the harness that runs it, the scores, and what
you changed after reading them. Any claim that your system works needs numbers behind
it.

A web app that calls a chat completion endpoint once does not qualify.

## What to submit

One markdown file, `proposals/team-NN.md`, where `NN` is your two digit project group
number. Copy [TEMPLATE.md](TEMPLATE.md) and fill in five sections.

| Section | What goes in it |
| ------- | --------------- |
| Team Number | Your project group number, digits only |
| Team Name | A short name for your team |
| Team Members | Full name and NetID for each member, 2 to 4 members |
| Project Title | One line, specific about what you are building |
| Abstract | 250 to 300 words, and no more than 300 |

List every member in the file. One member opens the pull request for the team.

[proposals/team-00.md](proposals/team-00.md) is a worked example. Read it before you
start, then pick your own project idea.

## What the abstract must cover

Seven things, inside 300 words. One sentence each covers 5 and 6, so they cost you
little. If you cannot explain the project in 300 words, you do not yet know what you
are building.

1. **The problem.** What breaks today, who it hurts, and why it matters.
2. **The architecture.** Your agents, what each one does, and how they coordinate.
3. **The data and tools.** Name the data sources, APIs, and services, and confirm you
   can reach them.
4. **The evaluation.** Name the metrics, the baseline you run against, and where your
   ground truth comes from. Say what counts as working.
5. **The build.** Where the agents run, which models you use, and why those models.
6. **The numbers you will measure.** Latency and cost for one unit of work. Pick the
   unit: one report, one answered question, one document processed.
7. **The biggest risk.** The one thing most likely to stop you finishing in eight
   weeks, and your plan for it.

Most weak proposals fail on 3 and 7. A proposal comes back when the data source turns
out to be unreachable, or when a risk sits in the middle of the design and nobody
names it. Naming a risk is half the job. We also want the plan.

### What makes an evaluation credible

Evaluations carry more weight than anything else you build, so say enough in the
abstract for us to judge these five. Bring the detail to your first milestone.

- **A baseline.** Something simpler than your system, run on the same test set. BM25,
  a keyword filter, one prompt and no agents. Without a baseline, 73 percent means
  nothing.
- **Ground truth, and who made it.** Say how you produced the labels and how many you
  produced. Hand-labeling 200 examples is real work, so budget for it.
- **Metrics that measure what you claim.** Check this before you commit to one. Cosine
  similarity between a document and its summary rewards copying the document, so it
  tells you nothing about faithfulness. If you cannot say what a metric shows when your
  system fails, pick a different metric.
- **Sample size.** Report n beside every rate, with a confidence interval. Twenty
  questions cannot separate 80 percent from 60 percent.
- **A judge you checked.** If an LLM scores your output, score a sample yourself and
  report how often you and the judge agree. Until you check it, you do not know what
  its scores mean.

We would rather read a project that measured an honest failure than one that claims
success with no numbers behind it.

## How to submit

Fork the repository, add your file on a branch, and open a pull request. Run the
check before you push, so you find the problems before the reviewer does.

```bash
# Fork and clone. Team 07 is the example throughout.
gh repo fork gu-dsan6725/project-proposals --clone
cd project-proposals

# Work on a branch
git checkout -b team-07-proposal

# Start from the template
cp TEMPLATE.md proposals/team-07.md

# Edit proposals/team-07.md, then check it
uv run python scripts/validate_proposals.py

# Submit
git add proposals/team-07.md
git commit -m "Add project proposal for team 07"
git push origin team-07-proposal
gh pr create --title "Team 07 project proposal" --fill
```

Install `uv` first if you do not have it:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
source $HOME/.local/bin/env
```

Once the pull request is open, work through the checklist in its description.

## What the automated check covers

A GitHub Action runs on every pull request and checks the mechanics, so review time
goes to your idea. It reports on:

- Filename is `team-NN.md` with a two digit team number
- The team number inside the file matches the filename
- All five sections appear, with the headings from the template
- The roster lists 2 to 4 members, each with a name and a NetID
- The title fits on one line
- The abstract runs 150 to 300 words
- The template placeholder text is gone

If the check goes red, fix what it lists and push to the same branch. The pull request
updates itself, so do not open a second one. A green check only means the mechanics
are right. It says nothing about your idea.

Run the same check yourself at any time:

```bash
uv run python scripts/validate_proposals.py
```

## After you submit

The professor and TAs read your proposal, then merge it or request changes. A merge
means you can start building. If they request changes, push an update to the same
branch and ask for another review. Hold off on serious building until your proposal
merges.

## FAQ

**Can I submit alone, or with more than four people?**
Teams run 2 to 4 members, so working alone is out. Five needs separate explicit
approval from the professor. The automated check rejects a five-person roster, so note
your approval in the pull request and we will merge past the red check.

**Which team number do I use?**
Your project group number, the same one as your `Project Group N` team in the
`gu-dsan6725` organization. Ask on Slack if you do not know yours.

**Does every member open a pull request?**
No. One pull request per team, from any one member. List everybody inside the file.

**Can I use any model provider?**
Yes. Use whatever works best for your project.

**We want to change the project after approval.**
Small changes to the architecture or the data need no approval. Talk to the professor
before you change the problem statement, then update your file in a new pull request.

**My abstract runs 310 words and I cannot cut it.**
You can. The cuts hide in your first two sentences, where you explain background the
reader already has.

**Is 150 words a target?**
No. It is a floor that catches stubs. Aim for 250 to 300.

**Can I read other teams' proposals?**
Yes. This repository is public, and merged proposals are visible to everybody.
Copying from them breaks the [honor code](https://honorcouncil.georgetown.edu/).

**What is the late policy?**
The proposal counts as a project intermediate assignment. The syllabus late policy
for those applies.

## Repository layout

```text
.
├── README.md                          # this file
├── TEMPLATE.md                        # copy this to start your proposal
├── proposals/
│   ├── team-00.md                     # worked example
│   └── team-NN.md                     # one file per team, you add yours
├── scripts/
│   └── validate_proposals.py          # the check that runs on every pull request
└── .github/
    ├── pull_request_template.md        # the submission checklist
    └── workflows/
        └── validate-proposals.yml      # runs the check
```
