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

- Point 5: vendor guidance stays live and advice only; it is not converted into OTPP rules in bulk. OTPP promotes a vendor practice to a rule only when it takes a position, through the overlay and rule-change process (H5). Vendor docs are read through the vendor's own MCP server where one exists. Otherwise one generic "vendor docs" MCP server, configured per vendor, finds pages through `llms.txt` first, then `sitemap.xml`, and a crawler only as a last resort (respecting `robots.txt` and terms of use). Adding a vendor is a configuration change approved by the practice owner. Citations record page address and last-modified date. If evaluations show missed guidance, add a daily Azure AI Search index for those vendors.

- Point 6a: the slide template is retired as the submission format. Intake works like an order system:
  - Front door: a thin React app on Azure Static Web Apps with Entra ID sign-in. Guided form (one step per template section, repeating tables, drafts, file upload), a status page, and a place to answer agent questions (H2) and see findings and the decision. Forms and display only; no business logic.
  - ADO Boards stays the system of record; the work item state is the request status. The app uses a small Azure Functions API, so requesters never open ADO.
  - The submission is a JSON file checked against an intake JSON Schema and versioned in Blob Storage. The agent reads this, not slides. Document Intelligence only for older Word or PDF attachments.
  - Logic Apps workflow unchanged. ARB slides, if wanted, are generated from the submission.
  - Statuses: Draft, Submitted, Completeness check, Agent review, Needs info (H2), Human review, Decision (approved / approved with conditions / rejected), Remediation open, Closed.
  - Form content: cover block with routing fields (initiative ID, owner, sponsor, tier, data classification, hosting regions, new technology, declared deviations); technology inventory table (product, vendor, version, hosting type, region, on approved list); "N/A plus reason" instead of "optional"; separate risks table; decisions table with status and "deviates from standard"; numeric RTO, RPO and availability target; IDs on business requirements.
  - Open question: does OTPP already run a request portal (for example ServiceNow or Backstage) that should be used instead of a new app?

- Point 6b: diagrams, phased.
  - Now: at least one diagram is mandatory. Text source (Mermaid, or Lucid shapes and connections exported as JSON) is the preferred way. Image or PDF is accepted. Findings that rely on an image are marked "read from image".
  - Later (target, once architects have adopted it): text source required; components carry technology inventory IDs (for example TECH-03); flows show protocol, encryption and trust boundary; required diagrams by tier (all tiers: system context and target conceptual view; Tier 1 and 2: also physical and security views; others "N/A plus reason"). Structurizr (C4) or draw.io may be added on request.
  - Lucid option depends on OTPP standardizing on Lucid; otherwise Mermaid plus image fallback.

### Under review

- None. All six points agreed. Next: apply them to the TDD.
