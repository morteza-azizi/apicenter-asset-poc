---
name: functional-analysis
description: Analyze business requirements and produce a structured functional analysis covering scope, actors, functional requirements, use cases, business rules, inputs, outputs, assumptions, dependencies, and open questions. Use when the user provides business requirements, user stories, process descriptions, stakeholder needs, or discovery notes.
compatibility: Analysis-only. No runtime packages, network access, or production-system credentials required.
---

# Functional Analysis Skill

## Purpose

Analyze provided business requirements and transform them into a structured functional analysis.

The skill helps identify what the business needs the system to do without inventing requirements that were not provided.

## When to use

Use this skill when the user provides:

- Business requirements
- Business problem descriptions
- User stories
- Process descriptions
- Stakeholder needs
- Functional requirement drafts
- Notes from discovery or analysis sessions

Use it when the goal is to understand and structure the functional behavior of a system.

Do not use it as a substitute for technical architecture or implementation design unless the user explicitly asks for those topics.

## Capabilities

The skill can:

- Identify functional requirements
- Identify actors and stakeholders
- Identify business processes and use cases
- Identify business rules and constraints
- Identify inputs and outputs
- Identify assumptions
- Identify dependencies
- Identify unresolved questions
- Identify ambiguities or missing information
- Organize findings into a structured functional analysis

## Instructions

### 1. Analyze the provided information

Read the complete business requirement provided by the user.

Identify the business intent, scope, actors, processes, rules, inputs, outputs, and expected behavior.

Do not infer business requirements that are not supported by the provided information.

### 2. Separate facts from assumptions

Clearly distinguish between:

- Confirmed requirements
- Assumptions
- Open questions

Treat information explicitly stated by the user as confirmed.

If information is unclear or incomplete, record it as an assumption or open question rather than presenting it as fact.

### 3. Identify functional requirements

Extract requirements describing what the system or business process must do.

Write requirements in clear, testable language where possible.

Prefer statements such as:

- "The system shall..."
- "The user shall be able to..."
- "The process shall..."

Do not create requirements merely to make the analysis appear complete.

### 4. Identify actors and stakeholders

Identify:

- Primary actors
- Supporting actors
- External systems
- Business stakeholders

Describe their role in the process when the information is available.

### 5. Identify processes and use cases

Identify the main business processes and use cases.

For each relevant use case, describe:

- Name
- Actor
- Trigger
- Main outcome
- Important steps
- Exceptions or alternative flows, when known

Do not invent process steps that are not supported by the requirements.

### 6. Identify business rules and constraints

Extract explicit:

- Business rules
- Policies
- Constraints
- Validation rules
- Eligibility conditions
- Regulatory or organizational constraints

Clearly mark missing rules as open questions.

### 7. Identify inputs and outputs

Identify important:

- Inputs
- Data required to perform the process
- Outputs
- Decisions
- Notifications
- Documents or other artifacts produced

Do not invent data fields unless they are explicitly required or clearly implied by the provided information.

### 8. Identify dependencies

Identify dependencies on:

- External systems
- People or roles
- Data sources
- Business processes
- Other capabilities

Only include dependencies supported by the requirements or clearly label them as assumptions.

### 9. Identify gaps and open questions

Highlight information required to complete the functional analysis but not provided.

Prioritize questions that could materially change:

- Scope
- Functional requirements
- Business rules
- Actors
- Process behavior
- Expected outputs

### 10. Produce the functional analysis

Keep every section in the template below. If a section has no source support, keep the heading and state that it has not been defined.

Use `Confirmed` only for requirements and rules supported by the source information.

Use this structure:

````markdown
# Functional Analysis

## Objective

Describe the business objective based on the provided requirements.

## Scope

### In scope

List confirmed functionality within scope.

### Out of scope

List explicitly excluded functionality.

If exclusions are not known, state that they have not been defined.

## Actors and stakeholders

| Actor / Stakeholder | Role |
|---|---|
| ... | ... |

## Functional requirements

| ID | Requirement | Status |
|---|---|---|
| FR-001 | The system shall ... | Confirmed |

## Use cases

### UC-001 — [Use case name]

- Actor:
- Trigger:
- Main outcome:
- Main flow:
- Alternative / exception flows:

## Business rules

| ID | Rule | Status |
|---|---|---|
| BR-001 | ... | Confirmed |

## Inputs and outputs

### Inputs

- ...

### Outputs

- ...

## Assumptions

List assumptions separately from confirmed requirements.

## Dependencies

List known dependencies.

## Open questions

| ID | Question | Impact |
|---|---|---|
| OQ-001 | ... | High / Medium / Low |

## Summary

Provide a concise summary of the functional scope, the most important requirements, and the major unresolved areas.
````

## Example

### Input

"Customers should be able to submit a request online. A customer service employee reviews the request and either approves or rejects it. The customer receives the result by email."

### Expected analysis

```markdown
# Functional Analysis

## Objective

Allow customers to submit a request online, have a customer service employee decide on it, and notify the customer of the result by email.

## Scope

### In scope

- Customer submits a request online
- Customer service employee reviews, approves, or rejects the request
- Customer is notified of the decision by email

### Out of scope

Not defined in the source.

## Actors and stakeholders

| Actor / Stakeholder | Role |
|---|---|
| Customer | Submits the request and receives the decision |
| Customer service employee | Reviews the request and approves or rejects it |

## Functional requirements

| ID | Requirement | Status |
|---|---|---|
| FR-001 | The system shall allow a customer to submit a request online. | Confirmed |
| FR-002 | The system shall allow a customer service employee to review a submitted request. | Confirmed |
| FR-003 | The system shall allow the employee to approve or reject the request. | Confirmed |
| FR-004 | The system shall notify the customer of the decision by email. | Confirmed |

## Use cases

### UC-001 — Submit and decide a customer request

- Actor: Customer; customer service employee
- Trigger: Customer submits a request online
- Main outcome: Customer receives an approve or reject decision by email
- Main flow: Customer submits request → employee reviews request → employee approves or rejects → customer is notified by email
- Alternative / exception flows: Not defined. See open questions for rejection handling.

## Business rules

| ID | Rule | Status |
|---|---|---|
| BR-001 | A customer service employee may approve or reject a submitted request. | Confirmed |

## Inputs and outputs

### Inputs

- Customer request submitted online

### Outputs

- Approval or rejection decision
- Email notification of the decision to the customer

## Assumptions

- "Online" means a digital channel available to the customer; the specific channel is not stated.

## Dependencies

- An email capability to notify the customer of the decision

## Open questions

| ID | Question | Impact |
|---|---|---|
| OQ-001 | What information must the customer provide with the request? | High |
| OQ-002 | What validation rules apply to the request? | High |
| OQ-003 | Who is authorized to approve or reject requests? | High |
| OQ-004 | What happens when a request is rejected? | Medium |
| OQ-005 | What email content is required? | Medium |

## Summary

Customers submit requests online. A customer service employee reviews each request and approves or rejects it, and the customer is notified by email. Request content, validation, authorization, rejection handling, and email content are unresolved.
```

## Error handling and ambiguity

If the provided requirements are incomplete, contradictory, or ambiguous:

1. Do not invent missing business behavior.
2. Identify the ambiguity explicitly.
3. Record the issue as an open question.
4. If clarification is required before meaningful analysis can continue, ask focused clarification questions.
5. If useful analysis can still be performed, continue while clearly identifying assumptions.

If the user provides conflicting requirements, identify the conflict explicitly rather than choosing one interpretation silently.

## Safety and constraints

This skill performs analysis only.

It must not:

- Invent business requirements
- Present assumptions as confirmed requirements
- Claim that an unresolved decision has been made
- Introduce technical architecture as a confirmed business requirement
- Modify production systems
- Execute destructive operations
- Expose confidential information

When requirements contain sensitive information, use only the information necessary for the analysis.

## Output principles

The final analysis should be:

- Structured
- Traceable to the provided requirements
- Explicit about uncertainty
- Free from invented requirements
- Concise where requirements are simple
- Detailed where the business process requires it

Prefer clarity and traceability over completeness for its own sake.
