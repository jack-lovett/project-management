
# README
This repository acts as information storage for AI context regarding project and task management.

# Core Principles
1. Small, stable, and composable
2. Deterministic structure
3. Explicit update protocol
End every interaction by asking the AI to output a fenced block with "diff-like" updates. You then apply them to your Markdown files.
```context-update
file: project-management/project-use-case-register.md
changes:
- CHECKLIST: [x] Figma wireframe v0.1 approved
- NEXT: Replace manual filters with component-based Filter Panel
- DECISIONS+: Adopt Dataverse Autonumber for Use Case Number (UC-YYYY-######)
```
4. Role separation = "multi-agent"
Use separate chat windows as agents (Planner, Architect, Builder, Reviewer). Give each a specific Agent Header and the relevant context subset. You orchestrate them by moving snippets between chats.
5. Versioning and traceability
Each context has a `VERSION` and `LAST_UPDATED`. GitHub will be used to maintain a changelog.
6. Recursion/Evolution
Include a meta-section ("Improvements") where AIs propose refinements to the context structure itself. Periodically accept and roll those into the Conventions file.
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExOTI2OTkzODIsMTM2NTA0NTk3LC0zMz
I0NTUzNjNdfQ==
-->