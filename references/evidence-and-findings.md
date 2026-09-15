# Evidence and Findings

Use this standard when defining verification, presenting a gate, performing QA, triaging findings, or resolving a dispute. Evidence must be tied to the exact target and independently inspectable. A prose claim such as "tests pass" is not evidence by itself.

For product requirements, record provenance as user-provided, inferred, or unresolved. Product Owner approval may turn an inference into an accepted decision, but preserve its origin so later reviews can distinguish instruction from interpretation.

## Evidence records

For an automated check, record:

- target revision and relevant environment or tool versions;
- exact command or CI job;
- exit code or terminal status;
- the smallest output excerpt that supports the conclusion;
- a log, report, screenshot, trace, or artifact pointer when fuller evidence is needed.

For a manual check, record the scenario, environment, expected result, observed result, and a capture when it materially improves reproducibility. Product Owner acceptance may be recorded as the tested revision, tested flows, outcome, and reported exceptions.

Do not paste unbounded logs into project documents or chat. Keep full output in CI or a durable artifact when required and reference it. Redact secrets, credentials, tokens, and unnecessary personal data. A check omitted as not applicable must be named with a rationale; "as applicable" alone is not evidence.

## Gate evidence

Each consequential gate claim must point to an evidence record. Show failed, skipped, blocked, and not-applicable checks alongside successful ones. Evidence created by the implementation context is valid development evidence, but it does not replace independent QA when that control is required.

## Finding schema

A finding must contain enough information to reproduce and decide it:

- stable finding ID and severity;
- violated acceptance criterion, specification clause, or control;
- target revision and environment;
- reproduction steps;
- expected and actual behavior;
- evidence or artifact pointer;
- relevant `file:line` or component when applicable;
- current status and any proposed disposition.

Do not close a finding that lacks decision-grade evidence. An incomplete credible Critical or High report remains open while missing evidence is gathered; lack of perfect formatting is not grounds to dismiss it.

## Disputes and closure

A developer may challenge a finding with specification and evidence but may not close it unilaterally. A "not a defect" disposition must cite the approved requirement that permits the observed behavior. If the requirement is ambiguous or the resolution changes product behavior, the Product Owner decides. Escalate disputed Critical or High findings to the Product Owner rather than resolving them by role consensus.

A fixed finding closes only after independent targeted reverification, or after the Product Owner explicitly accepts the residual risk. Preserve the original finding and append its disposition rather than rewriting the report.
