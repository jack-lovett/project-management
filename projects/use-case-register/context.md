## \[meta]
```json
{
	"project": "Use Case Register"
	"last_updated": "2025-01-05",
	"status": "active",
	"url": "projects/use-case-register"
}
```

## \[goals]
- Define and publish assurance guidance for "Other Risk Domain" and rating descriptors.
- Stabilize Lists → Dataverse migration model (tables, keys, relationships).
- Reduce context drift by emitting change sets for tasks/todos weekly.

## \[scope_and_boundaries]
- In scope: Microsoft Lists, SharePoint, Power Apps (Dataverse), Power Automate flows.
- Out of scope: Non‑MS tooling, automated CI/CD (manual only).

## \[tasks]
```json
{
	"tasks": [
		{
			"id": "T-124",
			"title": "Define 'Other Risk Domain' guidance and rating descriptors",
			"status": "todo",
			"due": "2026-01-15",
			"tags": ["assurance", "risk", "guidance"]
		},
		{
			"id": "T-125",
			"title": "Map Lists fields to Dataverse schema",
			"status": "in-progress",
			"due": "2026-01-22",
			"tags": ["dataverse", "schema"]
		}
	]
}
```

## \[decisions]
```md
- 2025-01-05T12:00:00Z: Separate system prompts from project context; keep change sets in project context. _Reason:_ minimize copy‑paste, avoid duplication.
- 2025-12-22T12:00:00Z: Use three core lists (Register, Timeline, Assurances) before Dataverse migration.
```

## \[identified_risks]
```md
-   **Context drift** between Lists and Protocol docs. _Mitigation:_ weekly change sets + verification checks.
-   **Manual errors** due to copy‑paste. _Mitigation:_ use simple patch schema and checklist verification.
```

## \[artifacts_and_references]
```md
-   Diagrams: `diagrams/er-model.drawio`, `diagrams/workflow.pptx`
-   Guidance docs: `docs/assurance-guidance.md`
-   Lists JSON formatting: `formatting/uc-register-buttons.json`
-   Power Automate: `flows/auto-id-assign.md`, `flows/create-sharepoint-folder.md`
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ2NDYwMDk3Ml19
-->