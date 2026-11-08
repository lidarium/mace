# Privacy Policy for OmniMarketer (Mace)

**Version 1.2 — Last Updated:** October 2026

OmniMarketer ("Mace", "we", "our", or "us") is committed to protecting your privacy. This Privacy Policy explains how your information is collected, used, and stored when you use our desktop application.

## 1. Local-First Architecture
OmniMarketer is built with a local-first, privacy-centric architecture. By default, the application runs entirely on your local machine. 

## 2. Information We Collect and Store Locally
When you use OmniMarketer, certain data is stored locally on your device (`~/Library/Application Support/Mace` on macOS):
- **Authentication Tokens:** OAuth tokens for platforms like Google and Meta are stored locally and encrypted using an AES symmetric key.
- **Application Logs & Crash Reports:** Logs of backend operations and crash traces are stored locally to help you troubleshoot.
- **Application Metrics:** Basic usage metrics (e.g., app starts, campaigns deployed) are recorded in local JSON files.

**None of this data is automatically transmitted to us or any third party.** Crash
diagnostics are written to local files and stay on your device unless you
separately opt in to crash reporting, which is described in §3.1.

## 3. Information Transmitted to Third Parties
The application connects directly to third-party services you authorize to perform its core functions. It does not send usage analytics, advertising identifiers or behavioural telemetry to its developers. The single exception is opt-in crash reporting, described in §3.1.

### 3.1 Opt-in crash reporting (Sentry) — off by default
Crash reporting is **off until you turn it on**. It is presented as its own
consent request at first launch and can be changed at any time under
Settings → Privacy, where declining it applies immediately.

If — and only if — you accept, OmniMarketer sends diagnostics to Sentry
(functivate Inc., GDPR-compliant processor, EU data region). What is sent:
the error message and stack trace, the app version, the release channel
(packaged vs. development), and session-health signals such as app starts and
clean-shutdown markers. No account identifier, no email address, no campaign
content, no prompt text, no API keys and no OAuth credentials are included.

**Legal basis:** your consent, given through the dialog described above and
withdrawable at any time (GDPR Art. 6(1)(a) / DPDP Act §6(3)).
**Retention:** 30 days in our Sentry project, after which events are deleted.
**Processor:** Sentry is an independent controller for its infrastructure and a
processor for this data; no personal data beyond the fields above is forwarded.
**Withdrawal:** Settings → Privacy → toggle crash reporting off. This stops
reporting immediately and clears the pending queue; it does not delete events
already transmitted, which age out within the retention window above.

If you decline, nothing is sent. The application is fully functional without it:
crash traces are still written to local files on your machine for your own use.

- **LLM Providers (e.g., OpenAI, Anthropic):** When you use the AI Agent or No-Text Creative Pipeline, prompts and image context are sent directly to the LLM APIs you have configured.
- **Ad Networks (Google Ads, Meta Ads):** Campaign data and OAuth tokens are transmitted to Google and Meta when you authorize deployments.
- **Scraping Providers:** If configured, competitor URLs are sent to third-party scraping APIs (e.g., Apify, Bright Data).
- **Release Feed (Cloudflare R2):** The auto-updater contacts the public release
  bucket to check for new versions. This transmits your IP address, application
  version, operating system version, and a download request. The bucket is
  operated by Cloudflare under a data processing agreement.
- **Download mirrors:** The application is primarily distributed from
  `https://lidarium.com`, and may also be offered on third-party mirrors. When
  you download from a mirror, that mirror's operator receives your IP address and
  download request, and their logging is outside our control. Mirrors are not
  authoritative; see §5 on verifying what you download.

## 4. Availability of Third-Party Services

The Application depends on services operated by third parties — LLM providers,
advertising networks, scraping providers, and our own release and reasoning
infrastructure. **These are provided strictly as offered by their respective
operators, under those operators' own terms of service, and they are outside our
control.**

You acknowledge that:

- These services **may become unavailable, degraded, rate-limited, suspended, or
  discontinued at any time**, without notice, whether by the operator's choice or
  by fault.
- **No service level, uptime, availability, or support commitment is offered** for
  any third-party service. Where an operator offers its own service levels, those
  apply to that operator and not to us.
- Interruption of a third-party service may interrupt the Application's
  server-assisted features. Local functionality continues to work; the outcome of
  an interrupted deployment or generation is not guaranteed and may need to be
  repeated.
- Our own infrastructure carries **no service level agreement**, and none may be
  assumed. This applies to the free tier and to paid tiers alike.

All data processing by third parties remains subject to the disclosures in §3.
We do not warrant the availability, accuracy, or policies of any third party.

## 5. User Control and Data Deletion
You retain full control over your data. You can delete all application data, logs, and encrypted credentials at any time by navigating to **Settings > System & Data > Delete All Data** within the application.

## 6. Closed Source: What You Can and Cannot Verify

OmniMarketer is **fully closed-source proprietary software**. No source code is
distributed to anyone — not under the free tier, not under a commercial licence,
and not on request. Section 3 of the End-User License Agreement states this
explicitly.

**What you cannot verify.** Because the source is not available, you cannot audit
the application's code to confirm that this privacy policy is accurate. You are
relying on the commitments below rather than on code you can read. We state this
plainly rather than imply an auditability we do not offer.

**What you can verify.**

- **The dependency list is complete.** Every third-party package the application
  links against, with its licence, is shipped inside the application and is
  viewable under Settings → Legal → Third-Party Notices. You can inspect what
  the application actually depends on, and check each licence independently.
- **Updates are genuinely from us.** Each release artifact carries a detached
  Ed25519 signature. The verification key is embedded in the application, and
  the application **refuses to install an update whose signature does not
  verify** — it fails closed rather than installing an unverified artifact.
- **Downloads are intact.** A SHA-512 checksum is published alongside every
  artifact, so you can confirm the file you downloaded was not altered in
  transit.
- **Data deletion is real.** Settings → System & Data → Delete All Data removes
  locally stored credentials, logs, crash reports, metrics, and the licence
  consent record. You can confirm the deletion by inspecting the application
  data directory afterwards.

**Why the source is closed.** Our advertising methodology — the prompt structure
and reasoning pipeline — is the product, and its protection depends on it not
being published. Trade-secret protection ends permanently at the moment of
publication, and it cannot be recovered by any licence. This applies to every
tier; there is no source-available or "open core" edition.

**What this does not change.** It does not change what is collected, stored, or
transmitted. Sections 1 through 4 describe the actual data behaviour and are
unaffected by the licensing model.

## 7. Data Controller
The Data Fiduciary for the purposes of this policy and of the Digital Personal
Data Protection Act, 2023 is **M/s TERALIDARIUM WORKS**, an Udyam-registered
sole proprietorship firm existing under the laws of India — the same entity
identified in the End-User License Agreement (Section "The developer"), operating
the "OmniMarketer" and "Lidarium" projects at https://lidarium.com.

The Udyam registration certificate, the name of the sole proprietor, and the
registered office address are held privately and are available on written request
for the purpose of legal notice or a dispute.

**Contact:** privacy@lidarium.com

## 8. Grievance Officer
In accordance with the Information Technology Act, 2000 and the Information
Technology (Intermediary Guidelines and Digital Media Ethics Code) Rules, 2021,
and with the Digital Personal Data Protection Act, 2023:

- **Contact:** legal@lidarium.com
- **Response time:** acknowledgement within 24 hours, resolution within 30 days
- **Escalation:** if unresolved, you may escalate under the grievance redressal
  mechanism of the Digital Personal Data Protection Act, 2023.

Complaints accepted: access, correction, erasure, consent withdrawal, and any
objection to our processing of your personal data.

No individual officer is named in this policy. Grievances are handled by
**M/s TERALIDARIUM WORKS** through the address above. The Udyam registration
certificate and the sole proprietor's name are held privately and disclosed on
written request for the purpose of legal notice or a dispute, as described in §7.

## 9. Changes to this Policy
We may update this Privacy Policy from time to time. Any change that expands what
we collect will be accompanied by a new consent prompt in the application — you
will not be asked to accept expanded collection silently. You may withdraw
consent at any time under Settings → Privacy.

The current version always ships with the application and is viewable under
Settings → Legal.
