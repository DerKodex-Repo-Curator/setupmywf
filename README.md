# SetupMyWF

> **ComfyUI setup takes hours. We do it in seconds.**

[setupmywf.com](https://setupmywf.com) · Live SaaS · 2026

---

## What it is

A SaaS that takes any ComfyUI workflow JSON and emits a complete, deployable setup script for cloud GPU pods (Vast.ai / RunPod). Models, nodes, dependencies, CUDA fixes — all in one `.sh` you paste into a fresh pod.

## The problem we solve

ComfyUI workflows are fragile. Every new workflow means:
- Hunting models across HuggingFace, CivitAI, direct links (URLs break weekly).
- Installing custom nodes whose Python requirements aren't listed.
- Fighting `mediapipe` / `onnxruntime` / CUDA version mismatches.
- Burning 1–3 hours at $0.40/hr per GPU pod just to get to "generate".

We do that work upfront, parse the workflow once, and hand back a single script.

## How it works

```
Upload workflow JSON  →  Analysis  →  Generate .sh script  →  Paste in pod
   (free, no account)    (free)        ($1.20–$0.67/script)   (one command)
```

- **Parse**: extract every model, custom node, dependency, latent size from the workflow.
- **Resolve**: match models to HuggingFace / CivitAI sources; track gated-repo licences.
- **Fix**: apply 50+ known CUDA / dependency patches for current ComfyUI ecosystem.
- **Emit**: single `.sh` with `wget` model downloads + `pip install` + `git clone` for custom nodes + start command.
- **Update**: when model URLs break, scripts auto-refresh — free forever.

## Pricing

| Tier            | Price       | Per script  |
| --------------- | ----------- | ----------- |
| Free analysis   | $0          | —           |
| 5 scripts       | $5.99       | $1.20       |
| 15 scripts      | $9.99       | $0.67       |
| Pro (coming)    | $9.99/mo    | 15/mo + extras |

Pro tier (soon): one-click deploy to Vast.ai / RunPod, unified multi-workflow scripts, cloud storage for outputs and LoRAs, GPU price comparison, pod management dashboard.

## Stack

- Frontend: Next.js, deployed on Vercel
- Backend: Python (FastAPI), worker queue for workflow parsing
- Payments: Stripe (one-off pack purchases + upcoming subscription)
- Auth & DB: Supabase
- Localization: EN / RU

## Status

Live since April 2026. Currently in early MVP — paying users, daily generation activity, roadmap focused on one-click pod deploy.

---

## Founder & maintainer

Built solo (with a co-founder on infra side) by **[Kristina Balandiuk](https://www.linkedin.com/in/christina-balandiuk-a35ab433a/)**.

This repository hosts only the public documentation and screenshots. Source is closed.
