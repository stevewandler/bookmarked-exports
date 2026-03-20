# Bookmarked Product Vision

*Canonical product vision document for the Bookmarked Operating System. This document provides capability-level detail sufficient for the CPO bot to generate epics and user stories, for the CMO to derive messaging, for the CRO to position in sales conversations, for engineering to make architecture decisions, and for all agents in the system to understand what we build, why, and what "done" looks like.*

**Last updated:** March 18, 2026
**Author:** Steve Wandler, Founder
**Status:** Active
**Upstream:** Bookmarked Vision Cascade (`bookmarked-vision-cascade-2026-03-18.md`)
**Downstream:** CPO (epics/stories), CMO (messaging), CRO (sales positioning), CCSO (onboarding/adoption), Engineering (architecture)

---

## Table of Contents

1. [Product Identity](#product-identity)
2. [Book Intelligence: The Engine](#book-intelligence-the-engine)
3. [The Intelligence Layer Architecture](#the-intelligence-layer-architecture)
4. [Product Capability Map](#product-capability-map)
5. [User Journeys](#user-journeys)
6. [Product Principles](#product-principles)
7. [The Compliance-to-Discovery Arc](#the-compliance-to-discovery-arc)
8. [Product Taxonomy & Naming](#product-taxonomy--naming)
9. [What Exists vs. What's Next vs. What's Future](#what-exists-vs-whats-next-vs-whats-future)
10. [Appendix: Data Fields & Intelligence Card](#appendix-data-fields--intelligence-card)

---

## Product Identity

### The Hierarchy

| Level | Name | What It Is |
|-------|------|-----------|
| **Company** | Bookmarked | The Book Intelligence Company. Parent brand. |
| **Product** | OnShelf | The platform districts log into. The software. |
| **Engine** | Book Intelligence | The intelligence layer that streams across the entire product. Not a module — it's the foundation underneath everything. |
| **Modules** | OnShelf Review, Classroom Libraries, Parent/Guardian Access, Collection Dashboard | Specific workflows within the OnShelf product. |
| **Future capabilities** | Content Scanner, Reader Intelligence Layer | Evolution of Book Intelligence and the product experience. |

### What OnShelf Is

OnShelf is the unified platform where school districts manage their entire book ecosystem — every library, every classroom, every book order, every compliance requirement, every stakeholder — in one place, powered by Book Intelligence.

Districts currently manage this with Excel spreadsheets, Google Forms, legacy ILS systems (Follett Destiny, Alexandria), PEN America ban lists, and manual processes stitched together with email. None of these tools talk to each other. The data is segregated. Nobody has a unified view of their compliance posture, their collection health, or their risk level.

OnShelf replaces all of that with a single platform where intelligence flows across every workflow.

### What OnShelf Is NOT

- Not a library catalog (we don't replace the ILS — we sit on top of it)
- Not a content filter or censor (we provide intelligence for informed decisions, not gatekeeping)
- Not a book retailer (we don't sell books — we help districts make better decisions about what to order)
- Not a reading app (students don't read books in OnShelf — we connect them to books)

---

## Book Intelligence: The Engine

### Definition

Book Intelligence is the AI-powered understanding of what's inside books, what's happening around books, and how to connect the right books to the right people — within regulatory, copyright, and ethical frameworks.

Book Intelligence is NOT a module or a tab in the product. It is the engine underneath every surface in OnShelf. When a librarian views their collection, Book Intelligence is what shows them the content ratings, flags, and challenge history. When an administrator reviews a book order, Book Intelligence is what powers the risk assessment. When a parent looks at their child's reading list, Book Intelligence is what provides the contextual transparency.

### What Book Intelligence Does (Concrete)

For every book in a district's collection or under consideration for purchase, Book Intelligence provides:

**Identity & Metadata:**
- Title, author, publisher, ISBN (edition-specific — not "a book called X" but THIS specific edition)
- Cover image, page count, publication year
- Synopsis from authoritative sources (ISBNDB, Open Library)
- Subject classifications, genre tags, theme tags

**Content Assessment:**
- Content ratings: Violence, Sexual Content, Language (None / Mild / Moderate / Explicit)
- Mature themes identification (e.g., Totalitarianism, Surveillance, Psychological Manipulation)
- Audience and reading level: Age range, grade level, reading level
- Grade level suitability: Elementary / Middle School / High School (Suitable / Not Suitable)
- Educational value assessment
- Content warnings (e.g., "Disturbing content; Psychological distress")
- Advisory context: Parental guidance recommendation

**Compliance & Risk:**
- Ban status: Has this book been banned anywhere? Where? When? By whom?
- Challenge status: Has this book been challenged? Where? Why? What was the resolution?
- Challenge risk level: Low / Medium / Flagged (NOTE: risk differentiation is being improved — see known issues)
- Potential concerns (e.g., "Disturbing themes of control and oppression")
- Regulatory alignment by jurisdiction (Texas SB 13, SB 412, and expanding)

**External Signals (Flags):**
- Categorized by source type: Library/Advocacy Organizations, News/Media Outlets, School/District Websites
- Each flag includes: date, category, description, source URL, state, district (where available)
- Continuous scanning — new flags surface automatically as they appear
- Source attribution: every piece of intelligence is traceable to its origin

**People & Characters:**
- Named characters in the book (for fiction)
- Subject identification (for non-fiction)

### What Book Intelligence Does NOT Do (Today)

- **Read the actual book.** Without publisher copyright access, we cannot analyze the text itself. All current intelligence comes from publicly available external sources.
- **Make decisions for districts.** Book Intelligence informs decisions. It does not approve, reject, or restrict books. Humans make the final call.
- **Provide legal advice.** We surface regulatory requirements and compliance data. We are not a law firm.
- **Rate or rank books.** We provide contextual intelligence. We do not create a rating system, which could be perceived as censorship.

### How Book Intelligence Differs from ChatGPT

Districts increasingly use ChatGPT to look up books. This is dangerous because:

| Dimension | ChatGPT | Book Intelligence |
|-----------|---------|-------------------|
| **Consistency** | Different answer every time, different between users | One system, one answer, for the entire district |
| **Source attribution** | No sources cited, may hallucinate | Every data point traceable to its source |
| **ISBN fidelity** | Answers about "a book called X" generically | Tied to the exact ISBN/edition |
| **Defensibility** | Screenshot of a chat conversation | Documented, auditable process in a system of record |
| **Collaboration** | Individual tool, no shared state | One platform for the entire district — librarians, administrators, board members, parents |
| **Institutional memory** | Gone when the chat closes | Persists across staff changes, year over year |
| **Continuous monitoring** | Point-in-time query | Proactive scanning — new flags surface automatically |
| **Workflow integration** | Separate research step | Intelligence embedded at point of decision |

---

## The Intelligence Layer Architecture

Book Intelligence operates across three layers, each building on the last. This is the technical and strategic roadmap for how intelligence deepens over time.

### Layer 1 — External Signals (LIVE TODAY)

**What it is:** Publicly available intelligence about books gathered from across the internet.

**Sources:**
- Challenge and ban lists (PEN America, state-level lists, district-level actions)
- News coverage and media mentions
- School board meeting minutes and actions
- Professional book reviews (Kirkus, School Library Journal, Booklist, Publishers Weekly)
- Library/advocacy organization publications (ALA, state library associations)
- Legislative tracking (bill text, committee actions, enforcement guidance)
- Open metadata databases (ISBNDB, Open Library, Library of Congress)

**What districts see:** The Book Intelligence card on every book — content ratings, flags, challenge history, audience assessment, educational value, and advisory context. All sourced, all traceable, all continuously updated.

**How it works:**
1. District uploads their book collection (ISBN list or ILS export)
2. Bookmarked enriches every book with intelligence from external sources
3. Proactive scanning continues — new flags surface automatically when external sources mention a book in the collection
4. Intelligence appears everywhere: library view, order review, classroom library view, parent portal

**The PEN America problem (and why Layer 1 matters):**
PEN America tracks bans and challenges but not resolutions. If a district removes a book for review and returns it to the shelf after committee review, PEN America still marks it "banned." Districts see the ban list and refuse to order anything on it — avoiding scrutiny rather than doing due diligence. Result: de facto censorship from incomplete data. Bookmarked's Layer 1 captures more context than any single source, and Layer 2 (Network Intelligence) will eventually track outcomes — creating the case law that doesn't exist anywhere today.

**Limitations:** Cannot assess content directly. Relies on what others have said about the book, which may be incomplete, biased, or outdated. The 98% "Medium" risk classification problem (March 2026) demonstrates this: without direct content access, differentiating risk levels is difficult.

### Layer 2 — Network Intelligence (BUILDING NOW)

**What it is:** Intelligence generated by the Bookmarked network itself — the decisions, patterns, and outcomes across all districts using the platform.

**What the network learns:**
- **Challenge velocity:** Which titles are being reviewed across districts right now? A spike in review activity signals emerging issues before they become crises.
- **Placement patterns:** Where are books being shelved — school library, classroom library, restricted section? How do similar districts handle the same title?
- **Decision benchmarking:** What did districts like yours decide about this book? Districts see how peer communities — similar size, demographics, values — handled specific titles.
- **Collection composition:** What's actually in school libraries and classrooms across the network? Patterns reveal gaps, risks, and opportunities districts didn't know they had.
- **Review outcomes:** When a book goes through committee review, what was the result? Approved, restricted, removed? This outcome data compounds into predictive intelligence.
- **Ordering patterns:** What are districts like yours ordering? What's working? What books are showing up in similar-profile districts that aren't in your collection?

**What districts see:** Contextual benchmarks embedded in the intelligence card — "73% of similar districts retained this title after review," "This book appears in 89% of high school libraries in your ESC region," "12 districts reviewed this book in the last 30 days."

**Privacy architecture:** Individual district data stays private. The network sees aggregated patterns and anonymized benchmarks. Districts get collective intelligence without exposing their specific decisions or collections.

**Why this is defensible:** The network effect creates a moat that deepens with every district added. A new entrant would need to rebuild this dataset from scratch — years of decisions, patterns, and outcomes across hundreds of districts. By the time they start, Bookmarked is further ahead.

**Current state:** Data collection infrastructure is being built. As V2 districts use the platform — making decisions, processing orders, reviewing challenges — this data accumulates. The intelligence surfaces will follow.

### Layer 3 — Publisher Content / Content Scanner (FUTURE — targeting next school year)

**What it is:** Source-verified intelligence from reading actual book content. The Content Scanner — AI-powered analysis of what's actually inside the book.

**What it enables:**
- Definitive content assessment (not "this book was challenged for sexual content" but "here is exactly what content appears and where")
- Regulatory compliance verification against specific statutes (reading the book against the text of SB 13, SB 412, etc.)
- Personalized book previews for every reader — "here's why YOU would or wouldn't want to read this" — without revealing copyrighted text
- Student-book matching based on actual content, reading level, interests, and regulatory context
- Collection gap analysis based on content diversity, not just metadata
- Protection against both wrongful censorship (book removed for bias, not legal grounds) and wrongful access (content that genuinely violates statute)

**How it works:**
1. Publishers grant Bookmarked access to read their books within a secure, copyright-protected environment
2. AI reads and analyzes the content against regulatory frameworks, educational standards, and reader profiles
3. Intelligence flows into the platform — deeper content assessment, definitive compliance answers, personalized matching
4. The publisher benefits: a direct, intelligent channel to institutional buyers, with analytics on what's being ordered and why

**Why publishers will participate:**
- Baker & Taylor's shutdown (66-75% of distribution market) has created a vacuum — publishers need new channels to reach institutional buyers
- Current distributors take 40-55% — Bookmarked's model offers better intelligence at lower cost
- Publishers currently print one message on the back of every book for a million readers. Content Scanner enables a unique, personalized preview for every reader — better marketing without copyright compromise.
- Data: publishers get visibility into what districts actually want, need, and order — intelligence that currently doesn't exist

**Current state:** Architecture being designed. Targeting initial capability by 2026-2027 school year. Requires publisher partnerships, copyright access agreements, secure reading infrastructure, and regulatory framework mapping.

---

## Product Capability Map

### Module 1: Collection Dashboard (Home)

**What it does:**
- Unified view of the district's entire book ecosystem in one screen
- Total libraries count (school + classroom)
- Book counts by location (school library vs. classroom libraries)
- Flagged book count and breakdown (school library vs. classroom)
- Access status distribution (Approved / Pending / Limited / Don't Show)
- Classroom library drill-down (see each classroom, its book count, flag status)
- Order alerts (overdue reviews, pending actions)
- Top readers (student activity, books read, last activity, status)
- Weekly overview (orders created, books approved, books rejected)
- CORE dashboard statistics (lists created, lists awaiting review, lists approved, total books this month)

**Who uses it:**
- **Librarians:** Daily check-in. "What needs my attention today?" See flagged books, overdue orders, student activity.
- **Administrators / Directors of Library Services:** District-wide compliance posture. "Are we in good shape?" See total flags, classroom library blind spots, pending reviews.
- **Superintendents:** Executive view. "What's our risk level?" High-level numbers they can report to the board.

**What "great" looks like:**
- A librarian opens the dashboard Monday morning and immediately knows: 3 new flags on books in the collection, 2 orders overdue for review, a classroom library in Social Studies Grade 2 with all books flagged. She knows exactly where to spend her time.
- A superintendent opens the dashboard before a board meeting and can say: "We have 267 libraries under management, 254 flagged books under review, and 45 books approved this week. We are in compliance."

**Current state:** Live in V2. Dashboard exists with the data described above.

**Book Intelligence connection:** The flagged book counts, risk levels, and alert triggers all come from Book Intelligence. The dashboard is a visualization of intelligence, not just inventory.

### Module 2: Library Management (Library Tab)

**What it does:**
- Browse and manage the school's book collection
- Visual book grid with cover images, title, author, location tag, review status, genre/subject tags, ISBN
- Search by title, author, ISBN, barcode, or tags
- Filter and sort capabilities
- Individual book detail view: full Book Intelligence card (see Appendix)
- Set book status (Approved, Limited, Don't Show, Pending Review)
- Refresh metadata on demand
- View Guardian Activities (parent/guardian interactions with this book)
- View Status History (audit trail of all status changes)
- View Circulation History (checkout/return data)
- Notes and Documents (attach documentation to any book)

**Who uses it:**
- **Librarians:** Primary daily workspace. Review flagged books, update statuses, research books using intelligence cards.
- **Teachers:** View books in their classroom library (same UI, scoped to their classroom).
- **Administrators:** Spot-check specific books, review books that have been flagged or challenged.

**What "great" looks like:**
- A librarian gets an alert that "The Perks of Being a Wallflower" has a new flag. She clicks through to the intelligence card. She sees: Bans: 2, Challenges: 1. She expands the ban details — Madison ISD removed it for explicit sexual references; Polk County removed it for sexual activities and homosexuality. She sees the Challenge Details — Denver Public Schools challenged it for sexual references and LGBTQ+ content. She checks the content ratings: no sexual content flagged in the AI assessment. She looks at grade level suitability: suitable for Middle School and High School, not suitable for Elementary. She's now equipped to make an informed decision in minutes, not hours of research.

**Current state:** Live in V2. The book detail view with full intelligence card is the core experience.

**Book Intelligence connection:** This IS where Book Intelligence lives most visibly. Every book detail page is an intelligence card. The intelligence isn't a separate tool — it's embedded in the library experience.

### Module 3: OnShelf Review (Orders Tab)

**What it does:**
- Full book order workflow replacing Excel spreadsheets and manual processes
- Three-stage pipeline: "Books to Order" → "Books to Review for Order" → "Book Orders"
- Teachers and staff create order lists (e.g., "Ms. Audrey's English 9," "Mr. Thompson's History")
- Each book in an order list shows: cover, title, author, publisher, ISBN, age range, ban count, challenge count, summary, themes, notes, copy count
- Ban and challenge details expandable inline (which district, which school, why, when, source link)
- Notes per book (reviewers add context, concerns, or recommendations)
- Submit list for review → Review and approve/reject → Finalize order
- Push approved order to public URL for 30-day parent comment period (SB 13 requirement)
- Parent feedback collected in-platform (replacing Google Forms)
- Route to board for final approval (SB 13 requirement)
- Complete audit trail at every stage

**Who uses it:**
- **Teachers:** Submit book order requests with justification
- **Librarians:** Curate and review submitted orders, check against Book Intelligence, manage the pipeline
- **SLAC Committee members:** Review books before parent exposure (if district elects to have SLAC committee)
- **Parents/Community:** Comment on proposed orders during 30-day review period
- **Board members:** Final approval of book orders

**What "great" looks like:**
- A teacher submits 15 books for her English 9 class. The librarian opens the list and immediately sees that 3 books have been banned in other districts and 2 have active challenges. She clicks into the ban details for "The Perks of Being a Wallflower" — Madison ISD and Polk County both removed it. She reads the reasons, checks the content assessment, adds a note: "Reviewed ban details — bans were for LGBTQ themes, not sexually explicit content per our policy definition. Recommend for high school, not middle school." She submits the list for SLAC review. The entire process — which used to take days of manual research — takes 30 minutes.

**Current state:** Live in V2. The Lovable prototype shows the order pipeline and book detail view with inline intelligence. The public URL for parent review and board approval workflow are in V2.

**Book Intelligence connection:** Every book in an order list is enriched with intelligence. The librarian doesn't leave the order workflow to research a book — the intelligence is right there, inline, at the point of decision.

### Module 4: Classroom Libraries (Classrooms Tab)

**What it does:**
- Unified visibility across all classroom libraries in a school
- Each classroom is a distinct sub-library with its own book collection
- Teachers manage their classroom library using the same UI as the main library
- Administrators see all classrooms and their contents from one view
- Cross-reference: "This book is already in Classroom 204 — do we need it in the school library too?"
- Flag visibility: "Social Studies Grade 2 has 49 books, ALL flagged"
- Same Book Intelligence applied to classroom books as school library books

**Who uses it:**
- **Teachers:** Manage their own classroom library. See what they have, add books (with approval workflow), remove books.
- **Librarians:** See the full picture — school library plus all classroom libraries. Identify duplicates, gaps, risks.
- **Administrators / Superintendents:** The "black hole" made visible. For the first time, see what's actually in classroom libraries across the district.

**What "great" looks like:**
- A superintendent has never known what books are in the 266 classroom libraries across the district. She opens OnShelf and sees: 234 classroom books across 266 classrooms, 201 flagged. She can drill into any classroom, see every book, see the intelligence on each. She discovers that a Social Studies classroom has books that are grade-inappropriate based on content assessment. She routes them for review. Before OnShelf, she had no visibility and carried criminal liability (SB 412) for content she didn't even know existed.

**Current state:** Live in V2. Classroom library management is functional. Teachers can access their classroom. Administrators can see all classrooms.

**Book Intelligence connection:** Same intelligence engine, different surface. Classroom books get the same intelligence card, same flags, same content assessment as school library books.

### Module 5: Parent/Guardian Access

**What it does:**
- Parents see what books their children have checked out
- Parents can restrict specific books they don't want their child to access (SB 13 requirement)
- Guardian Activities tracked on each book (which parents interacted, what actions taken)
- Public order review: parents can view and comment on proposed book orders during 30-day window

**Who uses it:**
- **Parents:** View their child's reading. Restrict access to specific titles. Comment on proposed book orders.
- **Librarians:** See parent restrictions and feedback. Understand community sentiment.
- **Administrators:** Demonstrate compliance with SB 13 parent access requirements.

**What "great" looks like:**
- A parent receives a notification that new books are being proposed for their child's school library. They click the link, see the list with Book Intelligence summaries, and can comment: "I'd like more information about why this book is appropriate for 6th graders." The librarian sees the comment in-platform and responds with the intelligence data. The parent feels heard. The district has documentation. No Google Forms. No email chains.

**Current state:** Partially live in V2. Parent restriction capability exists. Public URL for order review is in V2. Comment collection is functional.

**Book Intelligence connection:** Parents see a simplified version of the intelligence card — enough to make informed decisions about their child's access without overwhelming them with professional-level detail.

### Module 6: Reports

**What it does:**
- Compliance reporting for board presentations
- Collection health metrics
- Order activity summaries
- Flag and challenge history tracking
- Student engagement data (where circulation data is available)

**Who uses it:**
- **Librarians:** Generate reports for administrators and board
- **Administrators:** Board-ready compliance documentation
- **Superintendents:** Executive summaries for governance

**Current state:** Basic reporting in V2. Deep analytics is a growth area.

---

## User Journeys

### The Librarian (Primary User)

**Context:** Manages one school library and oversees classroom libraries. Responsible for collection development, book ordering, and responding to challenges. Stretched thin — may also teach, manage a media center, or serve multiple schools.

**Monday morning with OnShelf:**
1. Opens dashboard. Sees 3 new flags overnight on books in the collection, 2 order lists awaiting review, 1 order overdue.
2. Clicks into the flagged books first — a book in the 5th grade classroom library was mentioned in a news article about a challenge in another district. Reviews the intelligence card. Content assessment shows: suitable for middle school and high school, not elementary. This book is in an elementary classroom. Routes it for administrator review with a note.
3. Opens the order lists. A teacher submitted 12 books. Reviews them against Book Intelligence — 10 are clean, 1 has a challenge history (reviews the details, decides it's fine for high school), 1 has explicit content concerns. Adds a note rejecting that one with the intelligence data as evidence.
4. Checks the overdue order — it's been in parent review for 35 days. The 30-day window has closed. Moves it to board approval stage.

**Total time:** 45 minutes of informed, documented decision-making. Previously: days of manual research, or decisions made without data.

### The Superintendent / Director of Library Services

**Context:** Responsible for the district's compliance posture across all schools. Reports to the board. Carries personal liability under SB 412. Needs to demonstrate that the district has a defensible process.

**Board meeting prep with OnShelf:**
1. Opens dashboard. Sees district-wide numbers: 267 libraries under management, 55 school library books, 234 classroom books, 254 flagged books total.
2. Reviews access status: 2 approved, 52 pending review, 1 limited, 0 "Don't Show." Notes that 52 pending is too many — flags this for the librarian team.
3. Generates a compliance report showing: all books in the system, flagged books and their status, completed reviews this month (45 approved, 3 rejected), parent feedback received and addressed.
4. Goes to the board with documentation, not anecdotes. "We are managing 267 libraries. We have reviewed 48 books this month. 3 books were removed. Here is the documentation for each removal. We are in compliance."

**What this replaces:** Previously, the superintendent had no visibility into classroom libraries, no unified compliance view, and no documentation trail. Board presentations were based on librarian assurances, not data.

### The Parent

**Context:** Wants to know what their child has access to. May have concerns about specific content. Wants to be heard, not dismissed.

**Experience with OnShelf:**
1. Receives notification: "New books proposed for Eastwood Elementary school library."
2. Clicks link. Sees 15 proposed books with cover images, summaries, age ranges, and theme tags.
3. Notices a book tagged "Coming of Age" and "LGBTQ+ Themes." Reviews the summary. Decides she'd like to restrict her child's access to this title specifically.
4. Submits restriction through the parent portal. The librarian is notified. The restriction is documented. The book remains available to other students.
5. Later, she checks her child's reading history. Sees they've checked out 6 books this semester. Feels connected to her child's reading life.

**What this replaces:** Showing up at a board meeting angry because they didn't know what was in the library. Google Forms with no follow-up. Feeling unheard.

---

## Product Principles

These principles guide what we build, what we don't build, and how we make trade-off decisions.

### 1. Intelligence at the Point of Decision
Book Intelligence should appear where decisions happen — not as a separate research step. When a librarian reviews an order, intelligence is inline. When a parent views a book, intelligence is inline. Never make someone leave their workflow to access intelligence.

### 2. Informed Choice, Not Gatekeeping
We provide intelligence that enables informed human decisions. We never make the decision for the district. We never restrict, approve, or remove a book. We equip people with data and let them decide. This is critical for positioning: Bookmarked is not a censor.

### 3. Agnostic Platform
No commercial bias (we don't sell books). No personal bias (we don't curate based on opinion). No political bias (we serve districts regardless of political direction — both "restrict" and "protect" legislation creates demand). Intelligence is sourced, traceable, and objective.

### 4. Defensibility by Design
Every action creates an audit trail. Every decision is documented. When a book is challenged, the district has a record of their process, the evidence they considered, and the rationale for their decision. This isn't a feature — it's the architectural principle.

### 5. Unified, Not Fragmented
All data in one place. School library, classroom libraries, orders, parent feedback, board approvals, intelligence — all connected. No more Excel spreadsheets, Google Forms, and email threads stitched together. The value of the platform is the connections between data, not just the data itself.

### 6. Protect Both Directions
We protect against books that shouldn't be in a school (regulatory compliance). We also protect books that SHOULD be there — identifying removals driven by opinion or bias rather than legitimate regulatory grounds. The platform cuts both ways: keeping inappropriate content from kids AND keeping appropriate content from being wrongfully censored.

### 7. Give Time Back, Don't Add Work
Districts are understaffed and over-regulated. Every feature should reduce the time required to make good decisions, not increase it. If a feature adds work, it fails the test. The goal: a librarian does in 45 minutes what used to take days.

### 8. Data-Backed Decisions Replace Bias
Librarians choosing 10,000 books from 40+ million is a data problem, not a human judgment call. Publishers recommending their own books is commercial bias. PEN America marking books "banned" without tracking resolutions is institutional bias. Bookmarked replaces bias with data at every level.

### 9. Build the Network, Not Just the Tool
Every district that uses OnShelf contributes to intelligence that makes the system smarter for everyone. Design features that create network data (challenge outcomes, placement patterns, ordering decisions) alongside features that consume it.

### 10. Copyright is Sacred
We never compromise, expose, or diminish the publisher's IP. We build intelligence about and around books. When we have publisher access (Content Scanner), we create derivative intelligence, not derivative content. The book itself is never reproduced, summarized to the point of replacement, or given away.

---

## The Compliance-to-Discovery Arc

Bookmarked's product evolves through a deliberate arc. Compliance is the entry point, not the destination. Each stage builds on the last, and the data generated in earlier stages powers later ones.

### Stage 1: Compliance (WHERE WE ARE)
**Entry point.** Districts have an immediate, urgent, legally mandated need.
- "We must comply with SB 13 or face consequences."
- Product: Upload your collection, see your flags, manage your orders through the required process, document everything.
- Value: You're in compliance. You have the documentation. You can sleep at night.
- Data generated: Book collections, review decisions, order patterns, parent feedback.

### Stage 2: Visibility (EMERGING)
**The "aha" moment.** Districts see things they couldn't see before.
- "I didn't know what was in our classroom libraries. I didn't know 40% of our books haven't been checked out in 3 years."
- Product: Classroom library visibility, collection health metrics, dead inventory identification.
- Value: For the first time, the superintendent sees the entire district's book ecosystem. Decisions are data-informed.
- Data generated: Collection composition, usage patterns, cross-location insights.

### Stage 3: Optimization (NEXT)
**The shift from reactive to proactive.**
- "Based on our students, our gaps, and our budget — what should we order next?"
- Product: Collection gap analysis, student-informed recommendations, budget optimization, peer benchmarking.
- Value: Districts build better libraries with the budget they have. Dead inventory is replaced with books students actually want.
- Data generated: Recommendation effectiveness, student engagement changes, collection evolution.

### Stage 4: Intelligence Network (BUILDING)
**The moat deepens.**
- "What are districts like us doing? What's working? What should we watch out for?"
- Product: Network benchmarks, predictive challenge alerts, peer decision data, the "case law" repository.
- Value: Districts make decisions with the collective wisdom of the entire network. An emerging challenge in one state triggers proactive alerts in similar districts.
- Data generated: Cross-district patterns, predictive models, outcome tracking.

### Stage 5: Discovery (FUTURE)
**The vision realized — for school districts.**
- "Every student in our district is matched to books they'll love, within our regulatory framework."
- Product: Student-book matching, personalized reading paths, Content Scanner intelligence, collection curation recommendations based on actual students.
- Value: Libraries thrive. Literacy improves. Students find the next book that changes their life. Librarians spend time on relationships, not compliance paperwork.
- Data generated: Reading outcomes, discovery effectiveness, the richest student-book interaction dataset in K-12.

---

## Product Taxonomy & Naming

Current naming needs refinement. Here is the reality mapping and areas for alignment:

| Current Name | What It Actually Is | User-Facing Location | Notes |
|---|---|---|---|
| OnShelf | The product | Login screen, top nav | Established. Keep. |
| Book Intelligence | The engine across everything | Left nav on book detail pages | Users see it as a tab/section, not as the underlying engine. May need to make the concept more visible. |
| OnShelf Review | Book order + review workflow | Orders tab | Name doesn't immediately convey "orders." Consider whether "OnShelf Review" works for the user or if "Orders" is clearer. |
| Classroom Libraries | Classroom management module | Classrooms tab | Clear and intuitive. |
| Book Intelligence Shield | Marketing concept | Not user-facing | Not a separate module. It's the concept of BI proactively protecting. May be useful for sales/marketing, not product UI. |
| Content Scanner | Future capability | Not yet in product | Clear name. Conveys what it does. |
| Reader Intelligence Layer | Future capability | Not yet in product | May need a more user-friendly name when it ships. |
| OnShelf Engage | Parent/community layer | Not yet branded in UI | Exists functionally (parent access, public review URL). Needs formal identity. |
| Guardian Activities | Parent interaction tracking | Left nav on book detail | Current term in UI. |

**Recommendation for product vision purposes:** Use functional descriptions (what it does) alongside brand names. The CPO bot should think in terms of capabilities, not just names. Names can evolve; capabilities are stable.

---

## What Exists vs. What's Next vs. What's Future

### LIVE (V2 — Today)

| Capability | Status | Notes |
|---|---|---|
| Book collection upload and management | Live | ISBN-based, edition-specific |
| Book Intelligence cards (Layer 1) | Live | External signals — content ratings, flags, challenge data, audience assessment |
| Collection dashboard | Live | Unified view with key metrics |
| Book order workflow (OnShelf Review) | Live | Multi-stage pipeline with intelligence inline |
| SB 13 compliance workflow | Live | Committee review, parent URL, board approval |
| Classroom library management | Live | Teachers manage; admins see all |
| Parent book restriction | Live | SB 13 requirement |
| Parent order review (public URL) | Live | 30-day comment period |
| Audit trail | Live | Every action documented |
| Status management | Live | Approved / Limited / Don't Show / Pending |
| Flag categorization | Live | Library/Advocacy, News/Media, School/District sources |
| Multi-language support | Live | EN language selector visible in nav |

### BUILDING (Near-term)

| Capability | Target | Notes |
|---|---|---|
| Risk level differentiation | In progress | Current 98% Medium classification needs improvement. Engineering working on better risk assignment logic. |
| Network Intelligence surfaces | Next | Peer benchmarks, challenge velocity, placement patterns |
| Enhanced reporting | Next | Board-ready compliance reports, collection health analytics |
| Content Scanner architecture | 2026-2027 school year | Publisher partnership required |
| Student data integration | In progress | Top Readers visible on dashboard; deeper integration planned |
| Circulation analytics | In progress | Checkout/return data visible on book detail; analytics layer coming |

### FUTURE

| Capability | Horizon | Dependencies |
|---|---|---|
| Content Scanner (AI reads books) | 1-2 years | Publisher partnerships, copyright access, secure infrastructure |
| Student-book matching | 2-3 years | Content Scanner, student data, recommendation engine |
| Collection curation recommendations | 2-3 years | Network Intelligence + Content Scanner + student data |
| Publisher marketplace | 3+ years | Scale (1,000+ districts), Content Scanner, publisher participation |
| Reader Intelligence Layer | 3-5 years | Full stack: Content Scanner + Network Intelligence + student profiles |
| Multi-state regulatory engine | Ongoing | Expanding as legislation spreads (26 states → 35-40 projected) |

---

## Appendix: Data Fields & Intelligence Card

### The Book Intelligence Card (what users see on every book)

Based on the live product (1984 by George Orwell example):

**Header:**
- Book cover image
- Title, Author
- Location tag (e.g., "School Library")
- ISBN, Publisher, Year, Pages
- Action buttons: Set Status, Refresh Metadata, Delete Book
- Flag count badge (e.g., "36 Flags")

**Left Navigation:**
- Book Intelligence (main view)
- Guardian Activities
- Status History
- Circulation History
- Notes and Documents

**Intelligence Sections:**

1. **Synopsis** — From authoritative database (ISBNDB), including notable recognitions
2. **Subjects** — From ISBNDB and Open Library (dual-source)
3. **People/Characters** — Named characters and people referenced
4. **Times/Setting/Place** — When available
5. **Flags** — Tabbed by source type:
   - Library/Advocacy Organizations (count)
   - News/Media Outlets (count)
   - School/District Websites (count)
   - Each flag: Date, Category, Description, Source link, State, District
6. **Audience & Reading Level** — Age Range, Grade Level, Reading Level
7. **Content Ratings** — Violence, Sexual Content, Language (None/Mild/Moderate/Explicit) + Mature Themes tags
8. **Compliance & Challenge Risk** — Ban Status, Challenge Risk (Low/Medium/Flagged), Potential Concerns
9. **Grade Level Suitability** — Elementary/Middle School/High School (Suitable/Not Suitable)
10. **Advisory & Educational Context** — Parental Guidance recommendation, Content Warnings, Themes, Educational Value assessment
11. **AI Content Summary** — AI-generated overview of the book's content and themes

### Book Intelligence in Order Lists (what users see during review)

Compact inline view per book:
- Cover, Title, Author, Publisher, ISBN
- Age range badge
- Ban count + Challenge count (clickable for details)
- Summary
- Theme tags
- Notes (per-book, added by reviewers)
- Copies selector
- Ban Details popup: District name, School name, Reason, Tags, Date, Source link
- Challenge Details popup: District name, School name, Reason, Tags, Date, Source link

---

*This document is the canonical product truth for the Bookmarked Operating System. All agents, skills, and team members reference this for product context. Updates flow from the Founder through this document into the operating system.*
