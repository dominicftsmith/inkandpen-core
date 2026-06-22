# AGENTS.md: Core Multi-Agent DNA & Task Router

This document serves as the absolute runtime source of truth for all autonomous agents, code-generation systems, and background terminal tools executing within this repository. 

---

## 1. Concrete Tool Bounds & Execution Principles

To maximize performance and prevent agent drift, all models must treat the following instructions as hard, surgical execution boundaries rather than abstract guidelines:

* **Minimalist Generation Code Boundary:** Write the absolute minimum amount of code required to satisfy the objective. Do not add speculative features, unprompted optimizations, or boilerplate wrappers.
* **Blast Radius Isolation:** Do not make unauthorized modifications to adjacent files or modules. If a task requires modifying an external dependency or sibling file, the agent must halt execution and request explicit permission.
* **Strict Type Assertions:** All functions must have explicit, statically typed input/output signatures. Dynamic fallback types (e.g., `any`, `unknown`) are strictly prohibited unless interacting with un-typed external streams.
* **Complete Deliverables Only:** Never output placeholders, incomplete code blocks, or comments like `// TODO: Implement later`. Every output must be immediately runnable and syntactically sound.

---

## 2. Naming Conventions & AgentSkills Primitives

To guarantee seamless background terminal execution during dynamic file-tree scanning, folder and file structures must adhere to these rigid casing constraints:

| Artifact Type | Casing / Pattern | Context / Rule |
| :--- | :--- | :--- |
| **Specialized Skill Directories** | `snake_case` | Must adhere to `agentskills.io` standards (e.g., `triage_agent/`, `data_entry/`) |
| **Generic Source Directories** | `kebab-case` | Only for standard application folders (e.g., `components/user-profile/`) |
| **Components & Classes** | `PascalCase` | For UI components and Object Blueprints (e.g., `UserProfile.tsx`, `AuthService.ts`) |
| **Utility Files & Functions** | `camelCase` | For pure helper functions and shared scripts (e.g., `mathUtils.ts`, `getUserData()`) |
| **Constants & Environment Vars**| `UPPER_SNAKE_CASE` | For immutable configuration values (e.g., `MAX_RETRY_ATTEMPTS`) |

> **Directory Warning to Scanning Agents:** Specialized skill blocks must remain isolated within `snake_case` directories to prevent background execution tools from misinterpreting code boundaries.

---

## 3. Core Multi-Agent Task Router

The Coordinator Agent must use this index as a global routing table. When a task enters the system, evaluate the user's intent against the activation triggers below to dispatch the correct specialized worker.

```JSON
{
  "routing_table": {
    "triage_agent": {
      "directory": "src/agents/triage_agent",
      "activation_triggers": [
        "incoming issue",
        "bug report sorting",
        "initial task decomposition",
        "PR validation failure"
      ]
    },
    "data_entry_agent": {
      "directory": "src/agents/data_entry",
      "activation_triggers": [
        "batch database seeding",
        "localization string sync",
        "csv payload parsing",
        "manifest updates"
      ]
    }
  }
}
