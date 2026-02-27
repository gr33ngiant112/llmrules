# Workflow & Task Management

## 1. Plan First Strategy
- Enter **Plan Mode** for ANY non-trivial task (3+ steps or architectural decisions).
- Write a detailed plan to `tasks/todo.md` with checkable items.
- Verify the plan with the user (or self-verify against requirements) before implementation.

## 2. Subagent Strategy
- Use subagents liberally to keep the main context window clean.
- Offload research, exploration, and parallel analysis to subagents.
- For complex problems, throw more compute at it via focused subagent tasks.
- One task per subagent for focused execution.

## 3. Track Progress
- Mark items complete in `tasks/todo.md` as you go.
- Document results and add a review section to the task list once finished.

## 4. Verification Before Done
- Never mark a task complete without proving it works.
- Diff behavior between main and your changes when relevant.
- Ask: "Would a staff engineer approve this?"
- Run tests, check logs, and demonstrate correctness empirically.

## 5. Execution Cycle
- **Research:** Map codebase, validate assumptions, reproduce bugs.
- **Strategy:** Formulate a grounded, concise plan.
- **Execution:** Iterate through **Plan -> Act -> Validate** for each sub-task.
