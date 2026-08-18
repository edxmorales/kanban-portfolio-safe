# KPS — Kanban Portfolio with SAFe

**Version 1.10.0** · An open framework for teams that split people across several projects, technical debt, support, and improvements, with priorities that change every week.

> License: CC BY-SA 4.0 — you can use, adapt, and redistribute this framework, even commercially, as long as you give credit and keep any adaptations under the same license. See [`LICENSE`](./LICENSE).

> 🇪🇸 ¿Prefieres leerlo en español? Ver [`FRAMEWORK.md`](./FRAMEWORK.md).

## Table of contents

- [Executive summary](#executive-summary)
- [0. 360 Diagnostic: the mandatory starting point](#0-360-diagnostic-the-mandatory-starting-point)
  - [0.1 Relationship to the broader IT 360° transformation diagnostic](#01-relationship-to-the-broader-it-360-transformation-diagnostic)
- [1. The problem it solves](#1-the-problem-it-solves)
- [2. Foundations: why Kanban + SAFe](#2-foundations-why-kanban--safe)
- [3. The framework's pillars](#3-the-frameworks-pillars)
- [4. Original mechanics (what neither Kanban nor SAFe solve on their own)](#4-original-mechanics-what-neither-kanban-nor-safe-solve-on-their-own)
- [5. Roles and governance](#5-roles-and-governance)
  - [5.1 Escalation and disagreements between roles](#51-escalation-and-disagreements-between-roles)
- [6. How teams are managed](#6-how-teams-are-managed)
  - [6.1 When to use freelancers and when not to: project work vs. business-as-usual](#61-when-to-use-freelancers-and-when-not-to-project-work-vs-business-as-usual)
  - [6.2 Dependencies between value streams](#62-dependencies-between-value-streams)
  - [6.3 Onboarding: when someone new joins or rotates internally](#63-onboarding-when-someone-new-joins-or-rotates-internally)
  - [6.4 Cross-market initiatives with independent execution](#64-cross-market-initiatives-with-independent-execution)
- [7. How QA fits in without becoming a bottleneck](#7-how-qa-fits-in-without-becoming-a-bottleneck)
- [8. The infrastructure flow, end to end](#8-the-infrastructure-flow-end-to-end)
- [9. Measurement system](#9-measurement-system)
  - [9.1 Flow indicators (efficiency)](#91-flow-indicators-efficiency)
  - [9.2 Capacity and load indicators](#92-capacity-and-load-indicators)
  - [9.3 Interruption and cost indicators](#93-interruption-and-cost-indicators)
  - [9.4 Technical debt indicators](#94-technical-debt-indicators)
  - [9.5 Quality indicators](#95-quality-indicators)
  - [9.6 Predictability indicators](#96-predictability-indicators)
  - [9.7 Composite efficiency score](#97-composite-efficiency-score)
  - [9.8 Measurement cadence](#98-measurement-cadence)
  - [9.9 Indicators to validate the pilot](#99-indicators-to-validate-the-pilot)
  - [9.10 Lean lens: eliminating waste and cost, not just speed](#910-lean-lens-eliminating-waste-and-cost-not-just-speed)
- [10. Leveraging artificial intelligence](#10-leveraging-artificial-intelligence)
- [11. Implementation roadmap](#11-implementation-roadmap)
- [12. Budget and staffing: operating cost efficiency](#12-budget-and-staffing-operating-cost-efficiency)
  - [12.1 Two cost categories competing for the same budget](#121-two-cost-categories-competing-for-the-same-budget)
  - [12.2 Staffing cost: internal vs. freelance](#122-staffing-cost-internal-vs-freelance)
  - [12.3 Minimum operating budget categories to track](#123-minimum-operating-budget-categories-to-track)
  - [12.4 How budget connects to portfolio capacity](#124-how-budget-connects-to-portfolio-capacity)
  - [12.5 Cost efficiency indicators (extension of section 9)](#125-cost-efficiency-indicators-extension-of-section-9)
  - [12.6 Cadence](#126-cadence)
- [13. How this framework evolves](#13-how-this-framework-evolves)
- [Appendix: SAFe in depth](#appendix-safe-in-depth)
- [Appendix: glossary of acronyms and terms](#appendix-glossary-of-acronyms-and-terms)

---

## Executive summary

KPS deliberately combines two things: **Kanban** (continuous flow and work-in-progress limits, at both the team and individual level) and SAFe's **portfolio layer** (Lean Portfolio Management, Portfolio Kanban, and WSJF prioritization). On top of that, it adds its own mechanics to solve three problems neither Kanban nor SAFe solve on their own: critical knowledge concentrated in a few people, initiatives that quietly freeze whenever capacity gets pulled toward whatever's urgent, and the lack of clear authority over what actually counts as "urgent."

It isn't Scrum: Scrum assumes priority holds steady for an entire sprint, and here it can change from one day to the next. It isn't full SAFe either: SAFe is built for 50-125 people per Value Stream (Agile Release Train), a scale most teams that need this framework don't have and don't need.

**KPS is never applied directly to a project or initiative.** Before touching any work, teams run the [360 Diagnostic](#0-360-diagnostic-the-mandatory-starting-point) (Section 0) first — it's the framework's mandatory entry point, not an optional appendix. No board, limit, or role gets installed without that diagnostic in hand.

This document is meant to grow with real-world use. See [`CONTRIBUTING.md`](./CONTRIBUTING.md) to propose changes and [`CHANGELOG.md`](./CHANGELOG.md) for the version history.

---

## 0. 360 Diagnostic: the mandatory starting point

**No rule in this framework gets installed blind.** Before touching a board, setting a WIP limit, or naming a role, the team needs a 360-degree diagnostic of the portfolio's real state — not what people believe is happening, but what the data actually shows. Installing KPS without this diagnostic means guessing the configuration (what WIP limit, what Expedite threshold, how many value streams) instead of calibrating it with evidence.

The 360 Diagnostic reviews five angles, in this order:

**1. Real capacity per person, not per project.** For each active person, how many items they have in progress right now, no matter how many different initiatives that work is spread across. This surfaces where load is concentrating before it turns into a crisis.

**2. Real WIP compliance against the stated limit.** If a work-in-progress limit is already configured in the team's current tool, compare it against the actual number of active items. The gap between the limit and reality already tells you, on its own, how much control the system really has today.

**3. The state of every active initiative.** Which ones show recent movement, and which have gone days or weeks without a single item in progress — with nobody having formally decided that. An initiative that's "alive" on paper but frozen in practice is exactly the pattern KPS exists to prevent.

**4. The real state of pull requests and code flow.** How many PRs are open, how long they've been waiting for review, and whether several people are touching the same part of the system at the same time without coordinating.

**5. Real activity from the QA/automation team.** Whether the quality team has its own visible history of commits, PRs, or recent work — or whether its real capacity is absorbed into manual support the rest of the portfolio never sees.

**The result of this diagnostic isn't an opinion — it's an inventory with numbers.** How many people are carrying what percentage of active work, how many initiatives are effectively frozen, how long PRs have been sitting open, and whether QA capacity exists where it's supposed to. Those numbers are what later calibrate every piece of the framework — the WIP limit from pillar 2, the limit on simultaneous Expedite items, the capacity floor per initiative. Skip this step, and any number chosen is a guess, not a calibration.

See section 0.1 for how this diagnostic relates to a broader IT 360° diagnostic, and [application case 1](./docs/caso-aplicacion-01-diagnostico-seguridad.md) (Spanish) for a real example of that relationship.

Only after completing this diagnostic does the team move on to Step 1 of the [Implementation roadmap](#11-implementation-roadmap).

### 0.1 Relationship to the broader IT 360° transformation diagnostic

The 360 Diagnostic in this section is a specialized, narrower version of a broader methodology: the one a CIO would run when arriving at an organization, to assess the entire technology function before deciding anything. That methodology covers ten fronts — Listen, Infrastructure, Applications, Cybersecurity, Projects and Contracts, IT Processes, Budget, Human Talent, Digital Maturity, and Present and Prioritize. The table below details each one, along with how much of it KPS's own 360 Diagnostic covers (the five angles from the previous section):

| # | Front (full-scope IT 360° diagnostic) | What it reviews | Does KPS's 360 Diagnostic cover it? |
|---|---|---|---|
| 1 | Listen | Meeting with senior leadership, business leaders, key users, and the IT team, listening before drawing conclusions. | No — KPS assumes a mandate to install the framework already exists; it doesn't replace initial stakeholder interviews. |
| 2 | Infrastructure | Servers, networks, communications, data centers, cloud, continuity, and the state of technology assets. | Partial, indirectly — KPS doesn't diagnose infrastructure, but an infrastructure finding (e.g., a capacity ceiling with no autoscaling) enters KPS's prioritized backlog as soon as it's identified through some other means. See [application case 1](./docs/caso-aplicacion-01-diagnostico-seguridad.md) (Spanish). |
| 3 | Applications | Which systems generate value, which carry risk or duplication, or need to evolve. | Partial, indirectly — KPS doesn't assess which applications generate value or carry risk, but if the organization already has an internal inventory of business applications, services, in-house development, and operational tools, that inventory directly feeds how KPS groups value streams (pillar 5), the same way fronts 2 and 4 do. |
| 4 | Cybersecurity | Vulnerabilities, access, backups, continuity, incident management, and security maturity. | The diagnostic itself is out of scope — KPS doesn't audit vulnerabilities or security controls. But as [application case 1](./docs/caso-aplicacion-01-diagnostico-seguridad.md) (Spanish) shows, once that diagnostic has already happened through some other means, its findings get classified and prioritized directly with KPS's classes of service and WSJF. |
| 5 | Projects and Contracts | Strategic alignment, project status, active contracts, and operational, financial, and legal risks. | Partial — only the real status of initiatives (angle 3 of KPS's 360 Diagnostic); doesn't cover contracts or financial/legal risk. |
| 6 | IT Processes | Incident, change, problem, and asset management, continuity, service levels, and IT governance. | Partial — only workflow and PR flow (angles 2 and 4 of KPS's 360 Diagnostic); doesn't cover incidents, changes, or assets as a full ITSM discipline. |
| 7 | Budget | Current investment, how it's distributed, and the value each expense generates for the organization. | No, but related — KPS handles budget separately, in Section 12, not as part of the initial diagnostic. |
| 8 | Human Talent | Skills, strengths, gaps, and development opportunities across the team. | Partial — only real workload per person (angle 1 of KPS's 360 Diagnostic); doesn't cover skills, gaps, or development. |
| 9 | Digital Maturity | Level of digitization, automation, data use, innovation, digital culture, and strategic alignment. | Partial — only the automation and data-use slice covered by [Leveraging artificial intelligence](#10-leveraging-artificial-intelligence) (Section 10); doesn't cover innovation, digital culture, or strategic alignment as a full discipline. |
| 10 | Present and Prioritize | An executive report with evidence, indicators, risks, strengths, opportunities, and a prioritized roadmap. | Yes — the numbers-based inventory at the end of KPS's 360 Diagnostic serves the same purpose: it feeds directly into Step 0 of the roadmap. |

KPS doesn't try to cover all ten fronts — that would be a full IT management framework, not a workflow management one. As a diagnostic process, KPS only instantiates a specific slice of that methodology, mainly fronts 5, 6, and 8. Front 1 (Listen) is deliberately left entirely out of scope: KPS doesn't replace initial stakeholder interviews.

Fronts 2, 3, 4, and 9 are a different case. KPS doesn't diagnose them — it doesn't audit infrastructure, doesn't assess applications, doesn't evaluate vulnerabilities, doesn't measure digital maturity — but once that work already exists through some other means (an internal inventory, a security diagnostic like the one in [application case 1](./docs/caso-aplicacion-01-diagnostico-seguridad.md) (Spanish)), its results **plug directly into KPS's already-operating mechanics**: an inventory of applications or services feeds how value streams are grouped (pillar 5), infrastructure or security findings enter the prioritized backlog through WSJF and classes of service, and automation or data use enters through Section 10. The distinction matters: KPS doesn't replace those diagnostics, but it doesn't ignore them once they exist either.

**When to use which:** if the goal is to install KPS on a team or portfolio that already has a sponsor and a mandate, KPS's own 360 Diagnostic from the previous section is enough. If the goal is a full IT transformation — assessing an organization's entire technology function, not just how work flows within one team — KPS's five angles fall short by design, and the team needs to walk through all ten fronts before (or alongside) deciding whether KPS is even the right tool for the workflow layer.

---

## 1. The problem it solves

Priorities shift every week, new work keeps arriving, and the feeling stays the same: clear one backlog jam and another one shows up. Some initiatives move forward while others freeze without anyone formally deciding that. Pull requests pile up before every step toward production. Testing always seems to lag behind development.

This happens when four very different kinds of work — new projects, technical debt, support/incidents, and improvements — get mixed into the same team without explicit rules for how they compete for the same people's attention. It also happens when different initiatives share the same pool of people with no combined view of how much capacity each person actually has.

## 2. Foundations: why Kanban + SAFe

Kanban brings order to flow within a team: it visualizes work, limits how much can be in progress at once, and uses classes of service so not everything competes on equal footing. But Kanban has nothing to say about what happens when the same person is split across initiatives that can't see each other.

That's where SAFe's portfolio layer comes in: a single view of every initiative (Portfolio Kanban), a numbers-based prioritization logic (WSJF) instead of whoever argues loudest, and the principle of managing capacity by value stream instead of project by project (Lean Portfolio Management).

KPS takes exactly those two pieces and leaves out all the program-level ceremony and cross-Value-Stream coordination that SAFe adds for scales of hundreds of people. See [Appendix: SAFe in depth](#appendix-safe-in-depth) for the detail on competencies, configurations, and principles, and which parts of all that KPS decides not to adopt.

## 3. The framework's pillars

1. **One single capacity view, not one board per project.** Equivalent to SAFe's Portfolio Kanban: every initiative in a single view, so you can see how much each person is carrying regardless of which initiative each item belongs to.
2. **A work-in-progress limit per person, not just per team.** A team can look "within limit" while two people are carrying half the work. The real rule is an individual cap (1-2 active items): once someone hits it, the next item waits, gets reassigned, or someone consciously decides to pause something of their own.
3. **Classes of service with real behavior, prioritized with WSJF.** Expedite, Fixed Date, Standard, and Intangible, each with its own limit and ordering rules. What goes first is decided by cost of delay divided by job size, not by gut feeling.
4. **A capacity floor for every active initiative (Lean Portfolio Management).** No initiative that's still alive can silently drop to zero people. If capacity has to be diverted to an emergency, it comes out of a flexible pool reserved for exactly that.
5. **Value streams instead of isolated projects.** Initiatives are grouped by the business value they deliver, not by project name, so moving capacity within the same stream doesn't feel like abandoning something.
6. **A weekly ritual with one golden rule.** The weekly triage reorders what hasn't started yet. What's already in progress doesn't get touched, except for a real Expedite-class emergency — and that exception gets logged as an interruption.
7. **A short quarterly recalibration.** Half a day each quarter to adjust capacity floors and limits using the data that's accumulated — a scaled-down version of SAFe's PI Planning.

## 4. Original mechanics (what neither Kanban nor SAFe solve on their own)

- **Interruption cost measured in hours:** every Expedite-class interruption to work already in progress gets estimated and logged in a recurring report, so the cost of "urgent" stops being invisible.
- **Rotating on-call ("firefighter of the week"):** a rotating weekly role absorbs Expedite work, instead of it always falling on the same 1-2 people who know the most. Over time, this forces that knowledge to spread out.
- **A rising interest rate on technical debt:** every debt item accumulates a score that climbs week after week if it's left unaddressed, so competing against today's urgent work stops being a fight it's already lost.
- **Explicit authority to declare Expedite:** one named person, with a defined role, approves that classification. Without that approval, the item enters as Standard, no matter how urgent someone insists it is.
- **Radical visibility:** each person's workload and the status of every initiative are visible to the whole organization, not just to leadership. Social pressure holds the rules together better than any top-down audit ever could.

## 5. Roles and governance

KPS doesn't need a heavy role structure, but it does need every rule to have a named owner. Without that, rules get ignored under pressure — exactly the problem KPS exists to solve. It also needs that owner to never be a single point of failure, which is why every role in this table has a named backup too.

| Role | Responsibility | Authority | Backup |
|---|---|---|---|
| **Portfolio Flow Owner** | Keeps the single capacity view up to date and decides what happens when someone hits their WIP cap | Can pause, reassign, or reject a new item from entering for someone who's saturated | A second named person can make the same call if the primary is unavailable — without this, the role would carry the same bus factor risk the framework exists to remove from the rest of the team |
| **Class of Service Approver** | Evaluates and approves (or rejects) an item entering as Expedite | The only authority that can label something Expedite | Named backup with the same authority — this role is never uncovered, not even for a day, because urgent work doesn't wait for someone to come back from vacation |
| **Weekly Ritual Facilitator** | Runs the weekly triage, enforces the rule against touching work already in progress, and checks that no item enters development without meeting the Definition of Ready (section 7) | Can veto a reassignment that would break the protection rule for in-progress work, and can send any item that doesn't meet the Definition of Ready back to refinement | Any other facilitator trained in the ritual's protection rule can cover a given week |
| **Value Stream Lead** | Owns a grouping of initiatives by business value; negotiates capacity with the Portfolio Flow Owner; resolves the first level of disagreements within their stream (section 5.1) | Decides priorities within their own value stream, not across different streams | Named backup within the same value stream, with enough context to negotiate capacity without starting from scratch |
| **Business Value Representative** | Estimates and stands behind the Cost of Delay for initiatives in their stream, a direct input to WSJF; confirms that prioritization keeps reflecting what the business or customer actually needs | The only accepted source for WSJF's business-value component — without their estimate, an item gets prioritized with a guess, not with full WSJF | Named backup with direct visibility into the business or the customer, not just the technical backlog |
| **Rotating Firefighter** | Absorbs Expedite work during their week on duty | Can claim any Expedite item without going through the normal assignment queue | The weekly rotation is itself the backup mechanism — no one depends on a single person to handle what's urgent |
| **Flow Quality Owner** | Holds the WIP limit for the QA stage and automated test coverage | Can block an item from moving to "Ready to deploy" if it doesn't meet the Definition of Done | Named backup within the QA/automation team with the same authority to block |

None of these roles needs to be a full-time role or a new position on the org chart. They can (and usually do) work as hats that people on the team already wear — including the Business Value Representative, which in most cases already exists in the organization under another name (product owner, product manager, sponsor). The one non-negotiable thing is that who's wearing each hat, and who backs them up, stays explicit and visible to the whole team (the radical visibility pillar, section 4).

### 5.1 Escalation and disagreements between roles

No role structure fully prevents disagreement. What KPS needs is for disagreement to have a known path, instead of getting resolved by whoever pushes hardest or by informal hierarchy:

1. **Level 1 — within a single value stream** (e.g., the Class of Service Approver rejects an Expedite request someone keeps pushing for, or there's a dispute over a WSJF estimate). The Value Stream Lead for that initiative resolves it, using the authority already defined in the roles table.
2. **Level 2 — between a value stream and the portfolio view** (e.g., a capacity reassignment a Value Stream Lead won't accept, or a cross-stream dependency that doesn't line up — see section 6.2). This becomes an explicit agenda item in the weekly ritual; it doesn't get resolved outside it or through informal messages.
3. **Level 3 — a disagreement that didn't get resolved in the weekly ritual** (e.g., a strategic priority dispute between two value streams). It escalates to the quarterly recalibration and gets resolved using the measurement system's data (section 9) as evidence — never as just one more opinion among several.

**Closing rule:** while a disagreement is unresolved, the rule protecting work already in progress (pillar 6) stays fully intact. An unresolved disagreement is never an excuse to touch something already underway.

## 6. How teams are managed

KPS organizes people around **value streams**, not isolated projects with fixed teams. Front-end, back-end, full-stack, and QA roles all coexist within each value stream. The goal isn't for each person to belong exclusively to one stream forever — it's that their active load (WIP) never exceeds their individual cap, no matter how many streams that work comes from.

Teams that support every stream equally — QA automation, DevSecOps, platform — are treated as a **shared enabling pool**, not as one more project with its own isolated board. Their capacity enters the same single portfolio view as any value stream's, precisely so a support team doesn't vanish from the overall picture just because its work isn't reflected on any single project board.

When someone moves between value streams — something that will keep happening, and that's fine — that move gets logged in the single capacity view the same day, not at the end of the week. That way the Portfolio Flow Owner always knows, in real time, who has room and who doesn't.

### 6.1 When to use freelancers and when not to: project work vs. business-as-usual

Not all work should be staffed the same way. KPS explicitly distinguishes two natures of work to decide whether freelance/contract staff or permanent internal staff makes more sense:

**Project-type work (fits freelance).** Has a defined scope and delivery date, and once delivered, it's done — it gets executed, delivered, and the contract closes. It fits naturally with the Fixed Date and Standard classes of service. Examples: building a new module with already-defined requirements, a one-time migration, an integration with a specific vendor.

**Business-as-usual work (should stay internal).** Support, incidents, ongoing technical debt, and incremental improvements to a live system. This work needs continuity of knowledge and fast availability — it's exactly the kind of work where a freelancer who finishes their contract and leaves makes the bus factor worse instead of better, because the system's knowledge leaves with them.

**Criteria for deciding which bucket an initiative falls into:**

- Does it have a natural end date, after which no one needs to keep touching it? → freelance candidate.
- Does it need ongoing support after launch? → should stay with internal staff.
- Does it depend on tacit business knowledge that would take months to transfer? → internal staff.
- Is it part of the permanent "core" of a value stream, or a one-off initiative within it? → the permanent part stays internal; the one-off part can go freelance.

**Operating rules when freelance staff is used:**

- A freelancer's capacity enters the same single capacity view as the rest of the portfolio (pillar 1), explicitly flagged with their contract end date — so the Portfolio Flow Owner never builds a permanent dependency on someone who's leaving on a known date.
- Every freelancer delivers documentation of what they built as part of their Definition of Done, not as an optional afterthought — this is what keeps knowledge from walking out the door with the person (see also the AI leverage section for generating this documentation, in section 10).
- No Intangible-class item (technical debt) or Expedite-class item (security incidents) gets assigned to a freelancer without an explicit reason — by nature, both classes require continuity and deep system knowledge.

### 6.2 Dependencies between value streams

A value stream is almost never an island: sometimes an initiative in one stream needs something only another stream can deliver (an endpoint, a shared migration, a shared architecture decision). KPS doesn't adopt the program-level coordination SAFe uses between Agile Release Trains, because it assumes a scale this framework doesn't have — but it does need a lightweight rule so dependencies don't get discovered only after they've already blocked something.

- **Every dependency gets declared during refinement, not later.** It's part of the Definition of Ready (section 7): an item that depends on another value stream isn't "ready" until that dependency is written down and visible.
- **The dependency lives in the single capacity view (pillar 1),** flagged with the value stream it depends on — not just on the board of the stream that raised it.
- **A disagreement over a dependency between two Value Stream Leads** follows level 2 of the escalation path (section 5.1): it goes to the weekly ritual in front of the Portfolio Flow Owner, not resolved bilaterally and informally.
- **Tracking indicator (extends section 9.2):** the number of items blocked by a dependency on another stream, and how long they've been blocked. If this number keeps growing, it's evidence that value streams are grouped wrong (pillar 5) and should be redefined — not that people need more pressure.

### 6.3 Onboarding: when someone new joins or rotates internally

Section 6.1 already covers what happens when a freelancer's contract ends. This section covers the more common case: someone new joins the team, or someone internal rotates from one value stream to another — something section 6 already treats as normal and expected.

**When a new person (internal or freelance) joins a value stream:**

- From day one, they get a reduced WIP cap (half the team's standard) for their first few weeks, explicitly flagged in the single capacity view — not the same limit as someone who's already built up context.
- The Value Stream Lead informally designates, without creating a new role, someone from the stream as a point of context during that period.
- From day one, they get access to documentation generated through AI leverage (section 10) and to whatever an outgoing freelancer left behind (section 6.1) — knowledge that's already documented shouldn't depend on someone repeating it in person.

**When an internal person rotates from one value stream to another:**

- Before leaving their current stream, they document what only they know about the work in progress they're leaving behind — the same Definition of Done principle applied to freelancers in 6.1, extended here to internal rotation as well, not just to contract closures.
- The Concentration Index (9.2) gets reviewed before and after every rotation: moving the person who carries the most WIP without transferring their knowledge first doesn't fix the bus factor, it just moves it to another value stream.

### 6.4 Cross-market initiatives with independent execution

It's one thing for a value stream to depend on another (section 6.2), and a different thing for the same capability — the same initiative, the same build — to need deploying across several markets, segments, or clients that can move forward, get blocked, or finish without depending on each other. Treating this as a single aggregated card creates a concrete problem: the moment one market gets blocked, the whole card shows as "Blocked" even though the rest is already in production — hiding real progress and risking that the assigned person stays stuck on a stalled item instead of freeing up for the market that can actually move.

**Rule:** when a cross-market initiative has markets that can move independently through the workflow, each market is its own card in the single capacity view (pillar 1) — never one card that aggregates the status of all of them.

- **A shared base name identifies the family** (e.g., "Initiative — Market"), so the initiative doesn't lose its identity as a whole even though each market has its own card.
- **A blocked market never occupies the individual WIP cap (pillar 2) of the person assigned to another one.** If Market A gets blocked, that person is free to pick up Market B from the same family (or any other item within their value stream) while A's block gets resolved.
- **The criterion for deciding whether to split into per-market cards**, instead of leaving it as one: can the markets end up in a different state from each other at some point in the work (one certified and one not, one with its own local regulation, one with a different deadline)? If yes, split it. If the markets always move together, with the same team and the same date (built once, deployed to all of them at the same time), a single card is enough — its Size simply reflects that it covers several markets at once.
- **When to split, and when not yet:** while the initiative is still in validation (POC, proof of concept, internal pilot) and it hasn't been decided whether it will launch, or in which markets, it stays as a single card — splitting it before that decision would multiply rows over something that isn't even confirmed to exist yet. The split happens the moment the initiative moves from "being evaluated" to "approved and execution starts," because that's exactly when the markets can start diverging in status (one starts, another doesn't, one gets blocked). Before that point, the item lives in whatever class of service fits a POC (usually Intangible or Standard), not yet as a cross-market initiative.
- **The initiative as a whole is considered complete once all of its markets reach "Completed,"** not before — this gets checked by filtering on the base name in the single capacity view, with no need for an extra card to represent it.

**Tracking indicator (extends section 9.1):** % of markets at "Completed" out of the total target markets, per cross-market initiative — so the composite status score (9.7) doesn't get muddied by an isolated block in a single market while the rest of the initiative is moving along normally.

## 7. How QA fits in without becoming a bottleneck

The most common mistake is treating QA as a gate at the very end of the process, separate from the rest of the flow. In KPS, QA is just another stage on the same board, with its own work-in-progress limit — not a separate project with its own invisible backlog.

An item's flow, start to finish:

`Classified backlog → Refinement (acceptance and test criteria defined) → In development (WIP per person) → Code review / PR (WIP per reviewer) → QA (own WIP) → Ready to deploy → Production`

Three rules make this work without QA becoming the jam:

**First, QA enters at refinement, not at the end.** Acceptance criteria and test cases get defined before an item enters development, not after the code is already done. This is "shift-left": QA helps decide what "done" means from day one, instead of discovering at the end that a case wasn't covered.

**Second, QA capacity is part of the same portfolio view, not a separate project.** If the QA automation team runs its own backlog, separate from the rest of the work, its real load becomes invisible to whoever manages the portfolio — and it ends up absorbed into manual support with nobody noticing until automated tests stop moving forward.

**Third, nothing moves to "Ready to deploy" without meeting the Definition of Done, and that definition includes testing.** Minimum Definition of Done: code merged, automated tests passing, acceptance cases validated by QA, and a post-deployment monitoring plan where relevant. The Flow Quality Owner has the authority to block the move if any of this is missing — so the pressure of "it's almost ready" doesn't push something into production without it really going through QA.

**The Definition of Done has a counterpart at the start: a concrete Definition of Ready.** An item doesn't enter "In development" until it has, at minimum: written and verifiable acceptance criteria, test cases defined (not just mentioned) by QA, any dependency on another value stream explicitly declared (section 6.2), and a class of service already approved by the Class of Service Approver (section 5). The Weekly Ritual Facilitator has authority to send back to refinement any item that doesn't meet this — the same kind of authority the Flow Quality Owner uses to block production on the way out, but on the way in.

## 8. The infrastructure flow, end to end

The point of this section is that reaching production stops feeling like a surprise. Every stage has a concrete rule:

**Before coding: the "I'm touching this" signal.** Before creating a branch, the team announces which module or domain is about to change. This keeps several people from touching the same part of the system at the same time without knowing it until merge time.

**Branching strategy.** Short-lived branches (1-3 days max) or trunk-based development protected by feature flags. Never long-lived branches that accumulate changes and become hard to merge.

**Pull request policy.** A limit on open PRs per person (1-2, consistent with the WIP limit), at least one required reviewer, automated checks (build, unit tests, static security analysis) that must pass before a human reviews, and a recommended diff size (for example, under ~400 lines) so reviews stay fast and don't pile up.

**Continuous integration pipeline.** Build → unit tests → static/security analysis → automatic deploy to a test environment → QA validation (manual and automated) → approval → merge to the release branch.

**Environments and promotion.** Development → Test/QA → Staging (as close to production as possible) → Production, with explicit criteria for what's needed to move from one environment to the next. Never a "de facto" promotion just because time ran out.

**Feature flags to decouple merge from release.** Code can merge to the main branch without being active for users, which enables real continuous integration without waiting for the whole week's package to be ready at once.

**A rollback plan defined before deploying, never improvised during an incident.** Every deployment needs a clear way to be reverted (flip off the feature flag, redeploy the previous version) before it goes live, not once it's already failing.

**Post-deployment observation window.** A defined period after each deployment where the team actively watches error metrics and alerts before calling the deployment fully closed. This is the stage that removes the most "surprises" in production.

## 9. Measurement system

Guiding principle for this section: **what doesn't get measured doesn't improve, and doesn't get seen.** That's why no KPS indicator gets measured just once or left to whether someone happens to remember. All of them run on the same daily/weekly/monthly/quarterly cycle already defined throughout the framework, and all of them point at one goal: making the system's real efficiency visible, not just how busy people look.

### 9.1 Flow indicators (efficiency)

- **Lead time and cycle time, by class of service.** An Expedite item and a Standard item shouldn't be measured together: mixing their times hides whether the system actually prioritizes what it claims to prioritize.
- **Throughput:** items completed per week, per value stream.
- **Flow efficiency:** the time an item was actually being worked on, divided by the total time it spent in the system, expressed as a percentage. This is the central real-efficiency indicator: it almost always reveals that most of an item's time was spent waiting (in a code-review queue, waiting on QA) rather than being worked on — and it's the number that matters most to whoever asks "why does this take so long if nobody's sitting idle?"

### 9.2 Capacity and load indicators

- **% WIP compliance per person:** the share of days each person stayed within their individual cap, not over it.
- **Concentration Index:** what percentage of the portfolio's total WIP sits with the two people carrying the most load. This turns a pattern that would otherwise only be felt anecdotally into something objective — if two people are carrying 40% or more of active work, there's a real bus-factor risk, backed by a number instead of just an impression.
- **Capacity distribution across value streams**, compared against the agreed minimum floor for each.

### 9.3 Interruption and cost indicators

- **Simultaneously open Expedite items**, compared against the agreed limit.
- **Accumulated interruption cost**, in estimated hours.
- **% of interruptions that, reviewed afterward, actually deserved Expedite status.** This number lets the team calibrate, with evidence, whether the classification authority is being too permissive.

### 9.4 Technical debt indicators

- **Accumulated debt score**, and its trend over time (climbing, falling, flat?).
- **% of weekly capacity actually spent on technical debt**, compared against the agreed quota.

### 9.5 Quality indicators

- **Defects that escaped to production**, per period.
- **Automated test coverage**, and its trend.
- **% of items that bounce from QA back to development (rework).** A high number here usually signals that the shift-left from section 7 isn't really happening.

### 9.6 Predictability indicators

- **% of Fixed Date items delivered on time.**
- **Lead time variance:** a system can be fast on average and still unpredictable. This metric measures how reliable an estimated date is, not just how fast the average is.

### 9.7 Composite efficiency score

To have a single number that can be checked at a glance (green/yellow/red), it's recommended to combine four key indicators: Flow efficiency, % WIP compliance, Concentration Index, and % on-time Fixed Date delivery. No single indicator tells the whole story on its own. The composite score is what gets reviewed first in the weekly ritual, and each individual indicator is where you go dig in once the composite gets worse.

### 9.8 Measurement cadence

- **Daily:** silent capture of the base data (already handled through the PM/tracking-agent operation), no report unless there's an alert.
- **Weekly:** full dashboard refresh and review in the weekly ritual.
- **Monthly:** trend review and threshold recalibration (Expedite limit, how many freeze days count as an alert).
- **Quarterly:** full recalibration alongside the portfolio session from step 6 of the roadmap.

### 9.9 Indicators to validate the pilot

These are what turn "we think it got better" into real evidence:

| Indicator | Before the pilot | After the pilot | Control stream |
|---|---|---|---|
| Average lead time | | | |
| Flow efficiency (%) | | | |
| % WIP compliance | | | |
| Concentration Index | | | |
| Initiatives with 0 active items > 5 business days | | | |
| PRs open > 2 days | | | |
| % on-time delivery (Fixed Date) | | | |

This table, filled in with real data before and after, and compared against a value stream that didn't run KPS in parallel, is the concrete artifact that separates "proposed framework" from "methodology with evidence" — and it's exactly what gets documented as a case study for the framework's next version.

**Go/no-go decision criteria when closing the pilot:**

- **Expand to more value streams** if, compared against the control stream, at least three of the four composite-score indicators (9.7) improve consistently (across several weeks, not just one good week) and none get consistently worse.
- **Adjust and repeat the pilot in the same value stream** if only one or two indicators improve. Recalibrate the most likely parameters (WIP limit, Expedite threshold, value stream grouping) before trying to expand.
- **Document it as a negative learning in the CHANGELOG** if no indicator improves. A pilot not working in a specific context is valid information for the framework's next version, not a failure to hide.

### 9.10 Lean lens: eliminating waste and cost, not just speed

Measuring for the sake of measuring doesn't improve anything unless it connects to eliminating real waste. Every indicator in this section points at a concrete Lean waste:

| Lean waste | How it shows up here | Indicator that exposes it |
|---|---|---|
| Waiting | Items stuck in a code-review or QA queue | Low flow efficiency; age in those columns |
| Excess work in progress | More active items than the system can sustain | % WIP compliance |
| Rework/defects | Items bouncing from QA back to development | % rework; escaped defects |
| Overprocessing | Unnecessary ceremony or approval for simple work | Check whether cycle time for Standard items is disproportionate to their size |
| Knowledge not transferred | One person holds work nobody else can pick up | Concentration Index |
| Motion/handoffs | An item passes through hands or approvals that add no value | Count how many hands an item touches between Backlog and Production |

The underlying goal of the whole measurement system isn't "go faster" at any cost — it's to **expose where time and money are being lost without adding value**, so it can be eliminated with evidence. Real operational efficiency, not just the feeling of being busy.

## 10. Leveraging artificial intelligence

KPS is designed to lean on AI tools at the points where they cut the most waste and operating cost — not as a cosmetic add-on, but built into the mechanics already described:

- **Daily/weekly flow capture and reporting.** An AI assistant can read the team's daily updates (or a transcript of the standup) and keep the single capacity view current without anyone typing it twice, leaving the weekly report assembled automatically from that data.
- **Class-of-service suggestion.** When a new item comes in, an AI assistant can suggest whether it sounds like Expedite, Fixed Date, Standard, or Intangible based on its description. The Class of Service Approver still makes the call, just not from a blank page.
- **Support for WSJF estimation.** An AI assistant can propose a cost of delay and an estimated size based on similar historical items, giving prioritization an objective starting point instead of relying only on the estimator's gut feeling.
- **Documentation generation to reduce bus factor.** This connects directly to section 6.1: an AI assistant can help turn the tacit knowledge of the people who know the most (or of a freelancer before their contract ends) into real documentation, drawing from code, commits, and recorded explanations — cutting the knowledge-transfer cost that otherwise gets lost today.
- **QA support:** generating test cases and automated-test scaffolding from the acceptance criteria defined during refinement, easing pressure on the automation team without skipping the shift-left from section 7.
- **Efficiency alerts:** an AI assistant can continuously watch the indicators from section 9 and flag the moment one crosses its threshold (WIP exceeded, a frozen initiative, Expedite above the limit), instead of waiting for the weekly ritual to find out.

In every case, AI speeds up the execution of rules the framework has already defined. It never replaces whoever holds decision authority (Portfolio Flow Owner, Class of Service Approver, Flow Quality Owner). That distinction is what keeps "AI-leveraged" from turning into a black box nobody understands or can audit.

## 11. Implementation roadmap

0. **Complete the [360 Diagnostic](#0-360-diagnostic-the-mandatory-starting-point).** Skip this step and everything after it is blind configuration.
1. **Map the vocabulary.** Write down the SAFe equivalences so anyone who knows SAFe recognizes the logic.
2. **Write down, explicitly, what part of SAFe isn't being adopted.** No formal Agile Release Trains, no multi-day planning events.
3. **Install simplified-WSJF prioritization** instead of the informal weekly debate.
4. **Define the portfolio's value streams**, grouping initiatives by the business value they deliver.
5. **Name every governance role along with its backup** (section 5), and designate who holds the Business Value Representative role for each stream. Without this, step 3's WSJF has no one to supply the cost-of-delay number.
6. **Replace heavy planning** with a short quarterly recalibration slot.
7. **Install the framework's own mechanics:** rotating on-call, interruption cost, technical debt interest, classification authority, radical visibility.
8. **Run a scoped 4-6 week pilot** across two value streams, with the decision criteria from section 9.9 already agreed before starting. "What counts as success" doesn't get defined after seeing the results.

## 12. Budget and staffing: operating cost efficiency

No flow system is complete if it doesn't connect to what it actually costs to run. This section doesn't replace the organization's financial process — it states how budget and staffing connect to the capacity rules already defined elsewhere in the framework, so efficiency gets measured in cost as well as speed.

### 12.1 Two cost categories competing for the same budget

Whether anyone formally declares it or not, all of a team's capacity splits between two kinds of spend:

- **Keeping the business running (run the business):** support, incidents, corrective maintenance, and the technical-debt quota. It doesn't generate new value, but its absence generates loss — an unattended incident or an unpaid-down debt costs more later than it does now.
- **Changing the business (change the business):** new projects, improvements, and strategic initiatives. This is the spend that generates visible incremental value.

**Governance rule:** the percentage of capacity (and therefore of staffing budget) devoted to each category gets declared as an explicit number, reviewed during quarterly recalibration — not inferred after the money's already spent. The capacity floor per initiative (pillar 3) and the technical-debt quota (9.4/9.10) are how this rule already operates day to day; this section just makes it visible in budget terms too.

### 12.2 Staffing cost: internal vs. freelance

Building on the criteria from section 6.1, comparing internal vs. freelance cost isn't just about the hourly rate:

- **Fully loaded internal cost:** salary, benefits, and overhead. Stable capacity, also available for business-as-usual work and for tacit knowledge that can't be outsourced.
- **Freelance cost:** usually lower per billed hour, but with a hidden cost that has to be added explicitly: knowledge transfer at contract close (already required as a rule in 6.1) and the bus-factor risk if that transfer doesn't happen.

**Reference formula for an item's real cost:** the person's cost (internal or freelance) × actual time invested, **plus** the accumulated interruption cost if Expedite applied (already defined as an original mechanic), **plus** the knowledge-transfer cost if a freelancer did the work. Comparing freelance vs. internal by rate alone, without this third term, systematically underestimates the real cost of freelance work.

### 12.3 Minimum operating budget categories to track

- Internal staff (fully loaded cost).
- Freelance staff/contractors, with a visible contract end date (rule already defined in 6.1).
- Tools and licenses (board, CI/CD, monitoring).
- Environment infrastructure (test/staging/production).
- Incident and support cost, expressed in hours (9.3) and also in its monetary equivalent.
- A declared reserve for technical debt (weekly quota, 9.4).

### 12.4 How budget connects to portfolio capacity

The capacity floor per initiative (pillar 3) and the per-person WIP limit (pillar 2) are, in practice, how budget translates into real staffing. A new initiative isn't funded with "extra money" that has nowhere to land — it's funded with capacity currently sitting in a lower-WSJF initiative, or with new staffing (internal or freelance, per 6.1) that enters the single capacity view like anyone else.

**Governance rule:** no new initiative gets financially approved without first checking, using the 360 Diagnostic and the single capacity view, that a capacity floor is available or that capacity is being freed up from a lower-priority initiative.

### 12.5 Cost efficiency indicators (extension of section 9)

- % of total real capacity spent on running the business vs. changing the business, against what was declared.
- Cost per unit of throughput delivered (staffing cost weighted against throughput from section 9.1).
- Accumulated interruption cost (9.3) expressed in currency too, not just hours.
- % of staffing budget in freelance vs. internal, and its trend over time.

### 12.6 Cadence

Budget and staffing get reviewed in the same quarterly recalibration as pillar 7 (roadmap, step 5) — not as a separate financial process disconnected from the rest of the flow.

## 13. How this framework evolves

KPS uses semantic versioning (`MAJOR.MINOR.PATCH`): a `MAJOR` change alters a core pillar, `MINOR` adds a new mechanic or section without breaking what came before, and `PATCH` fixes or clarifies existing text. Every change gets logged in [`CHANGELOG.md`](./CHANGELOG.md).

Anyone using KPS can propose changes following the process in [`CONTRIBUTING.md`](./CONTRIBUTING.md). The explicit idea behind this framework is that it gets tested on more than one team and improves with that evidence — not that it stays frozen at its first version.

---

## Appendix: SAFe in depth

*Note: SAFe gets updated periodically (the most recent major version is SAFe 6.0). This section reflects its general, time-stable structure; before using it in external or formal material, it's worth confirming the current details at scaledagileframework.com.*

SAFe (Scaled Agile Framework) is the most widely used framework for scaling agile practices in large organizations, combining Lean, Agile, and systems-thinking principles across several layers: team, program, solution, and portfolio. KPS borrows only its portfolio layer; everything else is described here just as context.

**SAFe's seven core competencies:**

1. Team and technical agility.
2. Agile product delivery.
3. Enterprise solution delivery.
4. Lean Portfolio Management — the competency KPS borrows the most from.
5. Organizational agility.
6. Continuous learning culture.
7. Lean-Agile leadership.

**SAFe's four configurations:**

- Essential SAFe: a single Agile Release Train with several teams.
- Large Solution SAFe: multiple Agile Release Trains coordinated on a large solution.
- Portfolio SAFe: adds portfolio management to align strategy and investment — the configuration KPS draws its main inspiration from.
- Full SAFe: the complete combination for very large organizations.

**SAFe's ten Lean-Agile principles:**

1. Take an economic view of decisions.
2. Apply systems thinking.
3. Assume variability; preserve options.
4. Build incrementally with fast, integrated learning cycles.
5. Base milestones on objective evaluation of working systems.
6. Visualize and limit WIP, reduce batch sizes, and manage queue lengths.
7. Apply cadence, synchronize with cross-domain planning.
8. Unlock the intrinsic motivation of knowledge workers.
9. Decentralize decision-making.
10. Organize around value.

**Comparison with other scaling frameworks:**

| Framework | Approach | When it's usually preferred |
|---|---|---|
| **SAFe** | The most structured and prescriptive; adds program and portfolio layers | Large organizations governing investment and strategy across many teams |
| **Nexus** (Scrum.org) | A lightweight Scrum extension for 3-9 teams, with an integration team for cross-team dependencies | Moderate scaling, close to standard Scrum |
| **LeSS** (Large Scale Scrum) | Minimalist: a single Product Backlog and a single Product Owner for several teams | Organizations that prioritize simplicity |
| **Scrum@Scale** (Scrum Inc.) | A modular, "scale-free" architecture, with a network of Scrum-of-Scrums and an executive layer | Organic scaling without a monolithic framework |

KPS doesn't fully adopt any of the four: it takes SAFe's portfolio logic and combines it with team-level Kanban, leaving out the program layer that neither Nexus, LeSS, Scrum@Scale, nor full SAFe would solve any better for a team of this size.

## Appendix: glossary of acronyms and terms

**ART (Agile Release Train).** In SAFe, a group of 50 to 125 people organized around a shared value stream. Not adopted in KPS, since it's too large a scale.

**Backlog.** The full list of pending work, not yet prioritized.

**Bus factor.** How many people would have to "disappear" from the team for a piece of critical knowledge to be lost completely.

**Class of Service.** A category defining how a type of work behaves within the flow, with its own priority and limit rules.

**Cost of Delay.** An estimate of how much is lost for every week an item goes unaddressed. The numeric basis of WSJF.

**Technical debt.** Pending improvement or fix work postponed to deliver something faster.

**Definition of Done.** The list of conditions an item must meet before it's considered finished.

**Definition of Ready.** The conditions an item must meet before entering development (defined acceptance and test criteria).

**Expedite.** The most urgent class of service in Kanban: it can skip the normal queue, but its volume must stay limited.

**Value Stream.** A grouping of work by the end-to-end business value it delivers.

**Inspect & Adapt (I&A).** A SAFe event for reviewing and adjusting the process. In KPS, it's adapted as the weekly ritual.

**Kanban.** A visual work-management method based on continuous flow and work-in-progress limits.

**Lead time.** The total time from when an item enters the system until it's completed.

**Lean Portfolio Management (LPM).** SAFe's layer that decides how capacity and budget are split across initiatives or value streams.

**PI (Program Increment).** SAFe's 8-to-12-week planning cycle. In KPS, it's replaced by a short quarterly slot.

**PI Planning.** The planning event for a Program Increment. In KPS, a half-day session each quarter.

**Portfolio Kanban.** SAFe's board showing the status of every portfolio initiative in a single view.

**SAFe (Scaled Agile Framework).** A framework for scaling agile practices to large organizations.

**Scrum.** An agile framework based on fixed-length cycles (sprints).

**Shift-left.** The practice of moving quality activities (defining tests, reviewing security) earlier in the process, instead of leaving them for the end.

**WIP (Work In Progress).** The number of active items at a given moment. Limiting it is Kanban's central principle.

**WSJF (Weighted Shortest Job First).** SAFe's prioritization method: cost of delay divided by job size.
