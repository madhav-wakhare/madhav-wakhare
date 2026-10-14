# Madhav Wakhare

**AI-enabled Site Reliability Engineer at [One2N](https://one2n.io), working toward inference engineering.**

I build and run the infrastructure that software depends on: CI/CD pipelines, cloud infrastructure as code, and the monitoring that tells you when something is wrong. I use AI tools every day to cut toil in that work. Now I am learning how to serve large language models reliably, from GPU memory up to the inference server, because model serving is becoming one more production system that an SRE must understand and run.

> "Be curious. Read widely. Try new things. What people call intelligence just boils down to curiosity."
> — Aaron Swartz (1986–2013)

## How I work

- **Solve the actual problem.** Start with the simplest design that works, and add complexity only when the system needs it.
- **Own it end to end.** If I build a pipeline or a module, I also document it, monitor it, and fix it when it breaks.
- **Automate the repeatable.** Manual steps that run more than twice become a script, a pipeline, or a Terraform module.
- **Learn in the open.** I read engineering blogs, try new tools on side projects, and write about what I find.

## Featured project

### [Smriti](https://github.com/madhav-wakhare/smriti)

A local-first work and learning tracker. It runs as a single Docker container and keeps all data in one SQLite file, so nothing leaves your machine.

- Kanban board with ageing indicators for items that wait too long
- Jira-style work logs and time tracking per task
- Learning topics and an engineering-blog reading list with notes
- Weekly report of time spent per day and per project

I built it to plan my own day and keep what I learn in front of me. It is the tool I use every working day.

## Selected work

**CI/CD pipeline for application delivery**
Built an automated pipeline with Jenkins, Docker, GitLab, and Nginx. GitLab webhooks and branch protection enforce code-quality checks before merge. CloudWatch and SNS report build and deploy status. Deployment time dropped by 70%.

**Infrastructure as code with Terraform**
Wrote modular, reusable Terraform for AWS infrastructure, with workspaces for separate environments. HashiCorp Vault supplies credentials at apply time, so no secrets live in code. This removed most manual provisioning steps and the errors that came with them.

**Datadog agent rollout across 100+ Linux servers**
Automated agent installation and configuration with Ansible and Jinja2 templates, run through Rundeck. Keeper Secrets Manager injects API keys at runtime. Monitoring is set per environment for EC2 hosts and MySQL on RDS.


## Tools I use

| Area | Tools |
| --- | --- |
| Cloud | AWS |
| Infrastructure as code | Terraform, Ansible |
| Containers and orchestration | Docker, Kubernetes |
| CI/CD and automation | Jenkins, GitLab CI, Rundeck |
| Observability | Datadog, CloudWatch |
| Secrets | HashiCorp Vault, Keeper Secrets Manager |
| Languages | Python, Bash |
| Operating systems | Linux |

## Currently exploring: inference engineering

Training a model happens once. Serving it happens on every request, and that is where latency, cost and reliability are decided. I am studying the full path from hardware to inference server, starting from first principles:

- **Hardware and memory.** Why GPUs need VRAM, and why memory bandwidth, not compute, usually limits token generation. How the PCIe link between system RAM and the GPU becomes the bottleneck, and how unified memory changes that trade-off.
- **Model weights.** How parameters, weights and size on disk relate. How to estimate the VRAM a model needs for its weights, its activations and its KV cache.
- **Models larger than the GPU.** How PyTorch and CUDA load weights to the GPU, and what happens when a 70B-parameter model does not fit in VRAM: CPU offloading, multi-GPU sharding, and their cost in speed.
- **Quantization.** Trading numeric precision for memory, and what it does to model quality.
- **The serving path.** Prefill and decode, prefix caching, and how engines such as vLLM use GPU memory to serve many requests at once.

My next step is to apply this the SRE way: serve open models with vLLM, measure latency and throughput, and define the SLOs and dashboards an inference service needs in production.

I also use LLMs in daily operations work and keep an eye on cloud cost optimization.

## Contact

[Email](mailto:wakharemadhav@gmail.com) · [LinkedIn](https://www.linkedin.com/in/madhavwakhare-devopsengineer/) · [Hashnode](https://hashnode.com/@madhav-wakhare)
