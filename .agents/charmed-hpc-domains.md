# Charmed HPC — Suggested Domains of Concern

Applies the [Domains of Concern](domains-of-concern.md) pattern to the Charmed HPC
documentation. This document presents the resulting domain set — the current map of what exists
today and the ideal map of what the documentation should become. For the decisions, disagreements,
and adjustments that produced it, see the
[session notes](domains-of-concern-session-notes.md).

## Purpose and scope

- Organize the Charmed HPC documentation along the *thematic* axis described by the Domains of
  Concern pattern (orthogonal to the existing Diátaxis structure).
- The current home-page groupings were deliberately set aside; the domains below were derived
  fresh from the pages in the repository.

This document works in the pattern's two registers, and keeps them explicitly separate:

- **The current documentation** — *analyzing and understanding* the pages that exist today, and
  organizing only those real pages into domains. This is the [Current domain set](#current-domain-set):
  a faithful, comprehensive, descriptive map of the current repository.
- **The ideal documentation** — *creating* the domains the product should eventually have, by
  extending the current map with the content an HPC platform's documentation should include but
  currently lacks. This is the [Ideal domain set](#ideal-domain-set): a generative plan that
  names the gaps.

The current set contains solely existing pages; the ideal set adds proposed pages, marked so the
two registers never blur together. The two sets need not share an identical slice structure: each
is organized to best fit what it contains. Where they diverge, it is because a slice earns its
independence only once it holds enough content — so a theme that is a standalone slice in the
ideal set may be folded into a neighbour in the current set until the pages that justify it are
written.

Legend used in the ideal set:

- **`NEW`** — a page that does not yet exist but that the ideal set should include.
- **`PLACEHOLDER`** — a reserved stub for anticipated content in a thin, growing slice.

## Coverage audit

- **42** Markdown files exist across the documentation directories.
- **10** `index.md` landing pages are excluded per the coverage rule (the pattern is expressed
  on them).
- **32** content pages must each be represented exactly once.

Findings:

- **Gap found and fixed.** `howto/cleanup/cleanup-cloud-resources.md` was initially unplaced. It
  is the teardown counterpart to `howto/initialize-cloud-environment.md` and now sits in the
  **Decommission & clean up** slice.
- **Not missing.** The `howto-manage-*` reference anchors (rotate keys, node state, partitions,
  transition to high availability, and so on) are **sections within `manage-slurm.md`**, not
  separate files, so they are not counted as gaps.
- With the fix applied, all **32** content pages are placed exactly once.

## Gaps identified

These are the differences between the current and the ideal — the content that moves the
documentation from what exists today toward the ideal set. The ideal set proposes the following
additions (concentrated in user-facing job submission, architecture/concepts, lifecycle
operations, storage, and release information):

- Tutorials: run-and-monitor-a-workload; quickstart / installation summary.
- Architecture explanation (converged machine-plane / K8s-control-plane); requirements &
  supported platforms; Slurm concepts (nodes, partitions, jobs, QoS).
- Running workloads: submit batch & interactive jobs; software environment / modules; data
  staging & management.
- Storage: storage concepts; `PLACEHOLDER` shared storage reference.
- Lifecycle: end-to-end deployment walkthrough / Terraform plan reference; accounting &
  fair-share; scale the cluster; upgrade & update.
- Performance and Quality: login nodes & user access; TLS / certificate & secrets management;
  backup & disaster recovery.
- Support: troubleshooting & diagnostics; FAQ.
- Reference and Community: release notes / changelog.

(current-domain-set)=

## Current domain set

*The documentation as it exists today.* This is the descriptive map: it places only the pages
currently in the repository. It is the result of analyzing and understanding the current content,
and it stands on its own as an accurate view of the present documentation. Slices that would
exist only to hold not-yet-written pages are omitted here.

### Band A — Point of Entry

1. **Getting started**
   - `getting-started.md`

### Band B — Lifecycle *(lifecycle stages)*

2. **Provision & deploy** *(intrinsic cluster setup)*
   - `howto/initialize-cloud-environment.md`
   - `howto/deploy/deploy-slurm.md`
   - `howto/deploy/deploy-shared-filesystem.md`
3. **Manage & operate** *(day-two operations)*
   - `howto/manage/manage-slurm.md`
4. **Decommission & clean up**
   - `howto/cleanup/cleanup-slurm.md`
   - `howto/cleanup/cleanup-cloud-resources.md`

### Band C — Stack layers and core machinery

5. **Architecture & foundations**
   - `reference/underlying-projects-and-dependencies.md`
6. **Running workloads**
   - `howto/run-workloads/use-apptainer.md`
   - `howto/integrate/integrate-with-apptainer.md`
7. **Hardware** *(features)*
   - `explanation/gpus.md`, `reference/gpus.md`
   - `explanation/interconnects.md`, `reference/interconnects.md`

### Band D — Performance and Quality

8. **Identity & access**
   - `howto/deploy/deploy-identity-provider.md`
9. **Observability & monitoring**
   - `howto/integrate/integrate-with-cos.md`, `integrate-with-influxdb.md`,
     `integrate-with-email.md`
   - `explanation/job-email-notifications.md`
   - `reference/monitoring/grafana-dashboards.md`, `prometheus-alerts.md`,
     `prometheus-metrics.md`, `loki-logs.md`
10. **Security & cryptography**
    - `reference/hardening.md`
    - `explanation/cryptography.md`
    - `explanation/key-rotation.md`
11. **Performance** *(quality)*
    - `reference/performance.md`
12. **Reliability & availability**
    - `explanation/high-availability.md`
    - `explanation/reboot-timing.md`

### Band E — Reference and Community

13. **Reference**
    - `reference/glossary.md`
14. **Contribute**
    - `contributing/code.md`
    - `contributing/documentation.md`

The current set covers all **32** current content pages across **5 bands → 14 slices**. Its
structure differs deliberately from the ideal set below:

- **Troubleshooting & support** is not a standalone slice here. Its only current page,
  `explanation/reboot-timing.md`, sits in **Reliability & availability** — the two read as one
  "keeping the cluster healthy" theme at this scale. The dedicated support slice earns its own
  place in the ideal set once diagnostics and FAQ content exist.
- **Shared storage**, **Scale & maintain**, and **Upgrade & update** do not appear at all,
  because they would currently hold only proposed pages.
- The **Reliability & availability** slice holds high availability and the reboot-timing
  explanation here; the ideal set additionally folds in backup & disaster recovery and renames it
  accordingly.

(ideal-domain-set)=

## Ideal domain set

*The documentation the product should eventually have.* This is the generative plan: it takes
the current set above and extends it with the content an HPC platform's documentation should
include but currently lacks. Proposed pages are marked `NEW`, and reserved stubs `PLACEHOLDER`,
so this register never blurs with the current one. The structure grows to **5 bands → 18 slices**.

### Band A — Point of Entry

1. **Getting started**
   - `getting-started.md`
   - `NEW` Second tutorial: run and monitor a real workload

### Band B — Lifecycle *(lifecycle stages)*

2. **Provision & deploy** *(intrinsic cluster setup)*
   - `howto/initialize-cloud-environment.md`
   - `howto/deploy/deploy-slurm.md`
   - `howto/deploy/deploy-shared-filesystem.md`
   - `NEW` End-to-end deployment walkthrough / Terraform deployment-plan reference
3. **Manage & operate** *(day-two operations)*
   - `howto/manage/manage-slurm.md`
   - `NEW` Accounting & fair-share (`sacct`, `sacctmgr`, limits)
4. **Scale & maintain**
   - `NEW` Scale the cluster (add/remove compute nodes)
5. **Upgrade & update**
   - `NEW` Upgrade & update the cluster
6. **Decommission & clean up**
    - `howto/cleanup/cleanup-slurm.md`
    - `howto/cleanup/cleanup-cloud-resources.md`

### Band C — Stack layers and core machinery

7. **Architecture & foundations**
   - `reference/underlying-projects-and-dependencies.md`
   - `NEW` Architecture explanation (converged machine-plane / K8s-control-plane)
   - `NEW` Requirements & supported platforms
8. **Running workloads**
   - `howto/run-workloads/use-apptainer.md`
   - `howto/integrate/integrate-with-apptainer.md`
   - `NEW` Software environment / modules
   - `NEW` Data staging & management
9. **Shared storage** *(thin slice, expected to grow)*
   - `NEW` Storage concepts (Ceph/CephFS, `filesystem-client`)
   - `PLACEHOLDER` Shared storage reference
10. **Hardware** *(features)*
    - `explanation/gpus.md`, `reference/gpus.md`
    - `explanation/interconnects.md`, `reference/interconnects.md`

### Band D — Performance and Quality

11. **Identity & access**
    - `howto/deploy/deploy-identity-provider.md` *(add-on)*
    - `NEW` Login nodes & user access
12. **Observability & monitoring**
    - `howto/integrate/integrate-with-cos.md`, `integrate-with-influxdb.md`,
      `integrate-with-email.md`
    - `explanation/job-email-notifications.md`
    - `reference/monitoring/grafana-dashboards.md`, `prometheus-alerts.md`,
      `prometheus-metrics.md`, `loki-logs.md`
13. **Security & cryptography**
    - `reference/hardening.md`
    - `explanation/cryptography.md`
    - `explanation/key-rotation.md`
    - `NEW` TLS / certificate & secrets management
14. **Performance** *(quality)*
    - `reference/performance.md`
15. **Reliability, availability & recovery**
    - `explanation/high-availability.md`
    - `NEW` Backup & recovery
16. **Troubleshooting & support**
    - `explanation/reboot-timing.md`
    - `NEW` Troubleshooting & diagnostics
    - `NEW` FAQ

### Band E — Reference and Community

17. **Reference**
    - `reference/glossary.md`
    - `NEW` Release notes / changelog
18. **Contribute**
    - `contributing/code.md`
    - `contributing/documentation.md`

## Coverage confirmation

- **Current set** — all **32** current content pages are placed exactly once across **5 bands →
  13 slices**; the **10** `index.md` landing pages are excluded per the coverage rule.
- **Ideal set** — the same **32** pages plus the `NEW` pages and **1** `PLACEHOLDER`, across
  **5 bands → 17 slices**.
