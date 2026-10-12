# PLAVIO

**Android Property Discovery & Booking-Request Application**

PLAVIO is a business-oriented Android application designed to make property discovery more convenient and organized. It brings property browsing, listing details, saved options, and property-related requests into a focused mobile experience.

The project scope covers the Android application and the data layer required by its user-facing workflows. It does **not** include a separate web-based administration panel or back-office dashboard.

---

## Project Overview

Searching for a suitable property can involve reviewing multiple listings, comparing important details, and keeping track of promising options. PLAVIO brings these activities together in one mobile application with an emphasis on clear information, straightforward navigation, and a consistent user journey.

The application is centered on the end-user experience. Its data layer supports the property and user information required by the mobile workflows, keeping data access separate from presentation logic wherever supported by the existing implementation.

## Key Mobile Workflows

- **Property discovery:** Browse the property listings available in the application.
- **Search and filtering:** Refine results using the search criteria supported by the app.
- **Property details:** Review listing information and available images before taking the next step.
- **Saved properties:** Keep selected listings available for later review, where implemented.
- **User account:** Use the account functionality provided by the application.
- **Booking or inquiry requests:** Start the appropriate request flow based on the listing type and the business rules implemented in the app.
- **Data handling:** Present loading, empty, success, and error states consistently where supported by the implementation.

## Project Scope

### Included

- Android mobile application and its user-facing screens.
- Application logic needed for the supported mobile workflows.
- App-related data models and database integration.
- Property listing information and listing details.
- Data operations required by the features included in the mobile application.
- Input validation and error handling implemented in the app.

### Outside the Scope

- A separate web-based admin panel or administration portal.
- Administrative dashboards and business reporting interfaces.
- Payment processing or financial settlement unless explicitly implemented in the source code.
- External services that are not configured and verified in the project.

## Technology Stack

- **Primary language:** Java
- **Platform:** Android
- **Development environment:** Android Studio
- **UI approach:** Native Android UI
- **Data layer:** Application-specific data models and database operations

The exact database technology and any service/API integration should be named here once verified against the project configuration. Only technologies actually used in the delivered implementation should appear in this list.

## Application Data Domain

The app-related data layer is concerned with the information needed by the mobile experience. Depending on the actual schema, these concepts may include:

| Data concept | Purpose |
|---|---|
| User | Stores the user information needed by the application. |
| Property listing | Represents the property information displayed to users. |
| Listing media | Associates images or other supported media with a listing. |
| Favorite | Records listings saved by a user, if this feature is implemented. |
| Booking or inquiry | Represents a user request related to a property, if supported by the app. |
| Availability | Represents availability details where the implemented workflow requires them. |

The final documentation should match the real schema, including actual table, collection, entity, and field names. These concepts describe the application domain and should not be interpreted as a claim that every item above is already present in the database.

## Application Structure

The application is intended to maintain clear responsibilities between its main areas:

- **Presentation:** Screens, navigation, and UI state.
- **Application logic:** Validation and user actions.
- **Data access:** Reading and writing application data through the configured database or service.
- **Shared utilities:** Common helpers and consistent error handling.

The exact package and folder names should follow the existing source code rather than be documented as folders that do not exist.

## Security and Data Handling

Database access rules and authentication requirements should be configured to match the application's actual identity and data model. User input should be validated, and access to user-specific records should be restricted appropriately.

Never commit passwords, access tokens, service-account files, production credentials, or private user data to a public repository. Local configuration instructions should explain the required setup without exposing secrets.

## Quality Checks

The critical mobile flows should be checked before a release, including:

- Opening the app and navigating between screens.
- Loading and displaying property information.
- Search and filtering behavior.
- Saving or removing a favorite, if supported.
- Submitting a booking or inquiry request, if supported.
- Handling empty results, invalid input, and network or data-access failures.
- Confirming that database rules prevent unauthorized access to protected information.

## Repository Scope

PLAVIO focuses on the Android client and its associated data layer. A separate administration interface, payment system, or other platform component should be documented as an additional project only if it is actually developed and included in the repository.

## Project Summary

- **Project:** PLAVIO
- **Application type:** Android mobile application
- **Primary language:** Java
- **Delivery scope:** Mobile application and app-related data layer
- **Admin panel:** Not included in this scope

---

*This README is a project-documentation draft. Before treating it as the final delivery record, align the feature list, database technology, setup steps, and data model with the actual source code and configuration.*
