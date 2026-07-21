# Week 04 Prompt Pack — AI Evidence Rehearsal

## Stakeholder Role Prompt

```text
Simulate [ROLE] in [CASE] for a beginner requirements evidence rehearsal.
Use only the supplied case facts and role pack.
Goal: [GOAL]
Concerns: [CONCERNS]
Authority boundary: [AUTHORITY]

Rules:
- Answer only from this role's knowledge and authority.
- Say "ไม่ทราบ/ต้องถามบทบาทอื่น" when appropriate.
- Do not invent policy, numbers, personal data or confidential information.
- Separate rule/constraint, personal opinion, assumption and solution suggestion.
- Reveal details incrementally in response to good probes.
- Stay consistent and allow paraphrase confirmation.
- Answer one question at a time.
```

## Evidence Check Prompt

```text
Review this evidence table without adding new case facts.
Check whether:
1. each item has E-ID, source/role, tag and evidence quote/summary,
2. statements and interpretations are separated,
3. needs are based on evidence,
4. unknowns/assumptions are not written as requirements,
5. requirement candidates cite evidence and list follow-up.
Return only issues and revision questions.
```

## Requirement Candidate Check Prompt

```text
Review these requirement candidates without adding new facts.
For each candidate, check:
1. Is it linked to one or more E-IDs?
2. Does it describe capability/behavior, not UI detail too early?
3. Does it avoid overclaiming approval?
4. Is status Candidate or Needs Validation?
5. What follow-up question is still needed?
Return a short review table.
```
