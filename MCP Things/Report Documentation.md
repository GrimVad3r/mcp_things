This documentation captures the integration of a custom **Model Context Protocol (MCP)** server into VS Code, following the systematized "distributed cognition" workflow inspired by Boris Cherny.

---

## 🛠️ MCP Integration & Workflow Documentation

### 1. What I Did: Rule File Evolution

I modified the `.github/copilot-instructions.md` (or `CLAUDE.md`) to move away from generic AI behavior toward a **tool-augmented architectural role**.

* **Configured MCP Proxy:** Added the `tenxfeedbackanalytics` server to the VS Code settings to bridge the AI's reasoning with real-time feedback data via the `https://mcppulse.10academy.org/proxy` endpoint.
* **Explicit Headers:** Injected environment-specific metadata (`X-Device`, `X-Coding-Tool`) to ensure the MCP server returns platform-optimized code (e.g., ensuring shell commands match the OS).
* **Workflow Rules:** Added a "Verification Loop" rule requiring the agent to query the MCP feedback tool *before* finalizing any refactor, ensuring it aligns with the project's analytical metrics.

### 2. What Worked: Successful Configurations

* **The "Plan Mode" Enforcement:** By setting the rule "Do not write code until a plan is approved," the AI stopped making "guess-work" edits and started explaining how it would use the new MCP tools first.
* **Contextual Headers:** Hardcoding the `X-Device` and `X-Coding-Tool` in the JSON config resolved initial issues where the AI attempted to use Linux-specific commands on a Windows environment.
* **Tool-First Logic:** The AI successfully recognized the `tenxfeedbackanalytics` as a source of truth for optimization, rather than relying solely on its training data.

### 3. What Didn't Work: Challenges & Troubleshooting

* **The "Context Window" Bloat:** Initially, the AI tried to pull too much data from the MCP server at once, hitting token limits.
* *Solution:* Updated the instructions to mandate **atomic queries**—only asking for feedback on specific modules rather than the whole codebase.


* **Connection Timeouts:** The proxy URL occasionally hung.
* *Solution:* Added a "Retry & Log" rule in the documentation, instructing the AI to notify the user and fall back to local analysis if the MCP server remains unresponsive for >5 seconds.


* **JSON Formatting:** VS Code’s `settings.json` is sensitive. A missing comma in the `headers` block initially broke the Copilot extension.

### 4. Insights Gained: The "Agentic" Shift

The most significant insight is that **rules transform the AI from a "chatty assistant" into a "precision instrument."**

* **Alignment of Intent:** Without these rules, the AI defaults to "pleasing" the user with quick code. With the rules, it adopts my "thought pattern" of **Reliability over Speed**.
* **Reduced Cognitive Load:** Because the instructions now handle the "how" (e.g., "always use the MCP tool for feedback"), I can focus purely on the "what."
* **Systematized Correction:** Using Boris Cherny’s "Correction Tax" philosophy, I realized that if the AI ignores the MCP data once, the fix isn't to tell it again in chat—it's to **strengthen the rule file** to prevent a recurrence.

---
