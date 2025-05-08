## Session Summary

- **Axioms for Effective AI-Assisted Coding:**
  1. Preserve Essential Context: Save important instructions, code, and decisions outside the AI session, as session context is not persistent.
  2. Engineer Explicit Instructions: Use clear, specific instructions to guide the AI. (Footnote: In AI, an "instruction" is often called a "prompt" and can also mean a question or request.)
  3. Independently Verify AI Output: Always review AI-generated code for correctness and security. Copilot can help write tests, but cannot run them—always run and check tests yourself.

- **Session Context Management:**  
  - Save session context in a file like `COPILOT_CONTEXT.md` after each session.
  - Ask the AI to summarize key context and decisions for future reference.

- **Recovering Context:**  
  - To resume after a restart or interruption, open `COPILOT_CONTEXT.md`, review the summary, and instruct the AI to recover context from the file.

- **Changing Context During a Session:**  
  - When switching tasks, files, or modules, explicitly inform the AI of the new context.
  - Example:  
    - “I am now switching to `utils.py`. Please disregard the previous context.”
    - “In addition to the previous context, now consider that I am working on a new feature in `main.py`.”

- **Version Sensitivity:**  
  - Practices are based on the status of AI tools (GPT-4/GPT-4.1) and Visual Studio Code as of version 1.100. Capabilities may change in future versions.