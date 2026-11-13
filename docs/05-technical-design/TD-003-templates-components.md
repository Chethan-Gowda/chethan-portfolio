# TD-003 — Templates & Components

**Status:** Approved  
**Phase:** Phase 4 — Technical Design  
**Related Architecture:** ARCHITECTURE-001  
**Related ADRs:** ADR-001, ADR-003  
**Related Technical Design:** TD-001, TD-002

---

## 1. Purpose

This document defines how WordPress templates, template parts, patterns, and reusable components will work together to render the portfolio website.

The design follows the project's approved **native WordPress Block Theme** architecture and the decision to use a **pattern-driven Home page**.

The objective is to keep page composition simple, reusable, maintainable, and aligned with native WordPress capabilities without introducing unnecessary abstraction.

---

## 2. Design Principles

The template and component architecture follows these principles:

1. Prefer native WordPress Block Theme functionality.
2. Use patterns for meaningful reusable page sections.
3. Keep templates focused on page-level composition.
4. Keep template parts focused on shared site structure.
5. Use reusable PHP components only where genuine reuse exists.
6. Keep business logic outside templates wherever practical.
7. Prefer native WordPress blocks before introducing custom implementations.
8. Avoid unnecessary component abstractions.
9. Ensure accessibility and responsive behavior are considered at the template and pattern level.
10. Keep content independent from presentation code.

---

## 3. Page Composition Model

The theme will follow this general hierarchy:

```text
WordPress Template
        ↓
Template Parts
        ↓
Patterns
        ↓
Reusable Components / Blocks
        ↓
WordPress Content
```

The Home page will primarily be composed using reusable patterns.

```text
front-page.html
│
├── Header
│
├── Hero Pattern
├── About Pattern
├── Skills Pattern
├── Featured Projects Pattern
├── Experience Pattern
├── Contact CTA Pattern
│
└── Footer
```

This approach allows the Home page to remain readable while individual sections remain reusable and independently maintainable.

---

## 4. Template Structure

The theme will contain the following templates:

```text
templates/
├── index.html
├── front-page.html
├── page.html
├── single.html
├── single-project.html
├── archive-project.html
├── 404.html
└── search.html
```

### 4.1 `front-page.html`

**Responsibility:**

Defines the overall composition of the portfolio Home page.

The template should primarily assemble the required patterns and shared template parts.

It should not contain significant business logic.

Expected structure:

```text
Header
    ↓
Hero Pattern
    ↓
About Pattern
    ↓
Skills Pattern
    ↓
Featured Projects Pattern
    ↓
Experience Pattern
    ↓
Contact CTA Pattern
    ↓
Footer
```

---

### 4.2 `page.html`

**Responsibility:**

Provides the default template for standard WordPress pages such as:

- About
- Contact

The template should support normal WordPress page content and should not contain page-specific business logic.

---

### 4.3 `single.html`

**Responsibility:**

Provides the fallback template for standard WordPress posts.

The portfolio is not primarily a blog, but the template is retained as part of the standard WordPress theme structure.

---

### 4.4 `single-project.html`

**Responsibility:**

Displays an individual portfolio project.

Expected structure:

```text
Header
    ↓
Project Title
    ↓
Featured Image
    ↓
Project Metadata
    ↓
Project Content
    ↓
Project URL
    ↓
Footer
```

The template should retrieve project information using standard WordPress template functionality.

---

### 4.5 `archive-project.html`

**Responsibility:**

Displays the portfolio project listing.

Expected structure:

```text
Header
    ↓
Page Heading
    ↓
Project Query
    ↓
Project Cards
    ↓
Pagination
    ↓
Footer
```

The archive should display published projects and support pagination where required.

---

### 4.6 `search.html`

**Responsibility:**

Displays WordPress search results.

The template should provide:

- Search results heading.
- Matching content.
- Appropriate links.
- Pagination where required.
- Accessible empty-result handling.

---

### 4.7 `404.html`

**Responsibility:**

Provides a useful not-found experience.

The page should:

- Clearly communicate that the requested page was not found.
- Provide a route back to the Home page.
- Provide useful navigation where appropriate.
- Maintain the site's normal header/footer structure.

---

### 4.8 `index.html`

**Responsibility:**

Acts as the fallback template required by the WordPress template hierarchy.

It should remain simple and should not duplicate functionality unnecessarily provided by more specific templates.

---

# 5. Template Parts

Shared site structure will be maintained using template parts.

```text
parts/
├── header.html
├── footer.html
└── navigation.html
```

## 5.1 `header.html`

Responsible for:

- Site branding.
- Navigation area.
- Header layout.
- Any globally required header elements.

---

## 5.2 `navigation.html`

Responsible for:

- Primary site navigation.
- Navigation links.
- Responsive navigation behavior supported by WordPress blocks/theme functionality.

Navigation should remain accessible through keyboard and assistive technologies.

---

## 5.3 `footer.html`

Responsible for:

- Footer content.
- Copyright information where required.
- Supporting links.
- Social/profile links where appropriate.

---

# 6. Home Page Patterns

The Home page will use reusable block patterns.

```text
patterns/
├── hero.php
├── about.php
├── skills.php
├── featured-projects.php
├── experience.php
└── contact-cta.php
```

Each pattern represents a meaningful section of the portfolio.

---

## 6.1 Hero Pattern

**Purpose:**

Introduce the portfolio owner and communicate the primary professional positioning.

Potential content includes:

- Name.
- Professional title.
- Short professional statement.
- Primary call-to-action.
- Supporting visual/content where appropriate.

The pattern should use native WordPress blocks wherever possible.

---

## 6.2 About Pattern

**Purpose:**

Provide a concise professional introduction.

The pattern should present relevant professional information without duplicating the full About page unnecessarily.

---

## 6.3 Skills Pattern

**Purpose:**

Present key technical and professional skills.

Skills should initially be managed as normal WordPress content rather than introducing a separate custom post type.

---

## 6.4 Featured Projects Pattern

**Purpose:**

Display selected portfolio projects on the Home page.

The pattern should retrieve projects from the approved `project` Custom Post Type.

Expected structure:

```text
Featured Projects
        ↓
Project Query
        ↓
Project Card
Project Card
Project Card
        ↓
View All Projects
```

The number of featured projects and selection mechanism will be determined by the approved functional specification.

The implementation must not introduce additional data structures unless required by the specification.

---

## 6.5 Experience Pattern

**Purpose:**

Present relevant professional experience on the Home page.

Experience should initially be managed as normal WordPress page/content data rather than a separate Custom Post Type.

---

## 6.6 Contact CTA Pattern

**Purpose:**

Provide a clear call-to-action that directs users toward contacting the portfolio owner.

The actual contact mechanism will follow the approved contact-form specification and technical design.

---

# 7. Project Components

Reusable presentation components are defined under:

```text
components/
├── project-card.php
├── project-meta.php
├── social-links.php
└── pagination.php
```

Components should only be introduced where reuse justifies their existence.

---

## 7.1 `project-card.php`

**Responsibility:**

Display a summarized representation of a portfolio project.

Expected information may include:

- Project title.
- Featured image.
- Short description.
- Technologies.
- Project link.

The component must not contain unrelated business logic.

---

## 7.2 `project-meta.php`

**Responsibility:**

Display project metadata such as:

- Technologies.
- Role.
- Project URL.

The component should provide consistent presentation across project views where applicable.

---

## 7.3 `social-links.php`

**Responsibility:**

Display configured professional/social profile links.

Links must use meaningful accessible labels.

External links should follow the project's security and accessibility requirements.

---

## 7.4 `pagination.php`

**Responsibility:**

Provide reusable pagination for content listings where pagination is required.

The component should use native WordPress pagination functionality wherever practical.

---

# 8. Project Listing Architecture

The project archive will follow:

```text
archive-project.html
        ↓
Project Query
        ↓
Project Cards
        ↓
Pagination
```

The project listing must only display content that meets the relevant project specification.

The implementation should use WordPress's native query and loop capabilities rather than introducing a custom query abstraction.

---

# 9. Individual Project Architecture

An individual project page will follow:

```text
single-project.html
        ↓
Project Title
        ↓
Featured Image
        ↓
Project Metadata
        ↓
Project Content
        ↓
Project URL
```

Project information will come from the approved data model defined in **TD-002 — Content & Data Model**.

The project page should not require theme code changes when project content is added or updated.

---

# 10. Responsibility Boundaries

The following boundaries must be maintained:

| Layer | Responsibility |
|---|---|
| Template | Page-level composition |
| Template Part | Shared site structure |
| Pattern | Reusable page/section composition |
| Component | Reusable presentation element |
| WordPress Content | Portfolio content |
| `/inc/` | Supporting PHP functionality |
| `theme.json` | Global design configuration |

### Boundary Rule

A layer should not take over responsibilities belonging to another layer.

For example:

- Templates should not contain significant business logic.
- Patterns should not become complex applications.
- Components should not become general-purpose frameworks.
- Content should not be hardcoded into PHP when it should be editable through WordPress.
- `/inc/` should not be used to hide presentation logic unnecessarily.

---

# 11. Native WordPress First

The implementation should follow this preference order:

```text
Native WordPress Block
        ↓
Reusable Block Pattern
        ↓
Existing Theme Component
        ↓
Custom PHP Component
        ↓
Custom Implementation
```

A lower-level implementation should only be introduced when the higher-level option cannot satisfy the approved specification.

This prevents unnecessary custom development and keeps the theme aligned with WordPress standards.

---

# 12. Accessibility

Templates, template parts, patterns, and components must support the project's accessibility requirements.

The implementation should:

- Use semantic HTML through appropriate WordPress blocks.
- Maintain a logical heading hierarchy.
- Provide accessible navigation.
- Provide meaningful link text.
- Provide appropriate alternative text for meaningful images.
- Avoid unnecessary decorative content being exposed to assistive technologies.
- Support keyboard navigation.
- Maintain visible focus states.
- Avoid relying on color alone to communicate information.
- Maintain sufficient color contrast.
- Ensure interactive elements have accessible names.

Accessibility requirements will be validated against the project's approved accessibility specifications and Test Plan.

---

# 13. Responsive Behavior

Templates and patterns must support:

- Mobile.
- Tablet.
- Desktop.

Responsive behavior should primarily be implemented using:

- WordPress block layout capabilities.
- CSS.
- Responsive typography and spacing.
- Flexible layouts.

JavaScript should not be introduced solely to solve layout problems.

Responsive behavior must be validated during testing.

---

# 14. Performance Considerations

The template architecture should avoid unnecessary frontend overhead.

The implementation should:

- Prefer native WordPress blocks.
- Avoid unnecessary JavaScript.
- Avoid loading assets that are not required.
- Optimize project images.
- Avoid unnecessary third-party libraries.
- Keep template logic lightweight.
- Avoid excessive database queries.
- Use efficient WordPress queries for project listings.

Performance validation will be performed against the project's approved performance requirements.

---

# 15. SEO Considerations

The template architecture must support:

- Correct heading hierarchy.
- Semantic HTML.
- Crawlable navigation.
- Meaningful page titles.
- Descriptive links.
- Proper image alternative text.
- Search-engine-friendly project URLs.
- Appropriate canonical and metadata handling through the approved SEO approach.

SEO functionality should not be duplicated unnecessarily within the theme if it is already provided by an approved WordPress SEO solution.

---

# 16. Security Considerations

Template and component implementations must:

- Escape output appropriately.
- Avoid directly trusting user-controlled values.
- Use WordPress APIs wherever practical.
- Validate data where required.
- Avoid unnecessary direct database queries.
- Follow WordPress security practices.

Security responsibilities related to forms and server-side processing will be defined further in **TD-004 — WordPress Hooks & PHP Architecture**.

---

# 17. Content and Presentation Separation

Portfolio content must remain independent from the theme's presentation code.

For example:

**Preferred:**

```text
WordPress Project Content
        ↓
Template
        ↓
Project Card
```

**Avoid:**

```text
PHP Template
        ↓
Hardcoded Project Name
Hardcoded Description
Hardcoded Technologies
```

Adding or updating a portfolio project should not require editing theme PHP files.

---

# 18. Component Abstraction Rules

A component should only be created when at least one of the following is true:

1. It is reused in multiple locations.
2. It represents a clearly identifiable presentation responsibility.
3. Reuse improves maintainability.
4. The abstraction makes the implementation easier to understand.

Do not create components simply because a section contains multiple HTML elements.

For example, a unique Hero section does not automatically require a custom PHP component if it can be implemented effectively as a native WordPress pattern.

---

# 19. Out of Scope

The following are explicitly out of scope for TD-003:

- React-based frontend architecture.
- Headless WordPress.
- Custom frontend routing.
- Custom templating engines.
- Large component frameworks.
- Dependency injection containers.
- Custom page-builder architecture.
- Custom block framework unless a later requirement justifies it.
- Complex frontend state management.
- Unnecessary JavaScript-driven page composition.

Any future need for these technologies must be evaluated through the SDD change process.

---

# 20. Dependencies

TD-003 depends on:

- **ARCHITECTURE-001 — WordPress Architecture**
- **TD-001 — Theme & Folder Structure**
- **TD-002 — Content & Data Model**
- Approved functional specifications for Home, Projects, Navigation, and Contact.

---

# 21. Acceptance Criteria

TD-003 is considered complete when:

- [ ] All required page templates are defined.
- [ ] Home page composition is pattern-driven.
- [ ] Shared header, footer, and navigation are defined as template parts.
- [ ] Home page patterns are defined.
- [ ] Project listing architecture is defined.
- [ ] Individual project page architecture is defined.
- [ ] Reusable components have clear responsibilities.
- [ ] Templates do not contain unnecessary business logic.
- [ ] Patterns use native WordPress blocks wherever practical.
- [ ] Content remains independent from theme code.
- [ ] Accessibility considerations are defined.
- [ ] Responsive behavior is defined.
- [ ] Performance considerations are defined.
- [ ] SEO considerations are defined.
- [ ] Security boundaries are defined.
- [ ] No unnecessary component abstraction is introduced.
- [ ] No out-of-scope architecture has been introduced.

---

# 22. Traceability

The technical design maintains the following relationship:

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

For TD-003:

```text
Requirements
    ↓
Specifications
    ↓
ARCHITECTURE-001
    ↓
TD-001
    ↓
TD-002
    ↓
TD-003
```

Implementation tasks and tests will be mapped to TD-003 during the Implementation Planning and Testing phases.

---

# 23. Specification Change Rule

If implementation requires a template, pattern, component, or architecture that is not defined by this technical design, the change must be evaluated before implementation.

If the implementation differs from this design without updating the design, it introduces:

> **Specification drift.**

The team must decide whether to:

1. Change the implementation to match TD-003, or
2. Update TD-003 and any affected upstream specifications/requirements.

---

# 24. Decision Summary

The portfolio will use a **native WordPress Block Theme with a pattern-driven page composition model**.

The key architectural decision is:

```text
Templates
    → define page structure

Template Parts
    → define shared site structure

Patterns
    → define reusable page sections

Components
    → define genuinely reusable presentation elements

WordPress Content
    → stores portfolio information

/inc/
    → contains supporting PHP functionality
```

This provides a simple and maintainable structure while demonstrating practical Spec-Driven Development without introducing unnecessary architectural complexity.

---

**Document:** TD-003  
**Title:** Templates & Components  
**Phase:** Phase 4 — Technical Design  
**Status:** Approved