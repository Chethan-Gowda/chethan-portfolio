# TD-004 — WordPress Hooks & PHP Architecture

**Status:** Approved  
**Phase:** Phase 4 — Technical Design  
**Related Architecture:** ARCHITECTURE-001  
**Related ADRs:** ADR-001, ADR-003  
**Related Technical Design:** TD-001, TD-002, TD-003

---

## 1. Purpose

This document defines how PHP functionality will be organized within the portfolio WordPress theme.

The objective is to keep the PHP architecture:

- Simple.
- Maintainable.
- Secure.
- WordPress-native.
- Easy to understand.
- Consistent with the approved Block Theme architecture.
- Free from unnecessary abstraction.

The design also defines where WordPress hooks, Custom Post Type registration, asset loading, security functionality, and contact-form processing will live.

---

# 2. Architectural Principles

The PHP architecture follows these principles:

1. `functions.php` acts primarily as a lightweight bootstrap file.
2. Related functionality is separated into focused files under `/inc/`.
3. WordPress hooks are used instead of custom application-level event systems.
4. Native WordPress APIs are preferred.
5. The Project Custom Post Type is registered by the theme because it is specific to this portfolio.
6. Business logic should not be placed directly inside templates.
7. User-controlled data must be validated and sanitized where appropriate.
8. Output must be escaped at the point of output.
9. Contact-form processing must include security controls.
10. No framework, dependency injection container, service layer, or custom routing layer will be introduced unless a future approved requirement justifies it.

---

# 3. PHP Structure

The approved PHP structure is:

```text
portfolio-theme/
├── functions.php
└── inc/
    ├── setup.php
    ├── enqueue.php
    ├── post-types.php
    ├── security.php
    └── contact-form.php
```

Each file has a clearly defined responsibility.

---

# 4. `functions.php`

`functions.php` will act as the theme's bootstrap file.

Its primary responsibility is to load the required PHP modules.

Conceptually:

```text
functions.php
    │
    ├── setup.php
    ├── enqueue.php
    ├── post-types.php
    ├── security.php
    └── contact-form.php
```

`functions.php` should not become a large collection of unrelated functions.

### Responsibilities

- Load required `/inc/` files.
- Keep theme initialization easy to understand.
- Avoid containing significant business logic.

### Out of scope

The following should not be placed directly into `functions.php` unless there is a strong reason:

- Large functions.
- CPT implementation.
- Contact-form processing.
- Complex validation logic.
- Large amounts of HTML.
- Database access logic.
- Unrelated utility functions.

---

# 5. `inc/setup.php`

This file is responsible for theme initialization and WordPress theme support.

Potential responsibilities include:

- Theme setup.
- `after_setup_theme` functionality.
- Navigation/menu registration where required.
- Featured image support.
- Editor support.
- Other required WordPress theme supports.

The implementation must only enable features required by the approved specifications.

### Example responsibilities

```text
Theme Setup
    ↓
after_setup_theme
    ↓
Register theme supports
    ↓
Register navigation/menu support if required
```

The file should remain focused on theme initialization rather than general application functionality.

---

# 6. `inc/enqueue.php`

This file is responsible for frontend and editor asset loading.

Potential responsibilities include:

- Enqueueing CSS.
- Enqueueing JavaScript.
- Loading editor-specific styles where required.
- Applying appropriate versioning/cache-busting mechanisms.

Assets should be loaded only when required.

### Performance Principle

Avoid globally loading JavaScript or CSS that is not needed.

The portfolio should have minimal frontend dependencies.

---

# 7. `inc/post-types.php`

This file is responsible for registering the `project` Custom Post Type.

The approved content architecture contains only one Custom Post Type:

```text
project
```

### Responsibility

Register:

```text
project
```

using the WordPress Custom Post Type API.

The registration should define the required behavior, including where appropriate:

- Public visibility.
- Archive support.
- REST API availability.
- Supported features.
- Rewrite behavior.
- Appropriate labels.
- Menu configuration.

The exact configuration must follow the approved Project specification.

---

# 8. Project CPT Registration

The Project CPT is theme-owned because it is currently considered portfolio-specific functionality.

This decision was made deliberately to keep the architecture simple.

### Decision

```text
Project CPT
    ↓
portfolio theme
    ↓
inc/post-types.php
```

### Trade-off

The Project CPT will be coupled to the portfolio theme.

If the theme is removed, project registration will no longer be active unless the functionality is later moved to a plugin.

For this project, the simplicity benefit outweighs the portability benefit.

### Future Change

If the portfolio evolves into a reusable theme, framework, or multi-site content platform, this decision should be revisited through the SDD change process.

---

# 9. Project Data Handling

Project data should be accessed using standard WordPress APIs.

Preferred approaches include:

- WordPress template functions.
- WP_Query where custom queries are required.
- Standard post metadata APIs where metadata is defined.
- Native featured-image functions.
- Standard post content functions.

Avoid:

- Direct SQL unless clearly justified.
- Custom database tables.
- Custom ORM layers.
- Custom query abstraction layers.

---

# 10. `inc/security.php`

This file contains security-related theme functionality that applies globally to the theme.

Potential responsibilities include:

- Security-related filters/actions required by the specification.
- Safe handling of theme-generated data where centralized functionality is appropriate.
- Security helpers only when they provide genuine reuse.

This file must not become a generic dumping ground for every security-related function.

Security practices should primarily be implemented at the point where data is processed or output.

---

# 11. Sanitization, Validation and Escaping

The theme will follow the WordPress security principle:

```text
Input
  ↓
Validate
  ↓
Sanitize
  ↓
Store
  ↓
Escape
  ↓
Output
```

These operations have different purposes and must not be treated as interchangeable.

### Validation

Determine whether incoming data meets the expected rules.

Examples:

- Required fields are present.
- URL is valid.
- Expected value type is received.

### Sanitization

Clean data before storing or processing it where appropriate.

Examples:

- Text sanitization.
- URL sanitization.
- Email sanitization.

### Escaping

Escape data when rendering it to the browser.

Examples:

- HTML output.
- Attribute values.
- URLs.
- Text content.

The implementation should use the appropriate WordPress API for each situation.

---

# 12. `inc/contact-form.php`

This file will contain the server-side functionality for the portfolio contact form.

The contact form is a custom form as defined by the approved project architecture and requirements.

Responsibilities include:

- Processing submitted contact data.
- Validating required fields.
- Sanitizing submitted values.
- Validating email addresses.
- Protecting against unauthorized submissions.
- Handling successful submission.
- Handling validation errors.
- Sending the contact message through the approved WordPress mail mechanism.
- Preventing duplicate or unintended processing where required.

The detailed form behavior will be derived from the approved contact-form specification.

---

# 13. Contact Form Security

The contact form must implement appropriate WordPress security controls.

At minimum, the design should consider:

- Nonce verification.
- Server-side validation.
- Input sanitization.
- Email validation.
- Appropriate escaping of error/success messages.
- Spam protection if required by the specification.
- Safe email handling.

Client-side validation must never be considered a replacement for server-side validation.

---

# 14. WordPress Hooks

The project will use native WordPress hooks.

Hooks should be selected based on the responsibility of the functionality.

Examples include:

```text
after_setup_theme
wp_enqueue_scripts
init
wp_head
wp_footer
```

Additional hooks may be introduced when required by the specification.

Hooks must not be added merely for architectural style.

---

# 15. Hook Registration Responsibility

Each module should register only the hooks relevant to its responsibility.

Example:

```text
setup.php
    ↓
after_setup_theme

enqueue.php
    ↓
wp_enqueue_scripts

post-types.php
    ↓
init

contact-form.php
    ↓
appropriate form-processing hook
```

This makes the relationship between functionality and WordPress lifecycle events clear.

---

# 16. Avoiding Global Hook Complexity

The project will not introduce:

- Custom event buses.
- Custom hook abstractions.
- Service containers.
- Dependency injection frameworks.
- Application lifecycle frameworks.

Native WordPress hooks are sufficient for this project's scale.

---

# 17. Presentation vs Business Logic

PHP functionality should remain separate from presentation.

### Preferred

```text
WordPress Hook
      ↓
PHP Function
      ↓
Retrieve / Validate / Process Data
      ↓
Template / Pattern
      ↓
Presentation
```

### Avoid

```text
Template
    ↓
Large PHP processing block
    ↓
Database operation
    ↓
Validation
    ↓
HTML output
```

Templates should primarily compose and present content.

---

# 18. Direct Database Access

Direct database queries are discouraged.

The implementation should prefer:

- WordPress APIs.
- WP_Query.
- Metadata APIs.
- Post APIs.
- Options APIs where required.

Direct `$wpdb` usage should only be introduced when:

1. A requirement explicitly requires it, and
2. The WordPress API cannot reasonably satisfy the requirement.

If introduced, the implementation must follow WordPress database security practices, including prepared statements where applicable.

---

# 19. Global Helper Functions

The theme should avoid creating a large collection of generic global helper functions.

Before introducing a helper, determine whether:

- WordPress already provides the required functionality.
- The function is genuinely reused.
- The function belongs to an existing responsibility-specific module.

Avoid generic files such as:

```text
helpers.php
utils.php
common.php
misc.php
```

unless a future specification demonstrates a clear need.

---

# 20. Error Handling

The implementation should provide controlled handling for expected errors.

Examples include:

- Invalid contact-form input.
- Missing required project data.
- Failed email processing.
- Invalid URLs.

User-facing errors should be:

- Understandable.
- Accessible.
- Safe.
- Free from sensitive implementation details.

Internal technical details should not be exposed to users.

---

# 21. Logging

The portfolio should not introduce a custom logging framework.

If logging is required for a specific production issue or operational requirement, use an appropriate WordPress/hosting-supported mechanism.

Sensitive information must not be written to logs unnecessarily.

---

# 22. Performance Considerations

PHP implementation should minimize unnecessary processing.

The theme should:

- Avoid repeated queries.
- Avoid unnecessary database access.
- Avoid expensive processing during every request.
- Load only required assets.
- Use WordPress APIs efficiently.
- Avoid large initialization frameworks.

The project is a simple portfolio, so performance should be achieved through simplicity rather than optimization frameworks.

---

# 23. Security Considerations

The implementation must follow WordPress security practices.

Key areas include:

### Input

Validate and sanitize user-controlled data.

### Output

Escape output based on context.

### Forms

Use nonce verification and server-side validation.

### URLs

Validate and sanitize URLs appropriately.

### Permissions

Where administrative functionality is introduced, verify appropriate capabilities.

### Data Access

Avoid exposing private or sensitive data.

### Database

Prefer WordPress APIs and avoid direct SQL unless justified.

---

# 24. Theme vs Plugin Boundary

The following rule applies:

### Theme

Responsible for:

- Portfolio presentation.
- Portfolio-specific Project CPT.
- Theme setup.
- Theme assets.
- Theme-specific contact-form functionality.
- Template and pattern functionality.

### Plugin

No custom project-specific plugin is required initially.

Third-party plugins may be introduced only when justified by an approved requirement.

The project should not create a plugin merely to demonstrate plugin architecture.

---

# 25. Future Plugin Extraction

The Project CPT or other functionality may later be moved into a plugin if:

- The content model becomes reusable outside the theme.
- The portfolio becomes a reusable product.
- The theme is replaced but project data must remain available.
- Multiple themes need access to the same functionality.
- A new requirement makes portability important.

Such a change must go through the SDD change process.

---

# 26. PHP Coding Standards

PHP implementation should follow:

- WordPress Coding Standards.
- Meaningful function names.
- Clear responsibility boundaries.
- Appropriate documentation for non-obvious logic.
- Minimal nesting.
- Avoidance of unnecessary abstractions.
- Secure WordPress APIs.
- Consistent naming conventions.

Code should be readable by another WordPress developer without requiring additional architectural documentation.

---

# 27. Out of Scope

The following are explicitly out of scope:

- Laravel or other PHP frameworks.
- Dependency injection containers.
- Custom ORM.
- Custom routing.
- Custom database layer.
- Custom event system.
- Application service container.
- Repository pattern unless a demonstrated requirement emerges.
- Complex domain-driven architecture.
- Custom API framework.
- Headless WordPress backend architecture.

These would introduce unnecessary complexity for the current portfolio.

---

# 28. Dependencies

TD-004 depends on:

- **ARCHITECTURE-001 — WordPress Architecture**
- **TD-001 — Theme & Folder Structure**
- **TD-002 — Content & Data Model**
- **TD-003 — Templates & Components**
- Approved specifications for Projects and Contact.

---

# 29. Acceptance Criteria

TD-004 is considered complete when:

- [ ] `functions.php` has a defined bootstrap responsibility.
- [ ] `/inc/` responsibilities are clearly defined.
- [ ] Theme setup responsibilities are defined.
- [ ] Asset enqueueing responsibilities are defined.
- [ ] Project CPT registration is assigned to `/inc/post-types.php`.
- [ ] Project data access follows WordPress APIs.
- [ ] Security responsibilities are defined.
- [ ] Contact-form processing has a defined PHP responsibility.
- [ ] WordPress hooks are mapped to relevant modules.
- [ ] Validation, sanitization, and escaping responsibilities are defined.
- [ ] Direct database access is discouraged and controlled.
- [ ] Templates remain separate from significant business logic.
- [ ] Theme/plugin boundaries are defined.
- [ ] Performance considerations are defined.
- [ ] Security considerations are defined.
- [ ] Unnecessary PHP architecture is explicitly excluded.

---

# 30. Traceability

The technical design maintains:

```text
Requirement
    ↓
Specification
    ↓
Architecture
    ↓
Technical Design
    ↓
Implementation Task
    ↓
Implementation
    ↓
Test
```

TD-004 is related to:

```text
ARCHITECTURE-001
        ↓
ADR-001
        ↓
ADR-003
        ↓
TD-001
        ↓
TD-002
        ↓
TD-003
        ↓
TD-004
```

Implementation tasks and tests will be created during the Implementation Planning and Testing phases.

---

# 31. Specification Change Rule

If implementation requires PHP architecture that is not defined by this document, the change must be evaluated before implementation.

If implementation differs from TD-004 without updating the design:

> **This introduces specification drift.**

The team must decide whether to:

1. Change the implementation to match TD-004, or
2. Update TD-004 and any affected specifications, architecture decisions, and requirements.

---

# 32. Decision Summary

The portfolio will use a lightweight, WordPress-native PHP architecture.

The final responsibility model is:

```text
functions.php
    ↓
Bootstrap only

inc/setup.php
    ↓
Theme setup

inc/enqueue.php
    ↓
CSS / JS / editor assets

inc/post-types.php
    ↓
Project CPT

inc/security.php
    ↓
Theme-level security functionality

inc/contact-form.php
    ↓
Contact form processing
```

The architecture intentionally avoids frameworks, custom abstractions, and unnecessary plugin separation.

This keeps the implementation appropriate for a personal portfolio while still providing clear responsibility boundaries and a practical example of Spec-Driven Development.

---

**Document:** TD-004  
**Title:** WordPress Hooks & PHP Architecture  
**Phase:** Phase 4 — Technical Design  
**Status:** Approved