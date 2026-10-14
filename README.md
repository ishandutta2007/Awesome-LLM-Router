# Awesome-LLM-Router

# Top LLM Router Tools Ecosystem

**Curated List of SaaS Products & Open-Source GitHub Projects**  
*Focused on Intelligent Request Routing, Provider Failover & Cost-Aware Model Selection*  
**Last updated: March 2026**

This repository tracks notable **SaaS platforms** and **open-source projects** for **LLM Routing**. These tools sit between your application and model providers, deciding which model to send each request to based on cost, latency, capability, and availability — reducing spend, improving reliability, and avoiding vendor lock-in.

**Examples** include OpenRouter, LiteLLM, Portkey, Braintrust, ClawRouter, Manifest, RouteLLM, Cloudflare AI Gateway, Inworld Router, and Vercel AI Gateway (the category leaders).

**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, custom routing policies, and transparent cost tracking — ideal for AI engineers prioritizing data sovereignty, developers building production inference infrastructure, and teams facing unpredictable token bills.

Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.

## Table of Contents
- [SaaS/Hosted Platforms](#saas-hosted-platforms)
- [Open-Source GitHub Projects](#open-source-github-projects)
- [How to Contribute](#how-to-contribute)
- [Disclaimer](#disclaimer)

## SaaS/Hosted Platforms

- **[OpenRouter](https://openrouter.ai/)**  
  Unified API routing to 300+ models from multiple providers with automatic fallback. Charges **5.5% fee on credit purchases** ($0.80 minimum); inference pricing passed through with no markup [citation:1]. BYOK has a plan-dependent free allowance measured by list-price inference cost ($25,000/month on pay-as-you-go), with 5% fee above the allowance [citation:1]. Free tier: 50 requests/day without purchased credits, 1,000/day with at least $10 purchased [citation:1]. Non-USD card payments add 1-3% Stripe FX conversion on top [citation:9].

- **[Portkey](https://portkey.ai/)**  
  AI Gateway with guardrails routing to 1,600+ LLMs. **Dev plan is free forever with 10,000 requests/month**, Pro at **$49/month for 100,000 requests** (overage $9/month per 100K up to 3M), Enterprise custom [citation:3]. Features load balancing, retries with exponential backoff, request timeouts, and multimodal routing. Powers cost attribution for 200+ enterprises running 400B+ tokens/day [citation:11]. Self-hostable OSS version under MIT license.

- **[Braintrust](https://www.braintrust.dev/)**  
  Evaluation and observability platform with gateway capabilities. **Starter plan is $0/month** with $10 monthly credits, 1 GB processed data, 10k scores, and 14-day retention. **Pro at $249/month** adds 5 GB data, 50k scores, 30-day retention, RBAC, and priority support [citation:4][citation:12]. Calling built-in models directly through the gateway requires Pro or Enterprise [citation:4]. Enterprise supports BYOC and self-hosted deployment [citation:12].

- **[Cloudflare AI Gateway](https://developers.cloudflare.com/ai-gateway/)**  
  Managed gateway within Cloudflare ecosystem. **Core features free on all plans** — dashboard analytics, caching, rate limiting [citation:8]. **5% fee on Unified Billing credit purchases**; inference pricing passed through with no markup [citation:8]. Guardrails billed as Workers AI token-based inference [citation:8]. Log storage: 100,000 logs on Workers Free, 10M per gateway on Workers Paid [citation:16]. Near-zero operational overhead; trade-off is some data control [citation:13].

- **[Vercel AI Gateway](https://vercel.com/)**  
  Managed gateway integrated with Vercel's frontend cloud, providing unified access to multiple model providers with usage tracking and observability.

- **[Manifest](https://manifest.build/)**  
  LLM routing and cost optimization platform with intelligent model selection based on request complexity.

- **[ClawRouter](https://clawrouter.com/)**  
  LLM routing service with cost-aware model selection and automatic failover across providers.

- **[Inworld Router](https://inworld.ai/)**  
  Routing layer for game and interactive AI applications with latency-optimized model selection.

## Open-Source GitHub Projects

- **[LiteLLM](https://github.com/BerriAI/litellm)**  
  **The foundational open-source LLM proxy** translating OpenAI-format API calls to 100+ providers. MIT licensed, 18k+ GitHub stars [citation:10]. Offers Python SDK and self-hosted AI Gateway (Proxy) with virtual keys, spend tracking, load balancing, retries/fallbacks, and admin dashboard. **Hidden operational costs**: $200-500/month infrastructure, 20-40ms production latency overhead [citation:2][citation:10]. Enterprise features require ~$30k annual fee [citation:2]. The default choice for teams wanting a self-hosted gateway they fully own [citation:13].

- **[RouteLLM](https://github.com/lm-sys/RouteLLM)**  
  **Reference framework for LLM routing between strong and weak models.** Reduces cost by **over 2x** without compromising quality on MT Bench [citation:7]. Provides OpenAI-compatible server where clients specify `router-mf-[threshold]` to control cost-quality tradeoff per request [citation:7][citation:15]. Trained routers include matrix factorization, similarity-weighted ranking, and BERT. Threshold calibration based on Chatbot Arena data [citation:7]. Leverages LiteLLM to support any OpenAI-compatible endpoint including local Ollama [citation:15].

- **[Portkey Gateway (OSS)](https://github.com/Portkey-AI/gateway)**  
  Open-source core of Portkey's AI Gateway with load balancing, fallbacks, retries, and guardrails. MIT licensed with managed Pro/Enterprise options.

- **[GhostRouter](https://pypi.org/project/ghostrouter/)**  
  **LLM router that learns** across 10+ providers with fallback, circuit breakers, budget tracking, and post-model redaction [citation:14]. Features trust tiers (models tagged with trust levels; calls can require minimum tier), eligibility filtering by intent/verbosity/determinism, and execution traces recording which models were tried [citation:14]. Supports OpenAI, Anthropic, Gemini, xAI, Mistral, Groq, Together, DeepSeek, Perplexity, and Ollama [citation:14]. Async-native with HTTP API daemon mode [citation:14].

- **[OpenZiti LLM Gateway](https://github.com/openziti/llm-gateway)**  
  OpenAI-compatible proxy for routing across OpenAI, Anthropic, and OpenAI-compatible backends (Ollama, vLLM, llama-server, SGLang). Distinctive angle: connects gateways and private inference backends through zrok/OpenZiti for routing across NAT or private networks without exposing backend ports [citation:5]. Single Go binary with YAML config, model-prefix routing, semantic routing, and virtual API keys [citation:5].

- **[radlab-llm-router](https://pypi.org/project/radlab-llm-router/)**  
  Open-source router with load balancing strategies (balanced, weighted, dynamic_weighted, first_available, first_available_optim), semantic BiEncoder routing, RAG plugin, payload masking, and content guardrails [citation:6]. Features **error masking** — internal IPs, URLs, and stack traces are stripped from caller-facing responses while server-side logs retain full debugging info [citation:6]. Docker and Helm deployment [citation:6].

### Additional Strong Open-Source Options

- **Kong AI Gateway** — AI gateway features within Kong's mature API gateway platform. Strong plugin ecosystem and enterprise API management. Heavier than purpose-built LLM proxies; best for teams already running Kong [citation:5][citation:13].
- **Apache APISIX** — Cloud-native API gateway with AI gateway use cases. Mature Apache project with strong API management foundations [citation:5].
- **New API** — Broad provider aggregation gateway (mentioned alongside LiteLLM and Portkey in comparisons) [citation:5].
- **Helicone** — Open-source LLM observability and gateway with caching, rate limiting, and cost tracking.
- **LangChain Router** — Routing components within the LangChain ecosystem for model selection based on prompt characteristics.

**Frameworks for building custom systems**: Combine **LiteLLM** for unified provider access with spend tracking, **RouteLLM** for calibrated strong/weak model routing, **GhostRouter** for learned routing with circuit breakers and post-model redaction, **Portkey Gateway OSS** for guardrails and governance, and **OpenZiti LLM Gateway** for private network routing to self-hosted inference backends to build a complete LLM routing stack.

## How to Contribute

1. Fork the repo.
2. Add/edit entries in `README.md` (follow existing format).
3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.
4. Submit PR with a short explanation.

Star the repo if you find it useful!

## Disclaimer

- This is a **community-curated** list — not exhaustive and not an endorsement.
- LLM routers must comply with provider terms of service, data protection regulations (GDPR, CCPA), and SLAs for production workloads. **Routing decisions affect output quality** — thresholds and quality gates must be calibrated against your specific task distribution before production deployment. Self-hosted solutions like LiteLLM carry hidden operational costs ($200-500/month infrastructure, 20-40ms latency overhead) beyond the software itself [citation:2][citation:10]. Verify current pricing directly with providers before committing.

---

**Made for AI engineers, platform teams, MLOps practitioners, and developers building cost-efficient inference infrastructure.**  
Let's make LLM routing more open, cost-aware, and production-ready.
