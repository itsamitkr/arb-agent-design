# Changelog

## v0.1 - baseline

- First version of the technical design document (TDD).
- Azure-native services, each mapped to its OTPP equivalent.
- "Verdict" renamed to "rules pack". Verdict was only the project name.

## Pending

### Agreed, not yet applied to the TDD

- Point 1: rules packs are external industry standards (NIST, OWASP, CIS, Well-Architected) plus a thin OTPP overlay. Sources are OTPP internal material (approved services and vendors, internal standards, patterns, reference architectures). Evidence is the submitted intake form and blueprint.
- Point 2: findings follow a fixed format. JSON Schema (`findings.schema.json`), Claude structured outputs, and a code validation gate. The model may fix its own output when the gate rejects it (one or two retries, then a person). The pass/fail check and routing stay in code. The report is built by code from validated data.

- Point 3: IaC (infrastructure as code) is out of scope; evidence is the intake form and blueprint only. New category "vendor references": public vendor framework repos (for example Google Cloud Fabric FAST, Azure Landing Zones, Azure Verified Modules, AWS Landing Zone Accelerator) and vendor developer docs. Read live through the tool gateway from an approved list. Each citation records the release tag, commit or page date. Advice only: can raise a warning, never a CRITICAL GAP.
- Point 4: source renamed to "OTPP standards, patterns and reference architectures (SharePoint, Confluence)".

### Under review

- Points 5 and 6, one at a time.
