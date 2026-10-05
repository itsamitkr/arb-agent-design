# Changelog

## v0.1 - baseline

- First version of the technical design document (TDD).
- Azure-native services, each mapped to its OTPP equivalent.
- "Verdict" renamed to "rules pack". Verdict was only the project name.

## Pending

### Agreed, not yet applied to the TDD

- Point 1: rules packs are external industry standards (NIST, OWASP, CIS, Well-Architected) plus a thin OTPP overlay. Sources are OTPP internal material (approved services and vendors, internal standards, patterns, reference architectures). Evidence is the submitted intake form and blueprint.
- Point 2: findings follow a fixed format. JSON Schema (`findings.schema.json`), Claude structured outputs, and a code validation gate. The model may fix its own output when the gate rejects it (one or two retries, then a person). The pass/fail check and routing stay in code. The report is built by code from validated data.

### Under review

- Points 3 to 6, one at a time.
