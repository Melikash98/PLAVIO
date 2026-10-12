# Contributing to PLAVIO

Thank you for your interest in contributing to **PLAVIO**.

PLAVIO is a property-discovery Android application intended to help users explore properties, save listings, and submit the appropriate booking or property inquiry requests. The planned technical direction includes an Android client built with Java and XML, a Java/Spring Boot REST API, and persistent server-side data with local Android storage where appropriate.

This guide explains how the team should propose changes, work with branches, write code, test changes, and keep documentation reliable. Always follow the code and build configuration that actually exist in the repository; proposed technologies are not considered implemented until they are present in the source.

## 1. Project Scope

Contributions should support the user-facing Android application and its related data/API workflows, including:

- Property discovery, search, filters, and property details.
- Saved properties and account-related screens, where implemented.
- Stay booking requests and Rent/Buy inquiries, with distinct flows for each category.
- API integration, data models, local caching, and error handling.
- Accessibility, loading/skeleton states, empty states, and responsive layouts.
- Automated tests, documentation, and developer experience.

A separate web-based administration panel, payment processing, and financial settlement are outside the current scope unless the project scope is explicitly revised.

Do not describe planned features as completed functionality. In particular, submitting a request must not be represented as a confirmed booking.

## 2. Before You Start

1. Read `README.md` for the current project overview and setup instructions.
2. Check open Issues and Pull Requests to avoid duplicate work.
3. For a substantial change, open an Issue or discuss the proposal with the maintainers before implementing it.
4. Confirm that the proposed change fits the current scope and architecture.
5. Never commit production credentials, API keys, tokens, private user data, or local configuration files containing secrets.

If the repository does not yet contain a module or feature mentioned in the documentation, clarify the intended scope in an Issue instead of assuming it already exists.

## 3. Issue Guidelines

A useful Issue should describe:

- **Problem:** What is missing, incorrect, or difficult for the user or developer?
- **Expected outcome:** What should happen after the change?
- **Scope:** Which screen, user flow, API, data model, or documentation area is affected?
- **Acceptance criteria:** How can the team verify that the work is complete?
- **Evidence:** Screenshots, reproduction steps, logs with secrets removed, or example requests/responses where relevant.

Use a concise title and keep one Issue focused on one coherent change. Do not include passwords, access tokens, personal data, or other sensitive information in Issues.

## 4. Branching and Commit Messages

Create a separate branch for each feature, fix, or documentation change. Use descriptive names such as:

- `feature/property-search`
- `feature/saved-properties`
- `fix/request-validation`
- `docs/update-setup-guide`
- `test/listing-service`

Prefer clear commit messages in the Conventional Commits style:

- `feat(android): add property filter controls`
- `feat(api): add listing search endpoint`
- `fix(data): handle missing property images`
- `test(api): cover inquiry validation`
- `docs: clarify local setup`
- `refactor(android): extract property card component`

Use the relevant scope when it improves clarity. Keep commits focused and avoid mixing unrelated refactoring with feature work.

## 5. Pull Request Process

Before opening a Pull Request:

1. Sync your branch with the current target branch.
2. Run the available relevant checks and tests.
3. Review your own diff for accidental files, secrets, debug code, and unrelated changes.
4. Update documentation when behaviour, configuration, setup, or API contracts change.
5. Add screenshots or a short recording for visible UI changes, where useful.

A Pull Request should include:

- A clear summary of what changed and why.
- The related Issue, if one exists.
- Important design or implementation decisions.
- Tests run and their results.
- Screenshots for UI changes, where applicable.
- Known limitations or follow-up work.

Keep Pull Requests focused enough to review. Address review comments and resolve conflicts before merging. Do not merge changes that fail required checks or introduce undocumented breaking API changes.

## 6. Android Development Guidelines

For the Android client, follow the patterns and versions actually configured in the project. The intended direction is Java with native Android XML layouts; use the existing conventions rather than introducing a second UI stack without agreement from the maintainers.

### UI and UX

- Follow the PLAVIO design system and the supplied Figma specifications when available.
- Keep the visual language consistent: typography, colours, spacing, icons, imagery, and component states should be reused rather than independently reinvented on each screen.
- Make the interface distinct without sacrificing navigation clarity or accessibility.
- Use appropriate loading, skeleton/shimmer, empty, success, validation-error, offline, and retry states.
- Skeletons should reflect the content they replace and disappear when loading ends. Avoid flashing, high-contrast shimmer, and unnecessary animations.
- Provide meaningful accessibility labels, readable contrast, and practical touch targets.
- Keep Stay, Rent, and Buy workflows distinct where their information and actions differ.
- Do not label a request as a confirmed reservation unless the backend has confirmed that state.

### Architecture and code

- Keep UI presentation, application logic, and data access separated according to the architecture already established in the codebase.
- If MVVM is used, keep screen state and business decisions out of Activities and Fragments where practical.
- Use ViewBinding if it is configured for the module; avoid unnecessary repeated view lookups.
- Use RecyclerView for data-driven lists and reuse adapters/view holders appropriately.
- Use Retrofit/OkHttp only where configured for network communication. Keep endpoint definitions and network handling organised.
- Use Glide or the image library already selected by the project consistently; avoid adding a second image-loading library without a concrete need.
- Use Room only for data that genuinely needs local persistence or caching. Clearly distinguish local cached data from authoritative server data.
- Handle lifecycle changes and asynchronous responses safely. Do not update views after their lifecycle owner is no longer active.
- Avoid hard-coded production URLs, secrets, and user-specific values in source code.

## 7. Backend and API Guidelines

For the Java/Spring Boot backend, follow the actual module structure and dependency versions in the repository. Where the planned architecture is adopted:

- Keep HTTP controllers focused on request/response mapping and delegate application rules to service classes.
- Use request and response DTOs rather than exposing persistence entities directly as public API contracts.
- Validate incoming data and return consistent error responses.
- Use Spring Security and server-side authorisation for protected operations; hiding a button in the Android interface is not access control.
- Check ownership and permissions before exposing or changing user-specific records.
- Use transaction boundaries for operations that must remain consistent, particularly availability and request state changes.
- Document endpoint changes and keep API behaviour compatible where practical.
- Do not return secrets, internal stack traces, or unnecessary personal data in API responses.
- Add or update OpenAPI documentation if the project uses it.

Never assume that a client-side check is sufficient to enforce a business rule. The backend must validate state transitions and access to protected resources.

## 8. Data and Database Changes

The intended direction is PostgreSQL for authoritative server-side relational data and Room for appropriate local Android persistence. Follow the configured database implementation in the relevant module.

For any database-related change:

- Explain the purpose of the schema or model change.
- Preserve referential integrity and use appropriate constraints and indexes.
- Avoid storing duplicated data unless there is a documented reason.
- Keep local cache data distinguishable from server-owned data.
- Use the project's migration mechanism, if configured, for schema changes. Do not make undocumented production schema changes.
- Consider existing records and compatibility when changing or removing fields.
- Never commit real user records, production database dumps, credentials, or private data.

If Flyway or another migration tool is not present in the repository, do not claim it is in use or add it merely to match this guide; discuss the migration approach with the maintainers first.

## 9. Dependencies

Add a dependency only when it provides a clear, justified benefit.

Before adding or upgrading a library:

1. Check whether an existing dependency already solves the problem.
2. Verify compatibility with the project's configured Android, Java, Gradle, Spring Boot, and SDK versions.
3. Prefer maintained libraries with clear documentation and suitable licences.
4. Explain the reason for the dependency in the Pull Request.
5. Update the relevant Gradle or Maven file and project documentation.

Do not add duplicate libraries for the same task without a concrete reason. A README badge alone does not mean a dependency is installed or used.

## 10. Testing and Quality Checks

Tests should cover the behaviour changed by the contribution. Depending on the modules and tooling actually present, this may include:

- Android unit tests for validation, mapping, and presentation logic.
- UI tests for important navigation and form behaviour.
- Backend unit tests for service rules and validation.
- API/integration tests for persistence, authorisation, and error handling.
- Tests for empty responses, malformed input, missing images, and network failures.
- Regression tests for fixed bugs.

Use the commands supported by the module's checked-in build files and wrapper scripts. For example, if the Android Gradle wrapper exists, run the relevant Gradle tests from that module; if a Spring Boot Maven module exists, run its Maven tests. Do not report a test as successful unless it has actually been run.

For changes to user-facing screens, verify small and larger Android layouts and inspect loading, empty, error, and success states where applicable.

## 11. Documentation

Update documentation when a contribution changes:

- Setup or build steps.
- Required configuration.
- Screens, user flows, or supported features.
- API endpoints or request/response formats.
- Data models or migration steps.
- Testing commands or known limitations.

Use screenshots that reflect the actual current application. Clearly mark future designs, mock data, and planned capabilities as such.

## 12. Security and Responsible Disclosure

Do not publish vulnerabilities, exploitable details, credentials, or personal information in public Issues. Report security concerns privately to the repository maintainer using the contact or security-reporting channel specified by the repository. If no private reporting channel is listed, contact the maintainer before publishing sensitive details.

Do not commit `.env` files, signing keys, keystores, service-account JSON files, access tokens, private certificates, or production configuration. Provide safe example configuration with placeholder values instead.

## 13. Licensing and Third-Party Assets

Only contribute code, fonts, icons, images, and other assets that you created or are permitted to redistribute. Respect third-party licences and preserve required attribution and notices. Do not commit commercial or copyrighted assets without permission.

## 14. Code of Conduct

All contributors are expected to follow the repository's `CODE_OF_CONDUCT.md`. Be respectful, constructive, and focused on improving the product and the team's work.

## 15. Definition of Done

A contribution is ready to merge when applicable items below are complete:

- [ ] The change addresses the stated Issue or agreed requirement.
- [ ] Code follows the existing project conventions.
- [ ] Relevant tests have been added or updated and run.
- [ ] Loading, empty, validation-error, and failure cases have been handled where relevant.
- [ ] Accessibility and layout behaviour have been considered for UI changes.
- [ ] API contracts and data changes are documented where relevant.
- [ ] No secrets, private data, debug leftovers, or unrelated files are included.
- [ ] README or other documentation has been updated if needed.
- [ ] The Pull Request description explains the change and its verification.

Thank you for helping improve PLAVIO.
