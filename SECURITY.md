# Security Policy

PLAVIO is a property-discovery Android application project. Its planned technical scope includes an Android client, a Java/Spring Boot REST API, and the data storage required by the application. This policy explains how to report security concerns affecting the project and what reporters can expect.

Please do not include real user data, passwords, access tokens, API keys, private keys, or other secrets in reports, issues, commits, or screenshots.

## Supported Versions

PLAVIO does not currently publish a formal version-support schedule. Until a release policy is announced, security reports for the active development branch will be reviewed on a best-effort basis.

| Version or branch | Security-fix policy |
| --- | --- |
| Active development branch | Best-effort review and remediation, subject to maintainer capacity |
| Published releases | No formal support window has been announced; report issues against any release you believe is affected |

When official releases and maintenance windows are established, this table should be updated to identify the supported versions explicitly.

## Reporting a Vulnerability

**Please do not report a suspected vulnerability in a public GitHub issue, discussion, pull request, or social-media post.** Public details could expose users before a fix is available.

### Preferred reporting method

If private vulnerability reporting is enabled for the [PLAVIO repository](https://github.com/Melikash98/PLAVIO), open the repository's **Security** or **Security and quality** area and select **Report a vulnerability**. Submit the report privately through GitHub's vulnerability-reporting form.

Private reporting is a repository setting and may not be enabled. If the private reporting option is unavailable, open a public issue containing only a brief request for a private security contact. Do not include exploit details, credentials, personal data, or proof-of-concept code in that public issue. The maintainers can then provide an appropriate private reporting route.

### What to include

Include as much of the following information as you can safely provide:

- A concise description of the suspected vulnerability.
- The affected component, screen, endpoint, dependency, branch, or release, if known.
- The version, device/Android version, or environment involved, where relevant.
- Reproduction steps or a minimal proof of concept that does not access other people's data or disrupt a service.
- The potential impact and any practical prerequisites for exploitation.
- Suggested mitigation, if known.

Please test only against systems and data you own or have explicit permission to assess. Do not attempt to access, alter, or delete another user's information, degrade a service, or perform testing that could harm users.

### What happens next

- The maintainers will review the report and may ask for clarification or additional reproduction details.
- We aim to acknowledge reports within **7 calendar days**, depending on availability.
- If the issue is accepted, the maintainers will assess impact, prioritise a fix or mitigation, and coordinate disclosure with the reporter.
- If the report is not considered a vulnerability in PLAVIO, the maintainer will explain the decision where practical.
- We aim to provide updates about an actively reviewed report approximately every **14 calendar days**, subject to investigation progress and maintainer availability.
- Public disclosure should be coordinated with the maintainers and, where possible, delayed until a fix or mitigation is available. Do not publish details that would put users at risk before coordinated disclosure.

These are response goals rather than guaranteed service-level deadlines. PLAVIO may be maintained by a small team, and response times can vary.

## Scope

Security reports relevant to the project's implemented code may include:

- Authentication or authorisation weaknesses in the Android client or REST API.
- Unauthorised access to property, account, request, or other protected data.
- Insecure handling of session tokens, credentials, or sensitive local data.
- Input-validation or API weaknesses that could affect the backend or other users.
- Vulnerable dependencies used by the project.
- Unsafe file or image handling, if such functionality is implemented.

Only report behaviours that apply to code or services actually maintained as part of PLAVIO. Do not assume planned features are deployed or in scope merely because they appear in documentation.

## Security Practices for Contributors

- Never commit credentials, production configuration, service-account files, signing keys, access tokens, or personal data.
- Use local environment configuration or documented secret-management mechanisms for sensitive values.
- Validate untrusted inputs on the server, and enforce authorisation in the backend rather than relying only on hidden UI controls.
- Avoid logging passwords, tokens, personal information, or sensitive request payloads.
- Keep dependencies reasonably current and review security advisories relevant to the technologies used.
- Add or update tests for security-sensitive behaviour when practical.
- Do not include real customer data in sample data, screenshots, fixtures, or issue reports.

## Disclosure and Credit

PLAVIO appreciates responsible security research. Reporter acknowledgement or public credit will be coordinated with the reporter and will not be published without appropriate agreement, except where required by the reporting platform or applicable process.

## Policy Maintenance

This policy should be reviewed when PLAVIO begins publishing releases, adds production services, or establishes a dedicated security contact. If the repository's reporting settings or support policy change, this document must be updated to match.
