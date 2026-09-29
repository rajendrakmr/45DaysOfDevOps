# 🚀 45 Days of DevOps

> A hands-on, incident-driven journey from solid DevOps fundamentals to **senior-level** Docker, Kubernetes, AWS, Terraform, GitOps, Observability, SRE, and Platform Engineering.

![Status](https://img.shields.io/badge/status-in%20progress-blue)
![Duration](https://img.shields.io/badge/duration-45%20days-green)
![Focus](https://img.shields.io/badge/focus-DevOps%20%7C%20SRE%20%7C%20Platform-orange)

---

## 📌 About

This repository documents a **45-day structured learning plan** built around one idea: *seniors are made by breaking things and fixing them, not by watching tutorials.*

Every section contains:

- **Production-style labs**, not toy examples
- **Deliberate incidents** to troubleshoot (CrashLoopBackOff, OOMKilled, DNS failures, RBAC errors, and more)
- **Notes and runbooks** written as if for an on-call teammate
- **Interview-ready explanations** of what was built and why

---

## 🗺️ Learning Path

| Days (suggested) | Module | Focus |
|------------------|--------|-------|
| 1 – 5 | [01-docker](./01-docker) | Containerized FastAPI + PostgreSQL + Redis, Compose, healthchecks, failure debugging |
| 6 – 15 | [02-kubernetes](./02-kubernetes) | Namespaces, Deployments, Services, ConfigMaps, Secrets, Probes, Resources, Ingress, RBAC, 10 incident drills |
| 16 – 20 | [03-aws](./03-aws) | VPC, EC2, IAM, ALB, EKS, S3, RDS architecture and labs |
| 21 – 25 | [04-terraform](./04-terraform) | Modules, remote state, locking, drift, dev/prod environments |
| 26 – 29 | [05-cicd](./05-cicd) | GitHub Actions: test, lint, security scan, build, push, deploy |
| 30 – 31 | [06-helm](./06-helm) | Turning raw manifests into reusable charts and per-environment values |
| 32 – 33 | [07-gitops](./07-gitops) | ArgoCD sync, drift, rollback, failed syncs |
| 34 – 37 | [08-observability](./08-observability) | Prometheus, Grafana, Alertmanager, logging |
| 38 – 40 | [09-sre](./09-sre) | SLI/SLO/SLA, error budgets, incident management, postmortems |
| 41 – 42 | [10-platform-engineering](./10-platform-engineering) | Backstage, golden paths, self-service templates |
| 43 | [11-automation](./11-automation) | Python and Bash tooling for pod triage, log/event collection, incident reports |
| 44 – 45 | [12-interview-prep](./12-interview-prep) | System design, scenario questions, final review |

> The day ranges are a guideline. See [ROADMAP.md](./ROADMAP.md) for the detailed plan and [PROGRESS.md](./PROGRESS.md) for the tracker.

---

## 📁 Repository Structure

```text
senior-devops-45-days/
├── README.md
├── ROADMAP.md
├── PROGRESS.md
├── CONTRIBUTING.md
│
├── 01-docker/                  # App, Dockerfile, docker-compose, incidents
├── 02-kubernetes/              # Manifests by resource type + incidents
├── 03-aws/                     # Architecture diagrams and labs
├── 04-terraform/               # environments/{dev,prod} + modules/{vpc,security-group,ec2}
├── 05-cicd/                    # .github/workflows pipelines
├── 06-helm/                    # Charts
├── 07-gitops/                  # ArgoCD applications
├── 08-observability/           # prometheus, grafana, alertmanager, logging
├── 09-sre/                     # sli-slo, error-budget, incidents, postmortems
├── 10-platform-engineering/    # backstage, templates, golden-path
├── 11-automation/              # python, bash
├── 12-interview-prep/          # Q&A and system design notes
└── linkedin/                   # Public build-in-progress posts
```

---

## 🧰 Tech Stack

| Area | Tools |
|------|-------|
| Containers | Docker, Docker Compose |
| Orchestration | Kubernetes, Helm |
| Cloud | AWS (VPC, EC2, IAM, ALB, EKS, S3, RDS) |
| IaC | Terraform |
| CI/CD | GitHub Actions |
| GitOps | ArgoCD |
| Observability | Prometheus, Grafana, Alertmanager, Loki |
| Platform | Backstage |
| Automation | Python, Bash |
| Sample App | FastAPI, PostgreSQL, Redis |

---

## ⚡ Quick Start

### Prerequisites

- Docker and Docker Compose
- `kubectl` and a local cluster (kind, minikube, or Docker Desktop)
- Terraform `>= 1.6.0`
- Helm 3
- An AWS account (use the free tier and **always destroy resources after labs**)
- Git and Python 3.12+

### Run the Day 1 lab

```bash
git clone https://github.com/<your-username>/senior-devops-45-days.git
cd senior-devops-45-days/01-docker

docker compose up --build
```

Then verify the API:

```bash
curl http://localhost:8000/
curl http://localhost:8000/health
```

### Deploy the first Kubernetes workload

```bash
cd ../02-kubernetes
kubectl apply -f namespaces/devops-lab.yaml
kubectl apply -f deployments/devops-api.yaml
kubectl apply -f services/devops-api.yaml
kubectl get all -n devops-lab
```

---

## 🔁 Daily Routine

Each day follows the same loop:

1. **Learn:** read or watch just enough to start (30 min)
2. **Build:** implement the lab from scratch (60–90 min)
3. **Break:** trigger a realistic failure on purpose
4. **Fix:** debug using logs, events, metrics, and docs, then write a short RCA
5. **Document:** commit notes and update [PROGRESS.md](./PROGRESS.md)
6. **Share:** optionally post a summary in `linkedin/`

---

## 🔥 Incident-Driven Learning

Troubleshooting is the core skill. Labs are designed around real failures:

**Docker:** container crash, missing environment variables, network failure, database connection failure, healthcheck failure

**Kubernetes:** CrashLoopBackOff, ImagePullBackOff, OOMKilled, Pending Pod, Service unavailable, DNS failure, Readiness failure, Liveness failure, Ingress 404, RBAC Forbidden

Each incident should end with:

```text
Symptom → Investigation → Root Cause → Fix → Prevention
```

---

## ✅ Progress

Track daily completion in [PROGRESS.md](./PROGRESS.md).

| Week | Days | Status |
|------|------|--------|
| 1 | 01 – 07 | ⬜ Not started |
| 2 | 08 – 14 | ⬜ Not started |
| 3 | 15 – 21 | ⬜ Not started |
| 4 | 22 – 28 | ⬜ Not started |
| 5 | 29 – 35 | ⬜ Not started |
| 6 | 36 – 42 | ⬜ Not started |
| Final | 43 – 45 | ⬜ Not started |

---

## 🎯 Outcomes

By Day 45, this repo should demonstrate the ability to:

- Containerize and debug multi-service applications
- Design, deploy, and troubleshoot workloads on Kubernetes
- Provision AWS infrastructure with reusable Terraform modules
- Build CI/CD pipelines with quality and security gates
- Operate a GitOps workflow with ArgoCD
- Build monitoring and alerting around SLIs and SLOs
- Run incident response and write blameless postmortems
- Design a platform with golden paths and self-service templates
- Explain all of it confidently in a senior DevOps/SRE interview

---

## ⚠️ Cost and Security Notes

- AWS labs can incur charges. Destroy resources with `terraform destroy` when finished and set up billing alerts.
- Never commit secrets. `.env`, `*.tfstate`, and `.terraform/` are already in `.gitignore`.
- Credentials in the sample `docker-compose.yml` are for **local learning only**.
- The `nginx:latest` image is used as a placeholder; pin versions in real environments.

---

## 🤝 Contributing

Suggestions, corrections, and new incident scenarios are welcome. See [CONTRIBUTING.md](./CONTRIBUTING.md) for guidelines.

---

## 👤 Author

**Rajendra Kumar Marandi**
DevOps & Software Engineer

- GitHub: [@your-username](https://github.com/your-username)
- LinkedIn: [your-profile](https://linkedin.com/in/your-profile)

---

## 📄 License

This project is licensed under the MIT License. Add a `LICENSE` file to make it official.

---

⭐ If this repository helps you, consider giving it a star and following along with the journey!
