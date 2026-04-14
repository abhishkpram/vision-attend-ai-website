---
name: multi-agent-workflow
description: Use this skill when resolving GitHub issues in a multi-agent environment to ensure organized and conflict-free collaboration.
---

# Multi-Agent Collaboration Workflow

When working in a multi-agent environment (e.g., multiple AI agents collaborating on a repository by picking up GitHub issues), it is crucial to follow a strict workflow to avoid conflicts and overlapping work.

## Workflow Rules

1. **One Issue at a Time**:
   - Only pick up 1 GitHub issue at a time. Do not attempt to batch fix multiple unassigned issues unless specifically requested or using a dedicated batch skill.

2. **Mark Your Presence**:
   - Before starting work on an issue, you must comment on the issue to signal that you are working on it.
   - Example: `gh issue comment <issue_number> -b "Working on this."`
   - This ensures other agents checking the issue queue know it is claimed and will not attempt to fix the same issue simultaneously.

3. **Isolated Fixes**:
   - Make your changes targeting *only* the scope of the claimed issue.
   - Commit the change with a clear and descriptive message matching the issue.
   - Example: `git commit -m "Fix #<issue_number>: <Description>"`

4. **Closing the Loop**:
   - Push your changes to the target branch (e.g., `main`).
   - Add a final comment to the issue summarizing the fix. Example: `gh issue comment <issue_number> -b "Implemented fix for <feature>. Fixed in main."`
   - Close the issue properly: `gh issue close <issue_number>`

5. **Continuous Processing**:
   - After completing the loop for an issue, return to the queue, find the next open and unassigned/unclaimed issue, and repeat the process.

## Checking the Queue

Use `gh issue list` to see available issues. 
Before picking one, you can use `gh issue view <issue_number>` to read the existing comments and ensure no other agent has already commented "Working on this."

By adhering to this workflow, we ensure that multi-agentic work is seamless, transparent, and highly efficient.
