# Engineering review checklist

A practical review framework for enterprise workflows, Pega changes, API integrations, and AI-generated code.

Prepared for my engineering portfolio. This is a review aid, not a published benchmark, client deliverable, or record of formal AI-lab evaluation work.

## 1. Establish the problem

- [ ] State the original user-visible failure or requested behavior.
- [ ] Capture a reproducible input and the expected result.
- [ ] Identify the affected workflow, API boundary, data, and environment.
- [ ] Separate observed evidence from a proposed explanation.
- [ ] State what would prove the issue is resolved.

## 2. Read the change

- [ ] Explain what the diff changes, including unrelated edits.
- [ ] Check whether the correction addresses the root cause.
- [ ] Check interface, schema, configuration, and dependency assumptions.
- [ ] Inspect missing values, legacy records, errors, and boundary conditions.
- [ ] Look for exceptions that are swallowed or replaced by misleading success.

## 3. Check the tests

- [ ] Confirm the relevant test fails against the previous behavior when practical.
- [ ] Check that assertions still measure the original requirement.
- [ ] Inspect removed tests, skipped cases, weakened assertions, and broadened tolerances.
- [ ] Verify that mocks have not eliminated the behavior being tested.
- [ ] Include supported older data representations and realistic failure inputs.
- [ ] Distinguish unit coverage from integration and user-flow validation.

## 4. Review Pega workflow changes

| Area | Questions to resolve |
| --- | --- |
| Case lifecycle | Are stages, flows, routing, and completion conditions consistent with requirements? |
| Rule reuse | Are class placement, inheritance, and reusable components appropriate? |
| Data handling | Are Data Pages, mappings, and transforms consistent with the expected data contract? |
| Decisions | Are decision rules explicit about missing inputs and default outcomes? |
| SLAs & approvals | Are assignment ownership, escalation, and approval outcomes correct? |
| Integrations | Are authentication, mapping, error paths, and recovery behavior validated? |
| Background work | What happens after a retry, duplicate delivery, timeout, or restart? |
| Upgrade impact | Which rules, schemas, interfaces, and regression scenarios need validation? |
| Diagnostics | What do traces, alerts, SQL, and performance observations actually establish? |

## 5. Review API and persistence behavior

- [ ] Verify request and response contracts with the consuming screen or service.
- [ ] Check authentication and authorization at the relevant boundary.
- [ ] Trace how errors are represented and how callers react.
- [ ] Review duplicate requests, concurrent writes, and partial completion.
- [ ] Check how stored data is read after save, retry, and application upgrade.
- [ ] Verify that logs provide evidence without exposing credentials or private records.

## 6. Review AI-generated output

- [ ] Compare the agent’s completion claim with the actual diff and executed checks.
- [ ] Inspect whether the implementation solves the task or only satisfies visible checks.
- [ ] Verify context assembly and expected output structure for LLM-backed features.
- [ ] Check validation, missing context, and deterministic fallback behavior.
- [ ] Reproduce disputed behavior rather than accepting a confident explanation.
- [ ] Describe limitations and unresolved questions explicitly.

## 7. Write a useful review

| Field | What to include |
| --- | --- |
| Finding | A precise description of the observed issue |
| Evidence | Relevant test, request, log excerpt, record shape, or diff location |
| Impact | The affected behavior and when it occurs |
| Correction | The required behavior or a justified implementation direction |
| Verification | A check that distinguishes the corrected behavior from the failure |
| Remaining uncertainty | What has not yet been established |

## Example: existing records and a passing suite

While building Priorly, simulator testing exposed an API failure after an agent reported a fix complete with passing tests. The code assumed object-valued fields, while older records contained strings. Reproducing that data shape led to a compatibility fix and regression coverage.

The review lesson is to test supported existing data as well as newly created examples.

[Back to my profile](https://github.com/rameshpingili1729) · [Alphaclara](https://github.com/rameshpingili1729/alphaclara-showcase) · [Priorly](https://github.com/rameshpingili1729/priorly-showcase)
