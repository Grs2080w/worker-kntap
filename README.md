This is the enhanced version of the **Worker-knotew** documentation. I have organized the technical components, operational modes, and monitoring metrics into clear tables to make the architectural overview easier to digest.

---

# **Worker-knotew**

> "High-performance background worker for the Knotew ecosystem."
> **Scalable synchronization between Google Drive, GitHub, and Supabase.**

---

## 🎯 Overview

**Worker-knotew** is a specialized Go-based service designed to process intensive synchronization jobs. It functions as a bridge between cloud storage (Google Drive), version control (GitHub), and a central database (Supabase), utilizing Redis for low-latency token caching and Prometheus for real-time health monitoring.

### 🚀 Core Capabilities

| Feature | Description |
| --- | --- |
| **Job Polling** | Continuously monitors Supabase for pending synchronization tasks. |
| **Multi-Provider Sync** | Handles updates and data transfers for Google Drive and GitHub. |
| **Token Caching** | Uses Redis to store and retrieve access tokens, reducing API overhead. |
| **Observability** | Native Prometheus integration exporting metrics on port `8080`. |

---

## 🛠️ Operational Modes

The worker is architected to be flexible based on infrastructure requirements:

* **Concurrent Mode:** Runs multiple worker loops within a single process for high-throughput environments.
* **Isolated Mode:** Runs a single worker per process, ideal for microservices or containerized isolation.

---

## 📊 Monitoring & Metrics

Real-time visibility is provided via the `/metrics` endpoint. The following metrics are tracked to ensure system reliability:

| Metric Name | Description |
| --- | --- |
| `JobExecutionDuration` | Time taken to complete a single synchronization task. |
| `JobsProcessed` | Total count of successfully completed jobs. |
| `JobsFailed` | Count of jobs that failed due to logic or provider issues. |
| `JobsError` | Count of critical system or network errors. |
| `IdleIterations` | Tracks how often the worker finds no pending jobs (polling efficiency). |
| `MemoryUsageBytes` | Real-time RAM consumption of the worker process. |

---

## 🏗️ Architecture & Packages

| Package Path | Responsibility |
| --- | --- |
| `packages/worker` | Core concurrent worker loop logic. |
| `packages/worker/IsolatedWorker` | Logic for running workers in single-instance mode. |
| `packages/supa` | Supabase abstractions for queue management and token storage. |
| `packages/redis` | Redis client implementation for high-speed token caching. |
| `packages/prometheus` | Metric registration and recording logic. |

---

## 🗺️ Roadmap

<div align="center">
<img width="70%" src="./roadmap.png" alt="Worker-knotew Roadmap">
</div>

---

## 🔗 Project Context

This worker is a critical component of the **Knotew** platform.

> [!TIP]
> To see how this worker fits into the larger ecosystem, check the main Knotew repository as soon as it becomes available!

---

## Considerations

This worker is made for Knotew, click the link below when it becomes available!
