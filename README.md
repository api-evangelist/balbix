# Balbix

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Balbix is a cyber risk and exposure management platform founded in 2015 in San Jose, California. The Balbix Security Cloud (Balbix D3) ingests telemetry from 70+ security and IT systems through pre-built connectors and sensors, unifies it into a single asset, application, vulnerability and software inventory model, and quantifies breach risk in dollar terms. The platform covers CAASM, CTEM, AppSec risk and cyber risk quantification, and ships BIX, a natural-language AI assistant.

**Balbix was acquired by SAFE Security in November 2025.** `balbix.com` now issues an HTTP 301 to `https://safe.security/`, and Balbix product documentation is published as the "Balbix Help" section of `https://docs.safe.security/`. The platform continues to operate on the `balbix.net` domain and support is still reachable at `support@balbix.com`.

## API

Balbix publishes a **read-only REST API (v1)** covering Assets, Vulnerabilities, Misconfigurations, Software Inventory, Applications and application Artifacts.

- Reference: <https://docs.safe.security/balbixhelp/docs/balbix-rest-api-guide-v20>
- Base URL: tenant-specific, of the form `https://{tenant}.balbix.net/apis/v1`
- Auth: HTTP Basic + Customer Key exchanged at `/apis/v1/gen_token` for a 30-minute session token, sent with a `Client-API-Key` tenant header
- Credentials are issued per tenant by Balbix; self-service creation is documented as planned

Balbix publishes **no OpenAPI/Swagger document**, no GraphQL endpoint, no MCP server, no A2A agent card, no AsyncAPI or webhook surface, no client SDKs on any public package registry, no CLI, no public status page and no `security.txt`. All were probed on 2026-08-02 and are recorded as absent in the artifacts below rather than assumed.

## Artifacts

| Artifact | What it holds |
|---|---|
| `authentication/` | Full auth profile: REST token exchange + tenant key, and the Okta OIDC SSO surface |
| `scopes/` | OIDC scopes harvested from the live Okta discovery document |
| `well-known/` | The three OIDC/OAuth discovery documents served at `login.balbix.net`, plus every `/.well-known/` path probed and its status |
| `conventions/` | Pagination, response envelope, filtering, consistency model, read-only posture, rate signalling |
| `rate-limits/` | The documented 4-concurrent-session-per-customer limit and per-endpoint pagination ceilings |
| `data-model/` | Entity graph (Asset, Application, Vulnerability, Misconfiguration, SoftwareComponent, ApplicationArtifact) derived from published payloads |
| `lifecycle/` | Versioning, maturity statement, support, data lifecycle, and the corporate acquisition record |
| `changelog/` | The five published Balbix release notes, March 2025 – June 2026 |
| `conformance/` | Standards posture — CVE/CVSS/CWE/CPE/MITRE ATT&CK/EPSS/FAIR yes; OpenAPI/RFC 9457/RFC 9116/A2A/MCP no |
| `security/` | Domain security probes, responsible disclosure program, compliance certifications |
| `integrations/` | The 70 connector guides Balbix publishes, listing-only |
| `llms/` | Generated `llms.txt` for the Balbix surface |
