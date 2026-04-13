# Story Bank — Master STAR+R Stories

This file accumulates your best interview stories over time. Each evaluation (Block F) adds new stories here. Instead of memorizing 100 answers, maintain 5-10 deep stories that you can bend to answer almost any behavioral question.

## How it works

1. Every time `/career-ops oferta` generates Block F (Interview Plan), new STAR+R stories get appended here
2. Before your next interview, review this file — your stories are already organized by theme
3. The "Big Three" questions can be answered with stories from this bank:
   - "Tell me about yourself" → combine 2-3 stories into a narrative
   - "Tell me about your most impactful project" → pick your highest-impact story
   - "Tell me about a conflict you resolved" → find a story with a Reflection

## Stories

### [Architecture] Database Emailer Replatform
**Source:** Report #062 — GLP-1 Companion Startup — Founding Staff Engineer
**S (Situation):** Legacy LAMP stack with 1.2 billion records on a single server, no scalability or modern observability.
**T (Task):** Replatform to a cloud-native architecture while maintaining uptime and data integrity.
**A (Action):** Designed Kubernetes architecture on Vultr/AWS, migrated data to ClickHouse + PostgreSQL, built React frontend and Node.js API, implemented CI/CD with GitHub Actions, added HyperDX and PostHog for observability.
**R (Result):** Platform handles 1.2 billion records with modern cloud-native stack, automated deployments, and full observability.
**Reflection:** Would have started with a smaller data migration pilot before the full cut-over to reduce risk.
**Best for questions about:** system design, scaling, migration, infrastructure decisions, technical leadership

### [Mobile/Health] Tooths React Native App
**Source:** Report #062 — GLP-1 Companion Startup — Founding Staff Engineer
**S (Situation):** Needed a consumer-facing mobile app for a 3-sided dental health marketplace connecting patients, hygienists, and dentists.
**T (Task):** Build React Native mobile app with microservices backend and full DevOps pipeline.
**A (Action):** Architected on AWS EKS, implemented React Native + React web, collaborated with designers in Figma, deployed DataDog observability, set up CI/CD with security scanning.
**R (Result):** Functional marketplace app with microservices backend, zero-downtime deployments, and automated alerting.
**Reflection:** Would invest more upfront in a design system for consistency across mobile and web platforms.
**Best for questions about:** mobile development, health tech, design collaboration, startup building, observability

### [AI] Source Scribe — AI Documentation Generator
**Source:** Report #062 — GLP-1 Companion Startup — Founding Staff Engineer
**S (Situation):** Code repositories consistently lacked up-to-date documentation, slowing onboarding and knowledge transfer.
**T (Task):** Build an AI-powered tool that generates and maintains documentation automatically.
**A (Action):** Created a SaaS product using AI to analyze repositories and generate comprehensive docs covering onboarding, architecture, infrastructure, and contribution guides.
**R (Result):** Continuously updated documentation that stays in sync as new code and information is added.
**Reflection:** Would add user feedback loops earlier to refine AI output quality based on what developers actually find useful.
**Best for questions about:** AI integration, product building, developer tools, automation
