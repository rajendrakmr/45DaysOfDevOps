# 🗺️ Roadmap: 45 Days of DevOps

A day-by-day plan from containers to platform engineering. Each day has a **build** goal, a **break** drill (a deliberate failure), and a **deliverable** committed to the repo.

> Rule of thumb: if you did not break it and fix it, you did not learn it yet.

---

## Phase 1: Containers (Days 1–5)

| Day | Topic | Build | Break / Debug | Deliverable |
|-----|-------|-------|---------------|-------------|
| 01 | Docker basics | Run the FastAPI app in a container | Container crashes on startup | Working `Dockerfile` + notes |
| 02 | Docker Compose | API + PostgreSQL + Redis stack | Database connection failure | `docker-compose.yml` running |
| 03 | Config and env | Move config to environment variables | Missing / wrong env variable | Incident write-up |
| 04 | Networking and volumes | Custom networks, persistent volume | Network failure between services | Diagram + notes |
| 05 | Healthchecks and hardening | Healthchecks, non-root user, slim images | Healthcheck failure | `01-docker/incidents/` entries |

## Phase 2: Kubernetes (Days 6–15)

| Day | Topic | Build | Break / Debug | Deliverable |
|-----|-------|-------|---------------|-------------|
| 06 | Cluster setup, Namespaces | Local cluster + `devops-lab` namespace | Wrong context / namespace | Setup notes |
| 07 | Deployments | Deploy `devops-api` with 2 replicas | ImagePullBackOff | Manifest + incident |
| 08 | Services | ClusterIP service, port-forward | Service unavailable (selector mismatch) | Manifest + incident |
| 09 | ConfigMaps | Externalize app config | Missing ConfigMap key | Manifest + notes |
| 10 | Secrets | Inject secrets safely | Secret not mounted | Manifest + notes |
| 11 | Probes | Readiness and liveness probes | Readiness / liveness failure | Incident write-ups |
| 12 | Resources and scheduling | Requests, limits, quotas | OOMKilled, Pending Pod | Incident write-ups |
| 13 | Ingress | Ingress controller + routing | Ingress 404 | Manifest + incident |
| 14 | RBAC | ServiceAccount, Role, RoleBinding | RBAC Forbidden | Manifest + incident |
| 15 | Troubleshooting review | Rerun all incidents from scratch | CrashLoopBackOff, DNS failure | Troubleshooting cheat sheet |

## Phase 3: AWS (Days 16–20)

| Day | Topic | Build | Deliverable |
|-----|-------|-------|-------------|
| 16 | VPC | Public/private subnets, route tables, NAT | Architecture diagram |
| 17 | EC2 and IAM | Instance with least-privilege role | Lab notes |
| 18 | ALB | Load balancer in front of EC2 targets | Lab notes |
| 19 | EKS | Cluster overview and node groups | Architecture notes |
| 20 | S3 and RDS | Bucket policies, private RDS | Architecture diagram |

> Destroy all AWS resources at the end of each lab day.

## Phase 4: Terraform (Days 21–25)

| Day | Topic | Build | Deliverable |
|-----|-------|-------|-------------|
| 21 | Providers, variables, outputs | Dev environment scaffold | `environments/dev` |
| 22 | Modules | `vpc`, `security-group`, `ec2` modules | `modules/` |
| 23 | Remote state and locking | S3 backend + DynamoDB lock | Backend config + notes |
| 24 | Drift | Change resources manually, detect and fix | Drift incident write-up |
| 25 | Dev vs prod | Compose modules per environment | `environments/prod` |

## Phase 5: CI/CD (Days 26–29)

| Day | Topic | Build | Deliverable |
|-----|-------|-------|-------------|
| 26 | GitHub Actions basics | Test + syntax check | `ci.yml` |
| 27 | Lint and security scan | Linters, image and dependency scanning | Updated workflow |
| 28 | Docker build and push | Build image, push to registry | Updated workflow |
| 29 | Deploy and rollback | Deploy to Kubernetes, rollback strategy | Workflow + notes |

## Phase 6: Helm and GitOps (Days 30–33)

| Day | Topic | Build | Deliverable |
|-----|-------|-------|-------------|
| 30 | Helm chart | Convert manifests into `devops-api` chart | `06-helm/charts/devops-api` |
| 31 | Helm values | Per-environment values, helpers | Values files + notes |
| 32 | ArgoCD | Install ArgoCD, sync the app from Git | `07-gitops/argocd` |
| 33 | GitOps failures | Drift, failed sync, invalid manifest, rollback | Incident write-ups |

## Phase 7: Observability (Days 34–37)

| Day | Topic | Build | Deliverable |
|-----|-------|-------|-------------|
| 34 | Prometheus | Scrape app and cluster metrics | Config + queries |
| 35 | Grafana | Dashboards: CPU, memory, requests, errors, latency | Dashboard JSON |
| 36 | Alertmanager | Alerts for restarts, availability, error rate | Alert rules |
| 37 | Logging | Centralized logs with Loki | Config + notes |

## Phase 8: SRE (Days 38–40)

| Day | Topic | Build | Deliverable |
|-----|-------|-------|-------------|
| 38 | SLIs and SLOs | Define SLIs/SLOs for `devops-api` | `09-sre/sli-slo` |
| 39 | Error budgets | Burn-rate calculation and policy | `09-sre/error-budget` |
| 40 | Incidents and postmortems | Simulated incident, RCA, blameless postmortem | `09-sre/postmortems` |

## Phase 9: Platform and Automation (Days 41–43)

| Day | Topic | Build | Deliverable |
|-----|-------|-------|-------------|
| 41 | Backstage | Developer portal with a catalog entry | `10-platform-engineering/backstage` |
| 42 | Golden paths | Service template with CI/CD, K8s, observability | `templates/`, `golden-path/` |
| 43 | Automation scripts | Unhealthy pod finder, log/event collector, incident report generator | `11-automation/` |

## Phase 10: Interview Prep (Days 44–45)

| Day | Topic | Focus |
|-----|-------|-------|
| 44 | System design | HA Kubernetes, production CI/CD, observability, platform design |
| 45 | Final review | Mock interview, rerun weakest incidents, polish repo and profile |

---

## Definition of Done (per day)

- [ ] Lab runs from a clean state
- [ ] At least one failure reproduced and fixed
- [ ] Notes committed (symptom → investigation → root cause → fix → prevention)
- [ ] [PROGRESS.md](./PROGRESS.md) updated
- [ ] Cloud resources destroyed

## Stretch Goals

- Add a service mesh (Istio or Linkerd) after Day 33
- Add policy as code (OPA/Kyverno) after Day 29
- Add cost visibility for AWS labs
- Write a blog post per phase