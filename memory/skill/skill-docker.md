---
id: skill-docker
title: Docker & containerization
type: skill
description: Containerizing services for orchestrated deployment.
tags: [docker, devops]
status: active
visibility: public
created: 2026-07-02
updated: 2026-08-10
proficiency: advanced
related: [skill-kubernetes]
source: agent
---

Containerize backend services for Kubernetes/EKS deployment; comfortable with image build, layering, and runtime concerns.

**Docker Compose operational debugging** (AgentBosun P6): resolved a healthy-stack bring-up by diagnosing (1) hostname-vs-loopback healthchecks — probe `$(hostname)` rather than localhost; (2) wolfi/minimal images that ship without `wget`/`curl`, requiring a Python `urllib` probe instead; and (3) secrets baked into named volumes at first init — after changing `.env` you must `poe reset` (tear down volumes) or the old secrets persist.
