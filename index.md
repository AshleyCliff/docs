# Charmed HPC

Charmed HPC is a platform for managing high-performance computing clusters. It automates the lifecycle of essential cluster software and processes, such as workload management, shared storage, GPU access, and high-bandwidth networking. This allows operations teams and systems administrators to focus on running workloads rather than maintaining infrastructure.

---

## In this documentation

### Point of Entry

- __Getting started:__ [Getting Started tutorial](tutorial-getting-started-with-charmed-hpc)

### Lifecycle

- __Provision and deploy:__ [Initialize cloud environment](howto/initialize-cloud-environment.md); [Deploy Slurm](howto/deploy/deploy-slurm.md); [Deploy shared filesystem](howto/deploy/deploy-shared-filesystem.md)
- __Manage and operate:__ [Manage compute nodes and partitions](howto/manage/manage-compute-nodes.md); [Rotate Slurm authentication keys](howto/manage/rotate-slurm-keys.md); [Migrate a single slurmctld unit to high availability](howto/manage/migrate-slurmctld-to-high-availability.md)
- __Decommission and clean up:__ [Clean up Slurm](howto/cleanup/cleanup-slurm.md); [Clean up cloud resources](howto/cleanup/cleanup-cloud-resources.md)

### Stack layers and core machinery

- __Architecture and foundations:__ [Underlying projects](reference/underlying-projects-and-dependencies.md)
- __Running workloads:__ [Integrate with Apptainer](howto/integrate/integrate-with-apptainer.md); [Use Apptainer](howto/run-workloads/use-apptainer.md)
- __Hardware:__ [GPUs](explanation/gpus.md); [GRES](reference/gpus.md); [Interconnects](explanation/interconnects.md); [Public cloud interconnects](reference/interconnects.md)

### Performance and Quality

- __Identity and access:__ [Deploy identity provider](howto/deploy/deploy-identity-provider.md)
- __Observability and monitoring:__ [Integrate with COS](howto/integrate/integrate-with-cos.md); [Integrate with InfluxDB](howto/integrate/integrate-with-influxdb.md); [Integrate with a mail server](howto/integrate/integrate-with-email.md); [Email notifications for jobs](explanation/job-email-notifications.md); [Grafana dashboards](reference/monitoring/grafana-dashboards.md); [Prometheus alerts](reference/monitoring/prometheus-alerts.md); [Prometheus metrics](reference/monitoring/prometheus-metrics.md); [Loki logs](reference/monitoring/loki-logs.md)
- __Security and cryptography:__ [Hardening guidelines](reference/hardening.md); [Cryptography](explanation/cryptography.md); [Key rotation](explanation/key-rotation.md)
- __Performance:__ [Benchmarks](reference/performance.md)
- __Reliability and availability:__ [High availability](explanation/high-availability.md); [Reboot timing](explanation/reboot-timing.md)

### Reference and Community

- __Reference:__ [Glossary](reference/glossary.md)
- __Contribute:__ [Contribute to documentation](contributing/documentation.md); [Contribute to code](contributing/code.md)

## How this documentation is organized

This documentation uses the [Diátaxis](https://diataxis.fr/) documentation structure.

* The [Tutorial](tutorial-getting-started-with-charmed-hpc) takes you step-by-step through building a small Charmed HPC cluster, submitting batch jobs, and using container images.

* [How-to guides](howto/index) assume you have basic familiarity with Charmed HPC. They cover key operations for [deploy](howto/deploy/index.md), [integration](howto/integrate/index.md), [management](howto/manage/index.md), and [usage](howto/run-workloads/index.md).

* [Reference](reference/index) provides technical information such as [underlying projects and dependencies](reference/underlying-projects-and-dependencies.md), [monitoring](reference/monitoring/index.md), and [performance benchmarks](reference/performance.md).

* [Explanation](explanation/index) includes topic overviews, background and context, and detailed discussions of key concepts.
---

## Project and community

Charmed HPC is an Ubuntu community project. It's an open source project that warmly welcomes community contributions, suggestions, fixes, and constructive feedback.

**Get involved**

* [Support](https://discourse.ubuntu.com/c/project/hpc/151)
* [Online chat](https://matrix.to/#/#hpc:ubuntu.com)
* [Contribute](contributing/index)

<!-- **Releases**

* [Release notes](https://discourse.ubuntu.com/c/hpc/151)
* [Roadmap](https://github.com/orgs/canonical/projects) -->

**Governance and policies**

* [Code of Conduct](https://ubuntu.com/community/ethos/code-of-conduct)
<!-- * [Commercial support](https://ubuntu.com/pro) -->

Thinking about using Charmed HPC for your next project? [Get in touch!](https://matrix.to/#/#hpc:ubuntu.com)

```{filtered-toctree}
:hidden:
:titlesonly:

Getting started <getting-started>
howto/index
explanation/index
reference/index
contributing/index
```
