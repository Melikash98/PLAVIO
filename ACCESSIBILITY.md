# Accessibility

PLAVIO aims to make property discovery and property-related requests usable by as many people as possible, including people who use assistive technology, adjust text size, or interact with their devices in different ways. Accessibility is part of designing and implementing the Android experience—not a finishing step.

This document describes the design and contribution expectations for the PLAVIO Android application. It is an ongoing commitment, not a claim that the current application has passed a formal accessibility audit or conforms to a particular standard.

## Priorities

### Clear content and navigation

- Use meaningful, visible labels for actions, form fields, navigation destinations, property details, and request states.
- Keep screen headings, content order, and navigation consistent and predictable.
- Make it clear whether a property request is submitted, awaiting a response, accepted, declined, or cancelled. Do not communicate status by colour alone.
- Use concise language and explain validation errors in terms that help people correct them.

### Screen readers and assistive technology

- Provide meaningful accessible names for interactive controls, especially icon-only buttons such as Save, Back, Share, and Close.
- Give informative property images useful descriptions where they convey information. Mark decorative images so they do not add unnecessary announcements.
- Check that TalkBack focus order follows the visual and logical reading order.
- Expose the purpose, state, and result of controls to accessibility services. Do not make essential information available only through visual animation or colour.
- Avoid repeated or redundant announcements, and ensure dialogs, bottom sheets, form errors, and request-submission feedback can be discovered by screen-reader users.

### Text, contrast, and touch targets

- Support Android font scaling and display-size settings without clipping text, hiding actions, or making forms unusable.
- Use sufficient contrast between text, controls, icons, and their backgrounds. Do not rely on colour as the only way to distinguish selected, pending, successful, or error states.
- Aim for interactive touch targets of at least **48 × 48 dp** where practical, with enough spacing to prevent accidental activation.
- Do not place important text inside images. Use real interface text so it can be read, resized, translated, and announced by assistive technology.

### Motion and loading states

- Keep animations subtle and non-essential. Do not use flashing or rapidly alternating effects.
- Loading shimmer must not be the only indication that data is loading. Provide an accessible description or equivalent progress indication where appropriate, and ensure the loading state is not repeatedly announced.
- Replace skeleton content with the loaded, empty, or error state when the operation finishes.
- Avoid unnecessary motion and respect relevant device accessibility settings where the implementation supports them.

### Forms and requests

- Provide persistent labels rather than relying only on placeholder text.
- Associate validation messages with the relevant field and make errors understandable to screen-reader users.
- Preserve entered information when it is safe and reasonable to do so after a correctable validation error.
- Ensure the keyboard does not permanently obscure important fields or primary actions.
- After a request is submitted, make the result clear without implying that a booking is confirmed before it actually is.

### Language and layout

- Keep user-facing strings in resources rather than hard-coding text into layouts or logic.
- Allow labels and longer translations to expand without clipping or overlapping other controls.
- Use layout direction and alignment that can support right-to-left languages if those languages become part of the product's supported scope.

## Contributor Expectations

When changing a user-facing screen or interaction, contributors should:

1. Preserve logical reading and focus order.
2. Provide accessible labels for interactive icons and controls.
3. Check contrast, text scaling, and touch-target size.
4. Consider TalkBack announcements for navigation, dialogs, validation, loading, and submission results.
5. Include relevant loading, empty, error, disabled, and success states where the flow requires them.
6. Avoid introducing animation as the only way to communicate information.
7. Update design or implementation notes when accessibility behaviour changes.
8. Include brief manual-test notes in the pull request for substantial UI changes.

Where practical, test the changed flow with TalkBack enabled, increased font size, and increased display size on an Android device or emulator. Android Accessibility Scanner may be used where available as a helpful check, but an automated scan does not replace manual testing with assistive technology.

Do not claim formal accessibility conformance unless an evaluation has been completed. If a standard or conformance level is adopted in the future, document the evaluated scope, method, date, and evaluator.

## Reporting Accessibility Issues

Please report an accessibility barrier through the [PLAVIO GitHub repository](https://github.com/Melikash98/PLAVIO) by opening an issue. Start the title with **`[Accessibility]`** and describe the barrier in plain language. If issue templates or labels are available, select the relevant accessibility option.

Useful information includes:

- The screen or task where the barrier occurs.
- What you expected to happen and what happened instead.
- The Android version and device type, if known.
- The assistive technology or relevant device setting used, if applicable (for example, TalkBack or a larger font setting).
- Steps that help reproduce the issue.
- An optional screenshot or recording, provided it does not contain personal or sensitive information.

You do not need to disclose a disability or medical information to report a barrier. Please do not include passwords, access tokens, private account data, or other sensitive information in a public issue. If the report also describes a security vulnerability, follow `SECURITY.md` and report it privately instead.

## Severity

Maintainers may assign or adjust severity during triage. Reporters do not need to select a severity level.

- **Critical:** An accessibility barrier prevents users from accessing the app or completing an essential task, with no reasonable workaround. Example: users of a screen reader cannot reach the primary navigation or submit any property request.
- **High:** A key flow is substantially blocked for some users, and the available workaround is difficult or unreliable. Example: a required form field has no accessible label and cannot be identified with a screen reader.
- **Medium:** A task remains possible but is confusing, error-prone, or significantly less efficient. Example: request status is communicated only through colour.
- **Low:** A minor inconsistency or inconvenience that does not substantially prevent task completion. Example: a non-essential icon has an unclear accessible name.

These descriptions help prioritise work; they do not promise a specific fix deadline.

## How We Respond

Maintainers will review accessibility issues as project capacity allows. They may ask for reproduction details, clarify the affected workflow, or propose an interim workaround. Acknowledgement and resolution times are not guaranteed.

When a fix is prepared, contributors should verify the affected flow again and, where practical, ask the reporter to confirm that the barrier has been addressed. If the proposed change has a known limitation, document it in the issue rather than implying that all accessibility concerns have been resolved.

## Ownership and Maintenance

The project maintainer and the contributor responsible for the affected feature share responsibility for reviewing accessibility during design and code review. Pull requests that alter navigation, forms, property cards, image galleries, request status, or loading states should consider the guidance in this document.

Review this policy when major UI architecture changes, new user flows are introduced, or support for additional languages and platforms is added. If accessibility ownership changes, update this section so responsibilities remain clear.

## Supported Environments

PLAVIO is scoped to an Android mobile application. The design and implementation should account for common Android accessibility features, including TalkBack, system font scaling, display-size settings, and touch interaction.

The project does not currently publish a verified matrix of tested device models, Android versions, screen readers, or assistive technologies. Contributors should record the environment used for relevant manual testing in their pull requests and issues. Do not interpret the intended support described here as proof that every device and configuration has been tested.

## Known Limitations

No complete accessibility audit or verified conformance assessment is documented in this file. Individual barriers may remain undiscovered until the relevant screens and flows are implemented and tested.

When a limitation is identified, describe its effect on the user, provide any known workaround, and link to a tracked issue when available. Update this section as limitations are confirmed and resolved; do not claim that no accessibility barriers exist without an appropriate evaluation.

## Feedback and Improvements

Suggestions to improve this policy or PLAVIO's accessibility practices are welcome. Open an issue in the [PLAVIO GitHub repository](https://github.com/Melikash98/PLAVIO) with **`[Accessibility]`** in the title. Describe the proposed improvement and its expected benefit in plain language.

For active barriers affecting the application, use the reporting process above. For suspected security vulnerabilities, use the private reporting guidance in `SECURITY.md`.
