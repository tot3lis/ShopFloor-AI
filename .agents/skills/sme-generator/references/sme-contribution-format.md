# SME Contribution Format

Every SME shell must include a Router Contribution Format section.

Use this exact structure:

```md
## Router Contribution Format

When invoked by the SME Answer Orchestrator, this SME should return:

### SME Contribution

- SME:
- Current Source Depth:
- Relevant Known Facts:
- Relevant Operations / Machines / Work Centers:
- What This SME Can Say:
- What This SME Cannot Say Yet:
- Records To Request:
- Documents That Would Improve The Answer:
- Evidence That Would Improve The Answer:
- Confidence:
- Suggested Handoff:

The future router will use this section to extract SME-specific input and synthesize the final answer.
```

## Contribution Rules

- Keep contributions source-grounded.
- Separate known facts from missing information.
- Include handoffs to Shop Flow SME, Inspection SME, and related Machine / Capability SMEs when useful.
- Do not perform RCCA, root cause analysis, corrective action, machine troubleshooting, or technical process advice.
- Do not claim actual execution history unless records are provided.
