# AI Assisted Development

AI tools like GitHub Copilot[^1] can greatly enhance productivity, but effective use requires a few fundamental practices. The following practices are essential for reliable and efficient AI-assisted coding.

## Core Rules for Effective AI-Assisted Coding

1. **Preserve Essential Context**
   - Record important prompts, code snippets, and decisions outside the AI session (e.g., in comments or project notes), since session context is not persistent across restarts or between editor windows.

2. **Engineer Explicit Instructions**
   - Formulate clear, specific instructions[^2] to guide the AI toward relevant and accurate suggestions.

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
>   “Summarize the context of this session to ensure the continuity of this chat for the next session.”
> - Save the AI’s summary in `COPILOT_CONTEXT.md`.

By following this practice, you make your workflow more robust and resilient to interruptions or environment changes. This workflow helps ensure you never lose important context, even if your environment changes.

## How to Recover Your AI Session Context

To resume work after a restart or interruption, use the `COPILOT_CONTEXT.md` file (or another descriptive name) in your project directory to restore your working context.

**Recommended Practice:**  
1. Open the `COPILOT_CONTEXT.md` file.  
2. Review the summarized key context, instructions, and decisions from your previous session.  
3. Prompt the AI:  
   > “Recover the context from `COPILOT_CONTEXT.md` to ensure the continuity of this chat.”

By following this process, you can quickly restore your workflow with minimal loss of continuity, even after interruptions or environment changes.

## How to Change Context During a Session

If your goals, requirements, or focus change during an ongoing session, or if you switch to a different file or module, clearly inform the AI assistant of the new context. Many AI assistants, including GitHub Copilot, use the currently open file as a primary source of context for suggestions. To avoid confusion and ensure relevant assistance, be explicit about the change. For example:

> “I am now switching to `utils.py`. Please disregard the previous context.”

Or, if you want to keep some previous context but add new information:

> “In addition to the previous context, now consider that I am working on a new feature in `main.py`.”

```{tip}
If a file or task is no longer relevant to your current focus, consider closing it to avoid distractions and maintain a clear working context. In addition, pay special attention to the **current file**, as AI assistants like GitHub Copilot often treat it as a primary source of context for generating suggestions.
```

Being clear about context changes and the current file helps the AI provide more accurate and relevant suggestions as your work evolves.

For further tips or more detailed guidance, feel free to ask GitHub Copilot directly as you work. This section is intentionally kept simple to encourage direct engagement with AI assistants for further guidance.

## Refining Practices and Terminology

This chapter itself demonstrates how to refine practices and terminology collaboratively with an AI assistant. Here's how the process unfolded about the first section above.[^3]

> **Legend:**  
> - 🧑‍💻 Actions I took during the process.  
> - 🤖 Contributions made by the AI assistant.  

1. **Start with an Initial Proposal:**  
   - 🧑‍💻 I prompted the AI to propose general practices for effective AI-assisted coding wihout any specifics.  
   - 🤖 The AI generated a list of five practices, including ideas like "managing session context" and "reviewing AI-generated code."

2. **Simplify and Structure:**  
   - 🧑‍💻 I asked the AI to simplify the proposed practices into a smaller, more fundamental set of principles. To guide this process, I introduced the term "axiomatic" to emphasize the need for foundational and independent rules.  
   - 🤖 The AI suggested combining the practices into three "axioms," which were:  
     1. Preserve Essential Context  
     2. Engineer Explicit Instructions  
     3. Independently Verify AI Output  
   - 💡 **Tip:** Thoughtful word choice, like starting with "axiomatic," can significantly enhance clarity and focus during refinement. Choose terms that convey your intent precisely and minimize the need for additional explanation.

3. **Iterate and Refine:**  
   - 🧑‍💻 I reviewed the "axioms" and realized that while the term "axiomatic" effectively conveyed the foundational nature of the rules, it might feel too formal or mathematical for some readers. I consulted the AI to refine the terminology further.  
   - 🤖 The AI suggested replacing "axioms" with "Core Rules" (including other options) to make the language more familiar and accessible. It also helped rephrase specific rules for clarity and usability.  
     - **Example:** The AI suggested clarifying "Preserve Context" as "Save key prompts and decisions in project notes to ensure continuity."  
   - 💡 **Tip:** Refinement is an iterative process. Be open to revisiting terminology and structure to ensure they resonate with your audience while maintaining precision.

## Final Note[^4] 

AI-assisted development is a rapidly evolving field, and the practices outlined in this chapter are designed to help you make the most of current tools like GitHub Copilot. However, as AI tools and development environments continue to improve, it’s important to remain adaptable while asserting your preferences and goals without compromising easily.

The collaborative process described in this chapter—generating ideas, simplifying them into actionable principles, and iterating for clarity—can be applied not only to AI-assisted coding but also to other areas of your work. By combining thoughtful human input with the capabilities of AI, you can create workflows that are both efficient and resilient.

Finally, remember that while AI can assist with many aspects of development, your judgment and expertise remain essential. Use AI as a tool to enhance your productivity, but always verify its output and ensure it aligns with your goals and standards.

By staying engaged, adaptable, and assertive in your preferences, you can continue to refine your practices and make the most of AI-assisted development as the field evolves.

```{note}
The practices and limitations described in this chapter are based on the status of AI tools (such as GPT-4 or GPT-4.1) and Visual Studio Code as of 1.100. Capabilities and behaviors of AI assistants and editors may change in future versions.
```

[^1]: We say simply "GitHub Copilot" to mean "GitHub Copilot or another AI assistant" for brevity.

[^2]: In the context of AI, an "instruction" is often referred to as a "prompt" and can also mean a question or request given to the AI assistant to guide its response.

[^3]: This process primarily illustrates a refinement story about "writing" rather than "coding." However, the importance of collaboration, based on clear and non-confusing communication, applies equally to both contexts. 

[^4]: This section was initially generated by GitHub Copilot and refined collaboratively to emphasize the importance of asserting human preferences and goals **"without compromising easily"**.