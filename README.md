# 🤖 RABS (Reginald Atticus Bannedict Singleton III)

**RABS** (Real-time Adaptive Backend System) is a full-stack operational platform designed and developed by **Disability South West Ltd (DSW)**, an Australian NDIS service provider. Inspired by systems like MedCare and VisiCase but uniquely tailored for DSW’s evolving needs, RABS is being built from the ground up to manage every operational aspect of the organisation.

---

## ⚙️ Core Functional Areas

RABS provides functionality across all levels of service delivery, staffing, and administration:

- Schedule and coordinate participant programs  
- Assign and manage participant bookings  
- Handle complex rostering and staff scheduling  
- Manage billing and NDIS claims  
- Oversee communications and internal alerts  
- Track incidents, changes, and cancellations  
- Support payroll processing and HR workflows  
- Maintain daily operations and long-term planning  

This system aims to fully centralise and streamline operations within a single, adaptable interface.

---

## 🖥️ Frontend Development Strategy

To ensure long-term flexibility and platform-specific performance, RABS is being developed with multiple frontend targets:

- `frontend-vite`: Lightweight, blazing-fast web UI for the main interface  
- `frontend-next`: SSR-capable frontend for alternative rendering and SEO compatibility  
- `swift-ios`: Native iPhone and iPad experience  
- `swift-watchos`: Companion app for Apple Watch  
- `swift-tvos`: Dashboard and visualisation tools for Apple TV devices  

Each frontend consumes the same backend API and contributes to a shared operational memory.

---

## 🧰 Development Environment & Infrastructure

- Primary development and hosting is done on a Windows machine named `LUCAS`, using self-hosted services and local APIs  
- All platforms are synced via GitHub for version control  
- Mac Studio and MacBook laptops can remote into `LUCAS` or edit via synced directories  
- iPad development and editing is supported through **Firebase Studio**, a web-based IDE  
- Linux devices can interact via Git or Firebase Studio when needed  

---

## 🧠 Novel Concepts and Design Innovations

RABS is not just an app — it’s a new model for intelligent organisational software:

- **Reggie**, the operational agent, learns from task history, contradictions, and override patterns, conducting self-analysis and maintaining autonomous context logs  
- **CTCDs** (Custom Task Context Dumps) define logic deviations and behavioral exceptions per task type  
- **Context Buckets** allow memory entries to persist, decay, or gain salience based on frequency, weight, and consequence  
- **Reasoning Logs** track all major decisions with transparent logic traces, including justification, confidence, and source  
- **Epistemic Safety Nets** provide support for *"Agree to Disagree"* or *"Unknown"* resolution states  
- **Master Prompt Layering**: every AI action draws from a `System Prompt`, `Situation Prompt`, and `Welfare Prompt`  
- **Task Confidence Thresholds** determine when Reggie is allowed to auto-complete tasks vs when review is required  
- **Audit Trails and `why()` Queries** for on-demand explanations of any decision Reggie made  
- **Summary Type Categorisation**: output control via `Objective Type` (1–3) and `Category Level` (1–5) to define length, tone, and format  
- **Prompt Assembly Engine**: Reggie builds custom prompts from modular components based on task needs  
- **AI Task Isolation**: each task type (`summarise`, `explain`, `reflect`, `convert`, `tag`) is modular, overrideable, and versioned  
- **Central Model Matrix**: each AI task references a numeric shorthand (`model: 5`) mapped to specific model APIs (e.g. GPT-4o, Claude, Gemini)  
- **Versioned AI Behaviors**: all task templates and logic models are version-controlled to enable historical replay, auditability, and safe iteration  

---

## 🧪 Next Steps / Areas in Progress

- Finalise backend API schema for task processing and Reggie integration  
- Build a frontend status dashboard for reviewing Reggie’s decisions and confidence levels  
- Implement versioned CTCD management and context bucket editing tools  
- Add structured prompt templates for all common Reggie functions (`summarise`, `explain`, `justify`, etc.)  
- Develop `modelMatrix.json` to support model swapping via numeric shorthand  
- Integrate reasoning wrappers and self-evaluation logic into all high-impact tasks  
- Document memory shaping rules, prompt layering architecture, and fallback handling  
- Scaffold the “Reggie Is Alive” blog to share agent development insights and design philosophies  

---

## 🔗 Additional Docs

- [`docs/system-architecture.md`](docs/system-architecture.md)  
- [`docs/agent-design-principles.md`](docs/agent-design-principles.md)  
- [`docs/reggie-is-alive.md`](docs/reggie-is-alive.md)
