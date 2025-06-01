# codeRULES.md

RABS (Real-time Adaptive Backend System) is a private operational platform developed by Disability South West LTD to coordinate all administrative, operational, staffing, client, programming, facilities, and account needs. It integrates a structured AI agent (Reggie) and supports full task automation, dynamic documentation, multi-platform frontends, public-safe mirroring, a cognitive brainframe, novel context analytics, and bi-directional autonomy. Reginald Atticus Benedict Singleton III — at your service.

This document defines the **code conventions**, **folder structure**, and **project-wide standards** for all source code in the RABS system. It is designed to be used by both human developers and intelligent agents (like Reggie) for consistency, clarity, and maintainability.

---

## 🧠 Purpose

* Establish coding style consistency across the entire codebase
* Help AI agents generate and edit code that aligns with human standards
* Document the folder structure so tools and contributors know where things go
* Reduce ambiguity in cross-platform development (web, iOS, tvOS, backend)

---

## 📂 Project Root Standards

In the root of the RABS project you will find:

* `README.md` → Overview of the entire project
* `docGUIDE.md` → Rules for all documentation across RABS
* `codeRULES.md` → This file; defines shared coding and structural practices

Each major folder (e.g. `/backend`, `/frontend-vite`, `/swift-ios`) **may include its own**:

* `README.md` (module-specific summary)
* `docGUIDE.md` (if custom doc rules apply)
* `codeRULES.md` (if coding style diverges from root project rules)

---

## 🧱 General Coding Style

### JavaScript / Node / Express

* Use 2-space indentation
* Use `const` and `let` (never `var`)
* Prefer arrow functions `() => {}`
* Use named functions for exported utilities
* Always use semicolons `;`
* Group imports at the top, organized by external, then internal
* Use `.js` or `.mjs` extensions unless ES Modules require `.ts`

### Swift (iOS / watchOS / tvOS)

* Use 4-space indentation (Apple standard)
* CamelCase for variables and functions
* PascalCase for types and structs
* Use explicit `@State`, `@Binding`, etc. for SwiftUI where possible
* Separate logic and UI into different files where possible
* Consider UIKit or hybrid stack alternatives if SwiftUI performance issues arise

### JSON / YAML / Config

* Use 2-space indentation
* Keys should be in lowercase or kebab-case unless explicitly required
* Arrays and objects must be properly aligned and never mixed in-line

### Shell Scripts / CLI Helpers

* Prefer lowercase filenames with dashes (`build-deploy.sh`)
* Add `#!/bin/bash` shebang at the top
* All helper scripts should live in `/scripts`

---

## 💬 Code Commenting Guidelines

All files in RABS — whether generated or human-authored — should follow this standard for commenting:

* Every file must begin with a top-level comment block describing:

  * What this file is
  * What this file does
  * (Optional) Who or what generated it (e.g., Reggie)

* Use inline comments to describe sections of logic that would be unclear to someone seeing it for the first time

* For files that will be sanitized for public view (e.g. `rabs-public`), use `// {K}` at the beginning of any comment you want preserved in the public version

* Avoid using comments as versioning logs (Git handles that)

### Example:

```js
// File: userRouter.js
// Description: Express routes for managing user profiles and auth
// {K} Routes are grouped by feature folder for maintainability

const express = require('express');
const router = express.Router();
```

Reggie and sanitizer scripts will retain lines with `// {K}` when creating the public mirror, while removing all other logic and private content.

---

## 🗂 Folder Structure Guide

The RABS project is modular and supports multi-platform development. Core structure:

```
/rabs
├── backend/            # Express API and service logic
├── middleware/         # Shared server-side logic across endpoints
├── frontend-vite/      # React web interface using Vite
├── frontend-next/      # Next.js experimental frontend
├── frontend-reactn/    # Optional React Native for Apple platforms (alt to Swift)
├── swift-ios/          # Native iOS app
├── swift-tvos/         # Native Apple TV companion app
├── swift-watchos/      # Native Apple Watch interface (lightweight)
├── scripts/            # Automation scripts and CLI utilities
├── docs/               # Central documentation folder
├── data/               # Static datasets, e.g., mock data for dev
├── tests/              # Universal test suite and CI entrypoint
├── README.md           # Global project overview
├── docGUIDE.md         # Global documentation rules
├── codeRULES.md        # Global coding rules (this file)
```

---

## ✅ AI Agent Coding Behaviors

When an AI code assistant (like Reggie or Copilot) is generating or editing code:

* Use the correct file extension based on folder context
* Respect language-specific formatting rules defined above
* Place new files in the correct folder — use `/scripts` for helper CLI tools, `/frontend-*` for UI code, etc.
* Do not insert code blocks without filename context or purpose
* Include a comment at the top of generated files:

```js
// generated by Reggie :: purpose: {describe reason or task}
```

* Reference any supporting data files using relative paths (e.g., `../../data/mock-users.json`)
* Avoid hardcoding values that should be config-driven

---

## 🔄 Per-Folder Overrides

Any folder may include its own `codeRULES.md` file **if it has special conventions or deviates** from the global rules. For example:

* `/swift-ios/codeRULES.md` → Might define specific folder naming for ViewModels, Storyboards, etc.
* `/backend/codeRULES.md` → May define route structure, auth layer format, etc.

Global rules apply unless specifically overridden.

---

## 🧩 Section-Specific Coding Rules (Tables)

Each section includes a growing table of specific implementation rules.

### 🗃 backend/

| Date       | Rule                                                        | Why / Notes                                       |
| ---------- | ----------------------------------------------------------- | ------------------------------------------------- |
| 2024-05-30 | All API routes must live in `/backend/routes`               | Keeps endpoint organization predictable           |
| 2024-05-30 | Use `express.Router()` in all route files                   | Standardizes structure and enables modular routes |
| 2024-05-30 | Route files must match the endpoint name (e.g., `users.js`) | Improves discoverability and maintainability      |
| 2024-05-30 | Use `Joi` or validator for all incoming request schemas     | Enforces consistent and secure input validation   |

### 🔄 middleware/

| Date       | Rule                                                       | Why / Notes                                 |
| ---------- | ---------------------------------------------------------- | ------------------------------------------- |
| 2024-05-30 | Middleware functions must be named and exported explicitly | Enables reuse and testability               |
| 2024-05-30 | Avoid async middleware without error handlers              | Prevents silent failures or unhandled paths |

### 💻 frontend-vite/, frontend-next/, frontend-reactn/

| Date       | Rule                                                  | Why / Notes                                     |
| ---------- | ----------------------------------------------------- | ----------------------------------------------- |
| 2024-05-30 | Use React functional components                       | Aligns with modern standards and hooks usage    |
| 2024-05-30 | All components must live in `/components` or `/views` | Keeps UIs consistent and visually grouped       |
| 2024-05-30 | Use `/logic` or `/hooks` for non-UI logic             | Separates UI from core logic and reusable code  |
| 2024-05-30 | Avoid direct API calls inside components              | Promotes separation of concerns and testability |

### 📱 swift-ios/, swift-watchos/, swift-tvos/

| Date       | Rule                                                        | Why / Notes                                 |
| ---------- | ----------------------------------------------------------- | ------------------------------------------- |
| 2024-05-30 | Organize using MVVM when applicable                         | Supports scalability and modularity         |
| 2024-05-30 | UI in `/Views`, logic in `/ViewModels`                      | Improves structure and readability          |
| 2024-05-30 | Avoid deep SwiftUI view nesting                             | Keeps layout modular and memory-safe        |
| 2024-05-30 | Fallback to UIKit if SwiftUI impacts performance or clarity | Ensures smooth UX and platform compliance   |
| 2024-05-30 | Document UIKit usage clearly if mixed                       | Maintains clarity in hybrid implementations |

---

✅ Keep this file up to date as new platforms, frontends, or coding conventions emerge.
