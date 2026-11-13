# TD-001 — Theme & Folder Structure

**Status:** Approved  
**Phase:** Phase 4 — Technical Design  
**Related Architecture:** ARCHITECTURE-001  
**Related ADRs:** ADR-001, ADR-003

---

## 1. Purpose

Define the initial folder structure and responsibility boundaries for the portfolio's custom WordPress Block Theme.

The structure should remain simple, maintainable, and aligned with the approved architecture and design decisions.

---

## 2. Technical Decision

The portfolio will use a **native WordPress Block Theme** with a lightweight developer-oriented structure.

The theme will use:

- WordPress block templates
- Template parts
- Block patterns
- Minimal PHP under `/inc/`
- `theme.json` as the primary design-system configuration
- Native WordPress APIs and hooks

Custom JavaScript and additional CSS files will **not** be introduced initially unless an approved requirement requires them.

---

## 3. Initial Folder Structure

```text
portfolio-theme/
├── style.css
├── theme.json
├── functions.php
│
├── templates/
│   ├── index.html
│   ├── front-page.html
│   ├── page.html
│   ├── single.html
│   ├── single-project.html
│   ├── archive-project.html
│   ├── 404.html
│   └── search.html
│
├── parts/
│   ├── header.html
│   ├── footer.html
│   └── navigation.html
│
├── patterns/
│   ├── hero.php
│   ├── about.php
│   ├── skills.php
│   ├── featured-projects.php
│   ├── experience.php
│   └── contact-cta.php
│
├── components/
│   ├── project-card.php
│   ├── project-meta.php
│   ├── social-links.php
│   └── pagination.php
│
├── assets/
│   └── images/
│
└── inc/
    ├── setup.php
    ├── enqueue.php
    ├── post-types.php
    ├── security.php
    └── contact-form.php
```

---

## 4. Folder Responsibilities

### 4.1 Root Files

#### `style.css`

Contains the required WordPress theme metadata and any minimal theme-level CSS that cannot reasonably be handled through `theme.json`.

#### `theme.json`

The primary configuration and design-system source for:

- Typography
- Colors
- Spacing
- Layout widths
- Block settings
- Global styles
- Responsive-related configuration where supported

`theme.json` is the authoritative source for the initial design system.

Separate `colors.json` or `typography.json` files will not be maintained initially.

#### `functions.php`

Acts only as a lightweight bootstrap file.

It should load the required files from `/inc/` and avoid containing significant business or presentation logic.

---

## 5. Templates

The `/templates/` directory contains page-level WordPress block templates.

### `front-page.html`

Defines the overall Home page composition.

The Home page will primarily be assembled using registered block patterns.

### `page.html`

Generic template for standard WordPress pages such as:

- About
- Contact

### `single.html`

Fallback template for standard WordPress posts.

### `single-project.html`

Template for individual Project entries.

### `archive-project.html`

Template for the Project listing/archive.

### `search.html`

Search results template.

### `404.html`

Not-found page.

### `index.html`

Fallback template required by the Block Theme architecture.

---

## 6. Template Parts

The `/parts/` directory contains reusable structural sections.

### `header.html`

Site header structure.

### `navigation.html`

Primary site navigation.

### `footer.html`

Site footer structure.

Template parts should focus on structural composition rather than business logic.

---

## 7. Block Patterns

The `/patterns/` directory contains reusable page sections.

Initial patterns:

- `hero.php`
- `about.php`
- `skills.php`
- `featured-projects.php`
- `experience.php`
- `contact-cta.php`

Patterns will primarily be used for the Home page.

Patterns should use native WordPress blocks wherever possible.

---

## 8. Components

The `/components/` directory contains reusable presentation-oriented PHP components where genuine reuse exists.

Initial candidates:

- `project-card.php`
- `project-meta.php`
- `social-links.php`
- `pagination.php`

Components should not become a generic abstraction layer.

A component should only be introduced when:

1. The presentation logic is genuinely reusable, or
2. Repetition would otherwise reduce maintainability.

Native WordPress blocks should be preferred when they provide the required functionality.

---

## 9. Supporting PHP

The `/inc/` directory contains supporting WordPress/PHP functionality.

### `setup.php`

Responsible for theme setup and supported WordPress features.

### `enqueue.php`

Responsible for registering/enqueuing theme assets when required.

No custom frontend JavaScript or additional CSS asset is required initially.

If a future approved requirement requires an asset, it will be introduced through the SDD change process.

### `post-types.php`

Responsible for registering the `project` Custom Post Type.

### `security.php`

Contains approved theme-level security functionality.

### `contact-form.php`

Contains server-side processing for the custom contact form.

---

## 10. JavaScript Strategy

No custom JavaScript is included in the initial theme structure.

This is intentional and follows **TD-006 — JavaScript & Frontend Interaction Architecture**.

JavaScript may be introduced later only when:

- An approved requirement requires it, and
- Native WordPress, semantic HTML, CSS, or browser-native behavior cannot reasonably satisfy the requirement.

If JavaScript becomes necessary, the initial location will be:

```text
assets/js/main.js
```

The file will be added only as part of the relevant implementation change.

---

## 11. CSS Strategy

The initial design system will be implemented primarily through:

```text
theme.json
```

Additional CSS will only be introduced where `theme.json` and native block styling cannot reasonably satisfy the approved design requirement.

If frontend CSS becomes necessary, it will be added through the approved asset/enqueue architecture.

Editor-specific CSS may also be introduced later if required to maintain editor/frontend consistency.

---

## 12. Responsibility Boundaries

The following boundaries apply:

| Layer | Responsibility |
|---|---|
| Template | Page-level composition |
| Template Part | Shared structural section |
| Pattern | Reusable page section |
| Component | Reusable presentation element |
| `/inc/` | Supporting PHP/WordPress functionality |
| `theme.json` | Design system and global configuration |
| WordPress Core | Content management and platform functionality |

Business logic should not be embedded into templates unless there is a clear and justified reason.

---

## 13. Architectural Constraints

The initial implementation will **not** introduce:

- React frontend
- Vue or Angular
- PHP frameworks
- Dependency injection containers
- Custom routing systems
- Custom templating engines
- Large component frameworks
- CSS frameworks
- JavaScript frameworks
- Build tooling
- Custom REST API architecture
- Headless WordPress architecture

These may only be considered if a future approved requirement demonstrates a genuine need.

---

## 14. Maintainability Principles

The theme should follow these principles:

1. Prefer WordPress core functionality.
2. Prefer native blocks before custom implementations.
3. Keep templates focused on composition.
4. Keep PHP logic outside templates where practical.
5. Avoid premature abstractions.
6. Avoid generic helper files without a clear responsibility.
7. Keep the number of dependencies low.
8. Introduce new files only when they have a defined responsibility.
9. Keep the structure understandable to another WordPress developer.

---

## 15. Accessibility Considerations

The structure must support:

- Semantic HTML
- Logical heading hierarchy
- Keyboard navigation
- Visible focus states
- Accessible navigation
- Meaningful link text
- Appropriate image alternative text
- Screen-reader compatibility

Accessibility implementation details will be validated during implementation and testing.

---

## 16. Performance Considerations

The theme should avoid unnecessary:

- JavaScript
- CSS
- Third-party libraries
- Plugins
- Network requests
- Heavy frontend dependencies

The Block Theme and `theme.json` approach should allow the site to remain lightweight.

Performance will be validated during the testing phase against the approved performance requirements.

---

## 17. Security Considerations

Theme PHP must follow WordPress security practices including:

- Input validation
- Sanitization
- Output escaping
- Nonce verification where applicable
- Capability checks where applicable
- WordPress APIs instead of unnecessary direct database access

Security implementation details are defined further in **TD-004 — WordPress Hooks & PHP Architecture**.

---

## 18. Traceability

This technical design supports:

- **ARCHITECTURE-001** — WordPress Theme Architecture
- **ADR-001** — Native WordPress Block Theme
- **ADR-003** — Minimal/Native First
- **TD-002** — Content & Data Model
- **TD-003** — Templates & Components
- **TD-004** — WordPress Hooks & PHP Architecture
- **TD-005** — CSS, Design System & Responsive Architecture
- **TD-006** — JavaScript & Frontend Interaction Architecture

---

## 19. SDD Change Rule

Any significant structural change to the theme must first be evaluated against:

**Requirement → Specification → Architecture → Technical Design**

If the implementation differs from this design without an approved change, it constitutes **specification/design drift**.

The appropriate artifact must be updated before or alongside implementation.

---

## 20. Decision Summary

The initial portfolio theme will remain intentionally lightweight:

**WordPress Block Theme + theme.json + Templates + Template Parts + Patterns + Minimal PHP**

No custom JavaScript, CSS framework, frontend framework, build system, or unnecessary abstraction will be introduced without a demonstrated requirement.