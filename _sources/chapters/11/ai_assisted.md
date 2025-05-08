# AI Assisted Development

AI tools like GitHub Copilot[^1] can greatly enhance productivity, but effective use requires a few fundamental practices. The following axioms are essential for reliable and efficient AI-assisted coding.

## Axioms for Effective AI-Assisted Coding

1. **Preserve Essential Context**
   - Record important prompts, code snippets, and decisions outside the AI session (e.g., in comments or project notes), since session context is not persistent across restarts or between editor windows.

2. **Engineer Explicit Prompts**
   - Formulate clear, specific prompts to guide the AI toward relevant and accurate suggestions.

     | Vague Prompt         | Clear, Specific Prompt                                            |
     |----------------------|-------------------------------------------------------------------|
     | Write a function.    | Write a Python function that takes a list of numbers and returns the average. |

3. **Independently Verify AI Output**
   - Critically review all AI-generated code for correctness, security, and adherence to project standards before accepting or merging it.
   - Remember: Copilot can help you write tests, but cannot run them. Always run and check yourself.

Each of these axioms is fundamental and cannot be derived from the others. By following them, you ensure effective and reliable use of AI in your coding workflow.

## How to Save Your AI Session Context

Since chat and prompt history in VS Code (and similar environments) can be lost when you close a window, change workspaces, update extensions, or restart your machine, it is important to proactively save essential context.

**Recommended Practice:**  
After a productive session with GitHub Copilot, ask the AI to summarize the key context, prompts, and decisions from your session. Save this summary in a file named `COPILOT_CONTEXT.md` (or another descriptive name) in your project directory.

This way, you can easily recover your working context after a restart or when switching between environments, ensuring continuity and minimizing the risk of losing important information.

> **Example:**  
> - At the end of your session, prompt:  
>   “Summarize the key context and decisions from this session for future reference.”
> - Save the AI’s summary in `COPILOT_CONTEXT.md`.

By following this practice, you make your workflow more robust and resilient to interruptions or environment changes. This workflow helps ensure you never lose important context, even if your environment changes.

## How to Recover Your AI Session Context

When you restart your machine, reopen VS Code, or switch workspaces, you can quickly recover your previous working context by referring to the `COPILOT_CONTEXT.md` file (or your chosen context file) in your project directory.

**Recommended Steps:**
1. Open `COPILOT_CONTEXT.md` in your editor.
2. Review the summarized key context, prompts, and decisions from your previous session.
3. In your AI chat or prompt, simply say:  
   “Recover the context from `COPILOT_CONTEXT.md`.”
4. Continue your work, updating `COPILOT_CONTEXT.md` as your session progresses.

By following this process, you can efficiently resume your workflow with minimal loss of continuity, even after interruptions or environment changes.

## How to Change Context During a Session

If your goals, requirements, or focus change during an ongoing session, or if you switch to a different file or module, clearly inform the AI assistant of the new context. Many AI assistants, including GitHub Copilot, use the currently open file as a primary source of context for suggestions. To avoid confusion and ensure relevant assistance, be explicit about the change. For example:

> “I am now switching to `utils.py`. Please disregard the previous context.”

Or, if you want to keep some previous context but add new information:

> “In addition to the previous context, now consider that I am working on a new feature in `main.py`.”

Being clear about context changes and the current file helps the AI provide more accurate and relevant suggestions as your work evolves.

For further tips or more detailed guidance, feel free to ask GitHub Copilot directly as you work. This section is intentionally kept simple to encourage direct engagement with AI assistants for further guidance.

[^1]: We say simply "GitHub Copilot" to mean "GitHub Copilot or another AI assistant" for brevity.