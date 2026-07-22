# Domains of Concern

A conceptual reference for the *Domains of Concern* pattern: a way of organizing documentation by
*theme* — the domains a user cares about — as a layer orthogonal to Diátaxis. This document covers
what a domain is, how the slices are structured and scaled, the kinds of concerns a product
surfaces and how to sort pages among them, the two registers the pattern is applied in (mapping
the documentation that *exists* versus the documentation that *should*), and the principles that
guide the whole. The examples throughout illustrate the idea — they are not templates, titles, or
checklists to reproduce.

## Core concept

A *domain of concern* is a thematic slice of a product's documentation: a grouping of pages
reflecting how a user thinks about the product and their use of it. The pattern is this
conceptual division and its management — not any particular HTML, visual design, or labels.

The pattern is always applied in one of two registers, settled up front because it governs every
decision that follows: the **current map** describes the pages that exist today, and the **ideal
map** plans the pages the product should eventually have. Both are built the same way, but each is
organized to fit what it contains, so their slice structures may differ — the current map need not
prefigure the ideal one (see [The current map and the ideal map](#the-current-map-and-the-ideal-map)). The sections below apply to both, noting any point that bears on one in particular.

Slices tend to fall into recognizable kinds — for example *stack layers* (hardware, control
plane, an abstract layer such as mathematics), *lifecycle stages* (using, deploying,
developing), or *features* a user benefits from. These are common observations, not a required
set; a product produces whatever slices match how its users reason about it.

A page belongs to a slice by its *theme* — the question a reader is holding when they seek it —
not by a word it shares with other pages. Pages whose titles share a verb (for instance
"deploy") do not automatically belong together; grouping by a shared verb drifts back toward
organizing by the reader's *mode of engagement*, which is Diátaxis's axis, not this one.

## Structural pattern

One adaptable layered hierarchy that scales with the documentation:

- Minimum two layers: a slice and the pages listed under it.
- When slices themselves need organizing, add a grouping layer above them.

Layer count responds to scale; it is not a mode chosen in advance. The grouping layer emerges
only once the number of slices grows enough to need it — a reaction to size, never a starting
decision.

Slice size is likewise driven by content, not padded to look uniform. A single-page slice is fine
when one page is genuinely all there is to say on the theme; the alternative — a premature merge
that buries a subject inside an unrelated slice — is worse. What a thin slice may *contain*
differs by register: the current map holds only realized pages, while the ideal map may also
reserve placeholders for a subject the product will grow into (see below).

## Kinds of concerns a product surfaces

An *illustrative, non-exhaustive* sampling showing the *range* of concerns that can appear —
not a taxonomy to apply, not headings to use:

- points of entry (arriving and getting going)
- essential machinery / stack layers
- features (product-specific benefits)
- resources and interfaces the product relates to but does not contain
- qualities it must uphold (e.g. security, performance, accessibility, energy efficiency)
- lifecycle stages (using, deploying, maintaining, scaling, upgrading, developing)
- customer or industry use cases

Which apply, their names, and their number are wholly product-dependent. The point is the
*kinds* of thinking a product invites, not any fixed list.

A few distinctions recur when deciding *which* kind a page expresses. They apply when building
either map — in the current map they sort pages that exist, and in the ideal map they also guide
where proposed pages should land:

- **Intrinsic machinery vs. optional add-ons.** When several pages describe setting up parts of
  a product, separate the parts without which the product does not exist from the parts layered
  on to enhance it. The intrinsic parts tend to gather in a foundational or provisioning slice;
  the add-ons stay with the feature or theme they extend.
- **Conceptual vs. operational.** Understanding *how a component works* is a stack-layer concern;
  *doing day-to-day tasks* with that same component is a lifecycle concern. The same subject can
  therefore appear along two different slices without contradiction.
- **Cross-cutting reactive concerns are not lifecycle stages.** Activities such as
  troubleshooting or support apply at *every* stage rather than sitting at one point in a
  sequence; they read better as their own slice than wedged into a lifecycle arc.
- **Keep quality slices pure.** A slice expressing a quality the product upholds (security,
  reliability, performance) is diluted if reactive or diagnostic material is folded into it;
  give that material its own home so each slice keeps a single, legible theme.

## Relationship to Diátaxis

Orthogonal. Diátaxis organizes content by the reader's mode of engagement (tutorial, how-to,
reference, explanation); Domains of Concern organizes the same content by theme. It implies no
content rearrangement — it describes the existing thematic space along a different axis.

## The current map and the ideal map

Each register yields a map that is a legitimate end in itself.

**The current map** *describes* what exists — reading the pages, relating them thematically, and
organizing only that real content. It answers "what is the case today?" and must read as a
*self-standing, complete* account of the present: a reader should never sense it is missing pieces
or waiting to be filled in. Its slices are all realized, and it is judged complete against what
exists, not against some larger ambition. Use it to describe, audit, or restructure the
documentation as it stands.

**The ideal map** *creates* — extending the current map with content the themes imply but that is
not yet written, via proposed pages, reserved placeholders, or slices marking where the product
will grow. It answers "what should the documentation eventually be?" Use it to plan and prioritize
future work.

Keep the two distinct: settle the register up front rather than drifting from present into wish
mid-map, and when presenting both, mark everything ideal-only so the current map stays legible by
ignoring those marks. The gap between them *is* the roadmap — what the ideal map has and the
current map lacks is exactly the documentation still to write.

The two maps may also differ in *structure*, not just contents. Each is organized to fit what it
holds, so a theme that warrants its own slice in the ideal map can be folded into a neighbour in
the current map until the pages that justify it exist — and, more rarely, the current map may
group pages in a way the ideal map later outgrows. The current map should not be distorted to
prefigure the ideal; let each read as the best organization of its own contents.

## Guiding principles

- **System** — a reusable system for dividing and managing ideas into domains, applicable
  across products; not tied to one implementation.
- **Rationality** — its structure fits how users already think, so they can work with it.
- **Completeness** — represents the whole documentation (every part, not every detail), giving
  a synoptic view. It is measured against the register: the current map accounts for every page
  that *exists*, the ideal map for every page that *should* exist.
- **Density** — presents a large directory of information compactly, pressuring the
  architecture toward quality.
- **Pragmatism** — meant to be bent, extended, and truncated to fit very different scales while
  keeping a recognizable shape.
- **Exposition** — shows *what is the case* and exposes the documentation's own thinking; acts
  as a forcing function that surfaces gaps, excess, and contradictions. Mapping every page
  against the slices makes absent content visible, which is what lets the current map expose the
  gaps the ideal map then fills.

## Coverage rule

Every page should be represented, except the home page and landing pages — where the pattern
is typically expressed. In the current map, "every page" means every page that exists; in the
ideal map, it also means every page that should exist. Either way, a page that goes unrepresented
signals either a missing slice or a page that does not belong.
