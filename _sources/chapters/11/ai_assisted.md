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

4. **Redirect Context When Necessary**
   - AI tools lack the ability to recognize when a course change is necessary. It is the responsibility of the developer to identify when the current approach is no longer effective or optimal and to redirect the AI accordingly.

```{note}
While each instance of redirecting context may seem small, the cumulative effect of such deliberate shifts can lead to what Thomas Kuhn described as a "Paradigm Shift"—a fundamental change in approach or perspective. In this sense, redirecting context is not just a practical action but a critical part of driving innovation and progress in development workflows.
```

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

## Using Pre-Prepared Context Files

To further simplify the process of saving and recovering context, developers can use pre-prepared context files for common tasks. These files are designed to align with typical workflows and the current capabilities of tools like VS Code and GitHub Copilot.

### How to Use Pre-Prepared Context Files

1. **Choose a Context File**:
   - Select a context file that matches your current task or goal. The following table provides an overview of the available pre-prepared context files and their purposes:

| **Context File**           | **Purpose**                     | **Availability** |
|----------------------------|----------------------------------|------------------|
| `APPLY_CONTEXT.md`         | Simplify applying suggestions.   | Available        |
| `DEBUGGING_CONTEXT.md`     | Assist with debugging tasks.     | Candidate        |
| `REFACTORING_CONTEXT.md`   | Guide code refactoring.          | Candidate        |
| `DOCUMENTATION_CONTEXT.md` | Improve documentation.           | Draft            |
| `TESTING_CONTEXT.md`       | Support writing tests.           | Candidate        |
| `NEW_FEATURE_CONTEXT.md`   | Assist with adding features.     | Candidate        |

> **Note:** For more details about each context file, open the file in your project directory.

2. **Remind the AI**:
   - At the start of your session, remind the AI of the selected context file. For example:
     > "Please remind yourself of the context from `COPILOT_APPLY_CONTEXT.md` for this session."

3. **Follow the Workflow**:
   - Use the practices outlined in the selected context file to guide your interactions with Copilot.

4. **Update as Needed**:
   - If your session involves unique requirements, you can modify the selected context file or create a new one for future use.

### Benefits of Pre-Prepared Context Files

1. **Simplicity**:
   - Quickly start a session by selecting a context file instead of creating one from scratch.
2. **Consistency**:
   - Ensure best practices are applied consistently across sessions and teams.
3. **Efficiency**:
   - Save time by using ready-to-use templates for common workflows.

By using pre-prepared context files, developers can streamline their workflows and focus on their tasks without being bogged down by repetitive setup steps.

## How to Change Context During a Session

If your goals, requirements, or focus change during an ongoing session, or if you realize that the current approach is no longer effective, it is your responsibility to redirect the AI. Many AI assistants, including GitHub Copilot, rely on the current file and prompts for context. To ensure relevant assistance, explicitly guide the AI toward the new direction.

This section focuses on **general context changes**, such as switching files or adding new information to the current session. For example:
> “I am now switching to `utils.py`. Please disregard the previous context.”

Or, if you want to keep some previous context but add new information:
> “In addition to the previous context, now consider that I am working on a new feature in `main.py`.”

```{tip}
If a file or task is no longer relevant to your current focus, consider closing it to avoid distractions and maintain a clear working context. In addition, pay special attention to the **current file**, because it is treated in a special way as mentioned above.
```

While this section addresses general context changes, **Rule 4: Redirect Context When Necessary** focuses on specific scenarios where deliberate redirection is required to address limitations in the AI's approach. These scenarios often arise unexpectedly and require the developer's judgment to intervene. For more details, see the section **"Necessary Context Redirection under Rule 4."**

Being clear about context changes and the current file helps the AI provide more accurate and relevant suggestions as your work evolves.

For further tips or more detailed guidance, feel free to ask GitHub Copilot directly as you work. This section is intentionally kept simple to encourage direct engagement with AI assistants for further guidance.

## Necessary Context Redirection under Rule 4

While general context changes are common during development, Rule 4 (**Redirect Context When Necessary**) addresses specific scenarios where the need for redirection often arises unexpectedly. AI tools, like GitHub Copilot, may persist in iterating on an ineffective approach, attempting to refine a solution even after repeated failures. 

In such cases, it is the developer's responsibility to recognize when the current approach is no longer viable and to intervene by redirecting the AI toward a more effective path. This process is not always anticipated in advance but requires awareness and judgment to identify when a shift in focus or strategy is necessary.

### Common Scenarios for Context Redirection

1. **Switching to Library Utilization**:
   - **When to Redirect**: If you start with a basic implementation (e.g., using plain HTML/CSS) but later realize that a library (e.g., D3.js) would be more efficient or powerful.
   - **How to Redirect**:
     - Ask the AI for recommendations on libraries that align with your goals. The AI often has a broader knowledge of available tools and can suggest candidates you might not be familiar with.
     - Once you’ve identified a suitable library, inform the AI about your choice and its purpose.
     - Provide relevant documentation or examples to guide the AI in generating solutions using the library.
   - **Example Prompts**:
     - To explore library options:  
       > "What JavaScript libraries are available for creating interactive data visualizations? Please suggest some options and briefly describe their strengths."
     - To redirect after choosing a library:  
       > "I want to switch to using D3.js for this task. Please disregard the previous plain HTML/CSS approach and focus on generating D3.js-based solutions."

2. **Introducing Unit Testing**:
   - **When to Redirect**: During development, if the AI struggles to handle complex code changes or repeatedly fails to make progress, it may be necessary to simplify the problem and verify the approach through unit testing or a minimal example. This redirection is required because the work is ongoing and cannot proceed effectively without intervention.
   - **How to Redirect**:
     - Clearly state the need to simplify the problem or focus on testing specific scenarios.
     - Suggest creating a simplified version of the code to verify the AI's understanding and approach.
     - Once the simplified code works as expected, ask the AI to apply the solution to the original, more complex code.
   - **Example Prompts**:
     - To focus on testing:  
       > "The current implementation is incomplete. Let’s write unit tests for the key scenarios to verify the logic before proceeding further."
     - To simplify a complex problem:  
       > "The current code is too complex for this change. Let’s create a simplified version of the function to verify the logic. Once it works, we’ll apply it to the original code."
     - To apply the simplified solution:  
       > "Now that the simplified version works, please use it as a reference to update the original, more complex code."

3. **Dividing and Ordering Focus**:
   - **When to Redirect**: If a task becomes too complex, it may be necessary to break it into smaller, more manageable parts and address them sequentially.
   - **How to Redirect**:
     - Define the specific subtask you want to focus on first.
     - Clearly communicate the order of priorities to the AI.
     - Example Prompt:  
       > "Let’s focus on implementing the data parsing logic first. Once that’s complete, we’ll move on to the visualization component."

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
   - 💡 **Note:** At this stage, Rule 4 (**Redirect Context When Necessary**) was not yet included. It was later identified as a missing principle during the refinement process, as described in Step 4.
   - 💡 **Tip:** Thoughtful word choice, like starting with "axiomatic," can significantly enhance clarity and focus during refinement. Choose terms that convey your intent precisely and minimize the need for additional explanation.

3. **Iterate and Refine:**  
   - 🧑‍💻 I reviewed the "axioms" and realized that while the term "axiomatic" effectively conveyed the foundational nature of the rules, it might feel too formal or mathematical for some readers. I consulted the AI to refine the terminology further.  
   - 🤖 The AI suggested replacing "axioms" with "Core Rules" (including other options) to make the language more familiar and accessible. It also helped rephrase specific rules for clarity and usability.  
     - **Example:** The AI suggested clarifying "Preserve Context" as "Save key prompts and decisions in project notes to ensure continuity."  
   - 💡 **Tip:** Refinement is an iterative process. Be open to revisiting terminology and structure to ensure they resonate with your audience while maintaining precision.

4. **Identify Missing Principles:**  
   - 🧑‍💻 While reviewing the initial three axioms, I realized that they did not address a critical limitation of AI tools: their inability to recognize when a course change is necessary.  
   - 🤖 The AI assisted in brainstorming how to address this gap, leading to the idea of a new rule focused on **redirecting context** during significant course changes.

5. **Add Rule 4:**  
   - 🧑‍💻 I added Rule 4, titled **"Redirect Context When Necessary,"** to address this gap. The rule emphasizes the developer's responsibility to identify when the current approach is no longer effective and to guide the AI accordingly.  
   - 🤖 The AI contributed actionable examples, such as updating prompts and providing additional context, to make the rule practical and easy to apply.

6. **Improve Readability:**  
   - 🧑‍💻 To make Rule 4 more engaging and relatable, I proposed a note referencing Thomas Kuhn's concept of a "Paradigm Shift" to help readers understand it more deeply.
   - 🤖 The AI suggested phrasing the note to connect the practical action of redirecting context with the broader philosophical idea of driving innovation and progress.  
   - 💡 **Tip:** Adding contextual notes or analogies can help readers connect abstract principles to real-world applications, making the content more memorable and impactful.

By following this process, the Core Rules evolved into a more comprehensive and balanced framework, addressing both the strengths and limitations of AI tools like GitHub Copilot.

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