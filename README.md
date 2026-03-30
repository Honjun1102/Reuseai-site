# ReuseAI Site

ReuseAI helps you stop paying full inference cost for repeated LLM requests.

This repository hosts the public product site for ReuseAI, a request-level
response cache / reuse system for repeat-heavy LLM traffic.

## What it is

A proxy-first cache / replay layer in front of your existing LLM backend
(Ollama, vLLM, or OpenAI-compatible APIs).

No model changes. No retraining. No kernel work.

## Results on repeat-heavy workloads

- Customer support templates: **66.67% hit ratio**, **+660.95% TPS**, **-86.91% TTFT**
- API parameterized requests: **50.00% hit ratio**, **+98.11% TPS**, **-49.56% TTFT**
- Structured prompts with variables: **25.00% hit ratio**, **+35.36% TPS**, **-26.27% TTFT**

## Quickstart

1. Install Docker.
2. Start the proxy:

   ```bash
   docker run --rm -p 8080:8080 --env-file .env reuseai-response-cache-proxy
   ```

3. Point your client or API gateway to:

   ```text
   http://localhost:8080
   ```

4. Set your upstream backend in `.env`:

   ```text
   UPSTREAM_BASE_URL=http://host.docker.internal:11434
   ```

## Pilot

Start with one service or workflow. Route real or replayed traffic through
ReuseAI, measure hit ratio / TTFT / throughput impact, and decide whether a
broader rollout is worth it.

For pilot inquiries: honjun@tju.edu.cn

## Best fit

- Support / ops tools
- Private API inference services
- Workflow / agent systems with repeated prompts

## When it works best

- Repeat-heavy traffic
- Template-based requests
- Retry-heavy API workloads

## When it does not

- Fully random chat
- Highly variable prompts
- Workloads with little or no repetition

## Public links

- Public landing page: https://honjun1102.github.io/Reuseai-site/
- Public repository: https://github.com/Honjun1102/Reuseai-site

## Pages

This repository is published from the `main` branch root with GitHub Pages.
