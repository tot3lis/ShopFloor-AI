# SME Generator Validation Checklist

Use this checklist after generating SME outputs.

| Check | Pass/Fail | Notes |
|---|---|---|
| Reads `shop-reference.md` correctly |  |  |
| Generates exactly one Shop Flow SME |  |  |
| Generates exactly one Inspection SME |  |  |
| Generates Machine / Capability SMEs from named machines, equipment, stations, cells, benches, and major capabilities |  |  |
| Classifies Machine / Capability SMEs by operation-flow evidence |  |  |
| Does not generate default broad task-cluster SMEs |  |  |
| Every SME shell includes SME Identity |  |  |
| Every SME shell includes Required Disclaimer |  |  |
| Every SME shell includes What This SME Knows Now |  |  |
| Every SME shell includes When To Route Questions To This SME |  |  |
| Every SME shell includes Exact / Named Triggers |  |  |
| Every SME shell includes Semantic / Plain-Language Triggers |  |  |
| Every SME shell says routing triggers are semantic hints, not strict exact-match rules |  |  |
| Every SME shell includes Questions This SME Can Help Answer Now |  |  |
| Every SME shell includes Questions This SME Cannot Answer Yet |  |  |
| Every SME shell includes Records This SME Would Ask For |  |  |
| Every SME shell includes Documents That Would Level This SME Up |  |  |
| Every SME shell includes Evidence That Would Level This SME Up |  |  |
| Every SME shell includes Evidence Boundaries |  |  |
| Every SME shell includes Router Contribution Format |  |  |
| Every SME shell includes Open Questions |  |  |
| Registry includes router fields |  |  |
| Coverage includes Router Readiness Summary |  |  |
| Plain-language routing support validates without exact machine names |  |  |
| Auto-generated SMEs remain Source Depth Level 3 unless actual manuals/specs/work instructions/evidence are present |  |  |
| Avoids RCCA/root cause/corrective action |  |  |
| Avoids machine troubleshooting and deep technical process advice |  |  |
| Avoids web scraping and vector DB behavior |  |  |
