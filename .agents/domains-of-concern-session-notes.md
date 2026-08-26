# Domains of Concern — Session Notes

A record of the concepts, discussion points, disagreements, adjustments, and outcomes from the
working session that reviewed the Charmed HPC documentation and refined the Domains of Concern
material. This is a summary of *what changed and why* — not a restatement of the pattern itself.
For the pattern, see [`domains-of-concern.md`](domains-of-concern.md); for the Charmed HPC
application, see [`charmed-hpc-domains.md`](charmed-hpc-domains.md).

## Starting point

- Goal: apply the Domains of Concern pattern to the Charmed HPC docs and propose domains,
  deliberately ignoring the groupings already on the home page.
- The proposal went through several rounds of critique and adjustment before settling.

## Key concepts that emerged or were sharpened

These are the ideas the conversation surfaced and then folded back into the general pattern
document:

- **Theme, not shared verb.** A page belongs to a slice by the question a reader is holding, not
  by a word its title shares with others (e.g. "deploy"). Grouping by a verb drifts back toward
  the Diátaxis axis.
- **Intrinsic machinery vs. optional add-ons.** Pages that set up parts a product cannot exist
  without belong to a foundational/provisioning slice; add-ons stay with the theme they extend.
- **Conceptual vs. operational.** Understanding how a component works is a stack-layer concern;
  operating it day to day is a lifecycle concern. The same subject can sit in both.
- **Cross-cutting reactive concerns are not lifecycle stages.** Troubleshooting and support apply
  at every stage, so they read better as their own slice than inside a lifecycle arc.
- **Keep quality slices pure.** A quality slice (security, reliability) is diluted if reactive or
  diagnostic content is folded in; give that content its own home.
- **Thin slices are legitimate.** A single-page slice is fine when that is genuinely all there is
  to say; premature merges that bury a subject are worse.
- **Two registers — current vs. ideal.** The pattern applies either to the documentation that
  *exists* (a descriptive map that must read as complete in itself) or to the documentation that
  *should* exist (a generative plan that may add proposed pages and placeholders). The gap between
  them is the roadmap.
- **The two registers may differ in structure, not just contents.** Each map is organized to fit
  what it holds, so the current and ideal sets need not share the same slices. A theme that
  warrants its own slice in the ideal set can be folded into a neighbour in the current set until
  the pages that justify it exist. The current map should not be distorted to prefigure the ideal.

## Discussion and disagreement points, with resolutions

### 1. Where do the deploy pages belong?

- **Tension:** initial instinct was to keep `deploy-slurm` with the other Slurm pages under a
  workload-management slice.
- **Counter-point raised:** deploying Slurm and the shared filesystem is *intrinsic* to standing
  up a cluster (Slurm being the keystone), whereas identity, observability, and container
  integrations are add-ons.
- **Resolution:** adopt an intrinsic-vs-add-on criterion. `deploy-slurm` and
  `deploy-shared-filesystem` move to **Provision & deploy**; add-on deploys stay with their
  thematic slices. This avoids a generic "deploy everything" bucket.

### 2. What happens to the storage slice once deploy moves out?

- **Options:** (A) keep a thin storage slice for concepts, anticipating growth; (B) fold storage
  into Architecture and drop the standalone slice.
- **Resolution — Option A.** Keep a thin **Shared storage** slice with a concepts page and a
  reserved placeholder, expecting future storage reference content.

### 3. Does troubleshooting belong under Reliability, or in Lifecycle?

- **Tension:** troubleshooting is not a lifecycle *stage*, and only partly fits reliability
  (a designed-in quality) versus reactive diagnosis.
- **Resolution — Option 2 (of three considered).** Remove troubleshooting from Lifecycle; keep
  **Reliability & availability** as HA-only; add a dedicated **Troubleshooting & support** slice.

### 4. Should cluster management sit in the stack layers?

- **Tension:** managing a cluster is an operate/maintain activity, not a static stack layer.
- **Resolution:** remove the workload-management stack slice. Operational content
  (`manage-slurm`, accounting) moves to a new **Manage & operate** lifecycle slice; conceptual
  content (nodes, partitions, jobs, QoS) moves to **Architecture & foundations**.

### 5. Is backup & recovery a lifecycle stage?

- **Tension:** a *Back up & recover* slice had been placed in the Lifecycle band, but backup is
  ongoing maintenance and recovery is reactive — neither sits at a single point in a sequence, so
  neither is really a lifecycle stage.
- **Resolution — Option 2 (of three considered).** Drop the standalone lifecycle slice and move
  backup & disaster recovery into the reliability slice as a designed-in *resilience* capability.
  It pairs naturally with high availability and fills out reliability, an important aspect of
  Charmed HPC; the slice is renamed **Reliability, availability & recovery**. (Note the earlier
  "keep quality slices pure" principle: backup/DR fits here because it is a resilience capability,
  not reactive diagnosis — the latter still lives in Troubleshooting & support.)

### 6. Must the current and ideal sets share the same slice structure?

- **Tension:** the current set had been forced to mirror the ideal set's slices, which left some
  current slices holding a single page purely to prefigure the ideal.
- **Resolution:** the two sets need not share a structure — each is organized to best fit what it
  contains. In the current set, **Troubleshooting & support** (its only present page being
  `reboot-timing`) is folded into **Reliability & availability**, since at this scale they read as
  one "keeping the cluster healthy" theme; the dedicated support slice earns independence in the
  ideal set once diagnostics and FAQ exist. This drops the current set from 14 to 13 slices.

## Adjustments to the deliverables

The above decisions were threaded back into both documents:

- **Coverage audit.** Found and fixed one unplaced page (`cleanup-cloud-resources`); confirmed the
  `manage-slurm` anchors were sections, not missing pages, at the time of the audit; verified all
  content pages are represented once (landing pages excluded). `manage-slurm` has since been split
  into topic-based pages, so those anchors now live on separate pages placed in the slices matching
  their topics.
- **Lifecycle band added.** Introduced a dedicated Lifecycle grouping band, then refined its
  membership as the discussions above resolved.
- **General document.** Wove the sharpened concepts into `domains-of-concern.md`, added the
  current-vs-ideal distinction, and threaded it through the whole document with the emphasis that
  the current map must look *complete as it stands*, not like it is waiting for more.
- **Editing pass.** Removed redundancy in the current-vs-ideal material (it had been restated in
  several places), unified terminology to "current map"/"ideal map," and rewrote the intro to
  preview the document's full contents.
- **Charmed HPC document.** Split the single proposed structure into an explicit **Current domain
  set** (existing pages only, reading as complete) and an **Ideal domain set** (existing plus
  proposed `NEW`/`PLACEHOLDER` pages).
- **Home-page implementation.** Applied the current domain set to the root `index.md` "In this
  documentation" section: the five bands as sub-headings and the thirteen slices as linked bullets,
  pointing at the existing pages. The Diátaxis directory structure and the "How this documentation
  is organized" section were left intact — the domains are an added thematic navigation layer, not
  a reorganization of files. The Contribute slice links directly to the documentation and code
  contribution pages rather than the `contributing/` landing page.

## Outcomes

- **Final structure:** five grouping bands over seventeen thematic slices in the ideal set (down
  from eighteen after backup & recovery merged into reliability); the current set covers the same
  32 existing pages across thirteen realized slices — deliberately fewer, since it is organized to
  fit today's content rather than to prefigure the ideal.
- **Lifecycle band, settled:** Provision & deploy → Manage & operate → Scale & maintain →
  Upgrade & update → Decommission & clean up 
- **Two clean registers:** a self-standing description of today's documentation, plus a plan that
  names the proposed pages and one placeholder as the roadmap.
- **Documents produced/updated:** `domains-of-concern.md` (general pattern, refined),
  `charmed-hpc-domains.md` (Charmed HPC application), and these session notes.

## Open follow-ups (not yet actioned)

- Prioritize the proposed `NEW` pages into a build order.
- Optionally align the Charmed HPC document's "Actual/Ideal" headings with the general document's
  "current map"/"ideal map" wording for exact parity.
