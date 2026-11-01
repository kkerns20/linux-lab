# Project Olympus development roadmap

**Last updated:** 2026-11-01. **Status:** Idea workshop and proposed planning overview; documentation approved for publication 2026-11-01. Project usefulness, selection, and the 90-day experiment remain open. The experiment has no agreed start date. No application, content service, customer demand, or revenue is established by this plan.

## Purpose and scope

Coordinate useful family tools, practical development, and original content experiments without losing the Home Lab's infrastructure focus. This page owns the experiment backlog, sequencing, and decision gates. The [home server roadmap](home-server-roadmap.md) continues to own storage, reliability, hardware, and migration; the [Solutions Engineering roadmap](solutions-engineering-roadmap.md) continues to own portfolio capabilities and standards.

Project Olympus is used here as the broader planning umbrella; **Olympus the permanent server remains planned, not deployed**. Experiments do not depend on purchasing or deploying that server.

## Sources and evidence

Three planning responses were supplied by the owner on 2026-11-01: the coordinated device workshop/foundation-first proposal; the three-workstream application/content proposal; and the four-leading-ideas response beginning “You're seeing the same pattern I am.” The last two supply the core expansion ideas requested for preservation. Original response dates and formal Project Source titles are TODO. These are proposals, not execution evidence; the owner's latest direction is to continue workshopping their usefulness before selecting projects.

The first response proposed foundation work in month 1, reporting automation in month 2, and demand validation in month 3. The expanded response proposed a family-use app and original content alongside infrastructure work. The four-idea response recommended reporting as the first commercial experiment and gradual household productivity work. Preserve these as alternative sequencing suggestions: the 90-day table below captures the expanded proposal, not a settled schedule. The family organizer versus creator dashboard choice and the commercial target audience remain open.

The recovered [Home Lab HQ conversation](https://chatgpt.com/c/6acd10de-ff78-83e8-bed8-1d4f958dcd4e) provides continuity. The staged gates and workload allocation below are proposed refinements for review, not previously agreed commitments.

Repository baseline reviewed on 2026-11-01: GitHub main at `b598fe87400749a9566cf2596125b808697a0db1`. GitHub main is authoritative after approved changes are published. Local review drafts and ChatGPT Project uploads are snapshots; neither automatically synchronizes with main.

## Priorities and constraints

1. Protect the Home Lab foundation: preserve the [current infrastructure priorities](../docs/PROJECT-STATUS.md#prioritized-next-actions), especially security review, off-device backups, and controlled recovery planning. Experiment milestones must not displace necessary maintenance.
2. Select one small first application and one lightweight content experiment. **Family organizer versus creator production dashboard remains open.** Choose from a concrete recurring problem and an identifiable test user.
3. Explore spreadsheet reporting as the leading commercial hypothesis after initial learning. A recommendation to test it is not evidence of willingness to pay.
4. Defer broad personal-assistant and second-brain integrations until a narrow use case and data boundaries are clear.

Use existing devices; consult [Atlas](../docs/devices/atlas.md), [Athena](../docs/devices/athena.md), and the [inventory](../docs/devices/README.md) for documented roles. Do not assume new workloads fit Hephaestus or that a particular runtime is installed. Begin with local prototypes and synthetic/sample data. Hosting, stack, integrations, and production placement are TODO.

Proposed workshop roles extend existing documented device roles: Atlas for coding, integrations, documentation, editing and demonstrations; Athena for independent Linux development/testing and automation; Hermes for portable review, mobile usability tests and demonstrations; Hephaestus for possible shared experiments only after capacity, security and recovery review. An iPhone 12 Pro Max was suggested for footage and mobile web testing; its availability/configuration is not independently verified here. These suggestions do not establish new deployments, installed tools, or continuous availability. Avoid duplicating functions already served adequately by existing household tools unless a specific benefit is clear. Do not make Hephaestus a public production server or host customer-dependent work without a separately approved design addressing its documented gaps.

**Time:** approximately 5–7 hours/week across infrastructure and all experiments, not per workstream. A trial allocation is 2 hours infrastructure, 2–3 hours application work, 1 hour content, and up to 1 hour review/documentation. If maintenance exceeds its allowance, reduce experiments. Track actual hours and simplify scope before adding work.

**Spending:** minimize new spending and reuse current hardware and available tools. A spending ceiling, including subscriptions, API usage, hosting, and content tools, is TODO before incurring costs; no purchases are authorized by this roadmap.

## Three coordinated workstreams

| Workstream | Intended value | Initial experiment and boundary |
| --- | --- | --- |
| Home & Family | Improve a recurring household task and learn from real family feedback | Candidate family organizer; later a narrowly scoped personal assistant or household automation. Real family information and access requirements need review before use. |
| Build & Develop | Build practical application, data, API, and automation skills; potentially create portfolio evidence | First small web app; later spreadsheet dashboard/reporting prototype for one business problem. Map evidence to existing Solutions Engineering phases rather than create a competing curriculum. |
| Create & Publish | Practice original storytelling and a repeatable production workflow; learn what an audience finds useful | Original Shorts/TikTok experiments and a lightweight production process. Public release requires explicit authorization. Audience growth and monetization are hypotheses. |

One artifact may support multiple workstreams: a creator dashboard could be the first development project and support the content workflow. Reuse work without counting it as separate completed projects. Record results in one relevant project page and link it here.

## Leading idea backlog

All four ideas are **exploratory and unbuilt in this plan**.

| Idea | Smallest useful test | Proposed success evidence | Main unanswered question |
| --- | --- | --- | --- |
| Spreadsheet dashboard/reporting automation | Turn one synthetic or authorized sample spreadsheet into a repeatable report/dashboard; document input validation and refresh steps | Reconcile outputs to known totals, repeat the run, and compare time/effort with a manual baseline; later obtain feedback from a potential user | Which recurring report, user, data source, and measurable pain justify a prototype? |
| Original Shorts/TikTok production workflow | Manual-first process from idea and original script to recording/editing, review, and release; automate only a demonstrated bottleneck | Record production time, complete original pieces, and review available engagement/retention feedback after authorized release | Which topic, audience, format, rights-cleared assets, and sustainable cadence? |
| Personal assistant / daily briefing | Generate one reviewable briefing from a small approved set of inputs, initially sample data | Check accuracy, relevance, missed items, and time saved across repeated trials | Which inputs and actions are useful, and what access is appropriate? Begin with read-only inputs; any later actions need separate scope and approval. |
| AI second brain | Retrieve answers from a small curated, non-sensitive collection with references | Check answers against source material, identify unsupported claims, and demonstrate update/export/delete behavior | What knowledge is worth capturing, and what privacy, retention, and retrieval requirements apply? |

Reuse API access, data processing, authentication, scheduling, failure handling, and presentation capabilities where justified; avoid building four separate AI systems. The second-brain idea should build on GitHub documentation with retrieval and summarization rather than replace its authority or mandate a new notes platform. If demand emerges, assess a scoped implementation service before assuming a subscription product.

The source responses also mention a Home Lab dashboard, portable consulting demonstrations, and household automation. Retain these as secondary candidates, not additional active projects. Messaging agents, voice agents, listing-video services, website building, ad automation, and outreach automation remain outside the leading shortlist; they require fresh usefulness and support-cost evaluation before promotion.

The creator production dashboard is a possible first app supporting the second idea. The family organizer is the alternative first app; it does not imply committing to the broader assistant or second-brain ideas.

## First-project choice — open

| Option | Choose it if… | Minimum trial |
| --- | --- | --- |
| Family organizer | A family member can name a recurring coordination problem and will try the result | One workflow, such as a shared task list, using sample data first; test whether it helps the intended user |
| Creator production dashboard | Tracking the planned original videos is the more immediate recurring problem | Track idea → script → production → review → release status; test it on the proposed content batch |

Before choosing, write a one-page problem statement with user, baseline, one core workflow, exclusions, acceptance checks, data sensitivity, and estimated time. Prefer the option with the clearest user feedback and smallest maintenance burden. Do not start both. Record the choice and rationale here after owner agreement; create a detailed project page only when scoped.

## Proposed 90-day experiment and decision gates

Months are relative to an **owner-agreed start date: TODO**, not calendar commitments. All criteria are proposed. Reduce targets or pause if the 5–7-hour weekly limit is exceeded.

| Stage | Proposed work | Evidence and gate |
| --- | --- | --- |
| Before day 1 — scope | Workshop usefulness and choose family organizer or creator dashboard; agree time/spending limits, data boundaries, and publication scope; review infrastructure dependencies | **Gate 0:** Owner agrees the problem and minimum trial. Synthetic-data local prototyping need not wait for server migration; real data or shared hosting needs a suitable access and recovery plan. |
| Month 1 — build | One small family-use web application as originally proposed; if the creator dashboard is chosen, explicitly record that substitution. In parallel, continue storage/backup work and aim for 6–8 original short videos | **Gate 1:** Demonstrate one usable workflow to its intended user, record feedback and effort, and review the content batch and production time. Releases only if authorized; distinguish drafts from published pieces. Record infrastructure progress separately, without implying storage changes or restore tests occurred. Continue only if workload and maintenance are sustainable; simplify or pause otherwise. |
| Month 2 — experiment | Improve the selected app from feedback; prototype one small-business spreadsheet/reporting workflow; aim for another 6–8 original videos and try more content formats | **Gate 2:** Show a feedback-driven improvement and a repeatable report with checked outputs and a manual-effort comparison. Record content observations and costs. If the combined workload exceeds capacity, defer the business prototype or extra formats rather than assume three parallel builds fit. |
| Month 3 — evaluate | Seek feedback on the reporting problem and willingness to pay; review app usefulness, content performance, costs, and maintenance | **Gate 3:** Record actual user feedback, repeat use, time saved, production effort, and available audience data. Distinguish interest from a paid commitment. Decide continue, narrow, pivot, or stop for each experiment. No revenue target, customer count, or commercial outcome is assumed. |

At each gate, record actual hours, costs, evidence, limitations, and the owner's decision. Learning and an informed stop are valid outcomes. Small audience samples do not establish product-market fit; lack of monetization does not erase technical or family value. A paid pilot, public launch, or additional spending needs a separate scope and explicit approval.

## Documentation and continuity

- Keep this page as the canonical overview; keep current priorities in [PROJECT-STATUS](../docs/PROJECT-STATUS.md), planning decisions in [DECISIONS](../docs/DECISIONS.md), and dated outcomes in [WORK-LOG](../docs/WORK-LOG.md). Link details rather than duplicate them.
- For a selected project, follow the [repository documentation workflow](../README.md#how-projects-are-documented): problem, requirements, constraints, options, architecture, implementation, validation, troubleshooting, tradeoffs, and lessons.
- Record milestones as planned, implemented, tested, or published only with dated evidence. Keep secrets, host IPs, private infrastructure details, family records, and customer data out of this repository and public content.
- After review and explicit commit/push authorization, verify the published main revision and synchronize working checkouts before refreshing ChatGPT sources. Never replace snapshots from an unpublished draft.
- Refresh uploaded copies of this roadmap, PROJECT-STATUS, DECISIONS, and WORK-LOG from that same main revision; refresh README or related roadmaps if uploaded. Record repository URL, source commit, and refresh date in the upload description or an accompanying source note. Label older planning responses as historical proposals so they do not compete with the canonical plan.
- Source refresh is manual and requires owner confirmation. Open a fresh Project conversation and check that it can identify the roadmap, proposed status, open first-project choice, and source revision. Missing or stale uploads do not change GitHub's authority.

## Immediate continuation

The owner intends to resume YAMS administration checks from Atlas after this documentation is recorded. Those checks are a separate activity, not performed or authorized for execution by this roadmap. Confirm the intended checks and Windows versus WSL/SSH context at that time; use the [current status](../docs/PROJECT-STATUS.md) and [YAMS repository](https://github.com/kkerns20/yams-media-server) for scope, evidence, and detailed troubleshooting.

## Open questions

- Which ideas solve a useful recurring problem, and which should be parked? Original response dates and formal Project Source titles: TODO.
- Which first app has the clearest recurring problem and willing test user: family organizer or creator dashboard?
- What are the start date, review cadence, minimum useful outcome, and spending ceiling?
- Which topic and audience should original videos serve, and which platforms/releases will be authorized?
- Should the first commercial experiment target small businesses or individuals/families? Which report and potential user are suitable? Reporting is the leading hypothesis, not a selected product.
- What data may each prototype use, where may it run, and what backup/access controls are required before real use?
- Which assistant inputs and second-brain sources merit later exploration? What should remain manual?
- At day 90, what evidence would justify continuing each workstream within the available time?
