# ARCHITECTURE-001 — WordPress Portfolio Architecture

**Project:** Personal WordPress Portfolio  
**Version:** 1.0  
**Status:** Approved  
**Phase:** Phase 3 — Architecture

---

## 1. Purpose

This document defines the high-level architecture for the personal WordPress portfolio.

The architecture is derived from:

- `VISION-001`
- `REQUIREMENTS-001`
- `SPECIFICATIONS-001`
- Approved ADRs

The architecture prioritizes simplicity, maintainability, accessibility, performance, security, and content maintainability without unnecessary enterprise-level complexity.

---

## 2. Architecture Principles

The following principles govern the architecture:

1. **Specification is the source of truth.**
2. Prefer WordPress core capabilities before introducing dependencies.
3. Keep the architecture appropriate for a personal portfolio.
4. Avoid unnecessary custom frameworks and abstractions.
5. Content should be maintainable without modifying code where required by the specifications.
6. Accessibility is an architectural concern, not a final testing activity.
7. Performance should be considered during design rather than optimized only after implementation.
8. Minimize plugin and third-party dependencies.
9. No direct development or unreviewed changes on production.
10. Architectural decisions must be documented through ADRs.
11. Implementation must remain traceable to requirements and specifications.

---

# 3. WordPress Theme Architecture

## Decision

Use a **custom WordPress Block Theme** for V1.

### Rationale

The block theme approach supports:

- Modern WordPress architecture
- Gutenberg-based content management
- Native content editing
- Reduced dependency on page builders
- Maintainable templates
- Accessibility-conscious implementation
- Performance-conscious CSS and JavaScript
- Future extensibility without introducing unnecessary frameworks

### Constraints

The theme must not become a generalized framework.

Only components and abstractions required by the portfolio should be introduced.

---

# 4. Content Architecture

The portfolio uses a hybrid content model.

## 4.1 Projects

Projects will be implemented as a **Custom Post Type**.

Projects need independent management because new projects are expected to be added over time.

Project content will support the requirements defined in:

- `SPEC-006`
- `SPEC-007`
- `SPEC-008`
- `SPEC-009`

Projects will not have separate case-study pages in V1.

---

## 4.2 Experience

Experience will remain structured portfolio content rather than a separate Custom Post Type.

The Experience section must support:

- Organization
- Job title/role
- Employment period
- Responsibilities
- Achievements
- Multiple roles within the same organization
- Identification of the current role

Content must remain editable without modifying source code.

---

## 4.3 Skills

Skills will use structured content organized into logical categories.

Examples of categories include:

- Languages
- CMS / Platforms
- Frameworks
- Architecture / Solutioning
- AI-assisted development
- AI agents and related tools

The architecture does not require proficiency ratings or numerical skill levels.

---

## 4.4 Certifications, Talks and Achievements

Certifications, presentations/talks, and professional achievements will use repeatable structured content.

Individual items must be independently addable and removable.

Separate Custom Post Types are not required unless a future requirement demonstrates a clear need for them.

---

## 4.5 Resume

The resume will be maintained as a PDF through the WordPress Media Library.

The architecture must allow the current resume to be replaced without modifying theme code.

---

## 4.6 About/Profile

The primary professional profile and About content will use standard WordPress content/Gutenberg capabilities.

The content should remain relatively simple and directly editable.

---

## 5. Content Editing Strategy

The architecture follows a **Native Gutenberg First** strategy.

### Priority order

1. WordPress core/Gutenberg capabilities
2. Existing reusable WordPress capabilities
3. ACF only when a concrete structured-content requirement justifies it
4. Custom Gutenberg blocks only when native capabilities are insufficient

No technology should be introduced merely because it is available.

This follows:

**ADR-003 — Minimal/Native First Plugin Strategy**

and

**ADR-005 — Native Gutenberg First; ACF/custom blocks only where justified.**

---

# 6. Plugin and Dependency Architecture

The portfolio follows a **Minimal/Native First** dependency strategy.

Plugins will only be introduced when:

- WordPress core does not adequately satisfy a requirement
- The plugin provides meaningful value
- It is actively maintained
- It has an acceptable security profile
- It does not introduce unnecessary performance overhead
- It remains compatible with the architecture
- Its accessibility impact is acceptable

Page-builder dependencies such as Elementor or WPBakery are not part of the architecture.

---

# 7. Contact Form Architecture

The contact form will be implemented as a **custom WordPress form** rather than through a form plugin.

The form architecture must support:

- Name
- Email
- Subject
- Message
- Server-side validation
- Input sanitization
- Output escaping
- Nonce/security protection
- Accessible validation errors
- Spam mitigation
- Email delivery
- Configurable recipient
- Success/error feedback
- Alternative contact method when delivery fails

Contact submissions must **not be stored in the WordPress database**.

The implementation should use appropriate WordPress/core APIs rather than creating unnecessary custom infrastructure.

Detailed validation, spam protection, mail delivery and error-handling design will be defined during Technical Design.

---

# 8. Environment Architecture

The project will use a controlled three-stage environment flow:

```text
Local Development
       ↓
      Git
       ↓
    Staging
       ↓
Testing / Review
       ↓
  Production
```

## Local

Used for:

- Development
- Local testing
- Theme development
- Content/model experimentation

## Git

Git is the source-control mechanism for:

- Theme source
- Configuration that belongs in version control
- Documentation
- Tests
- Specifications
- Architecture
- Implementation plans

Secrets must not be committed.

## Staging

Used for:

- Functional testing
- Responsive testing
- Accessibility testing
- Performance testing
- SEO verification
- Security verification
- Regression testing
- Stakeholder review where required

## Production

Production represents the approved version of the portfolio.

Direct development on production is prohibited.

---

# 9. Security Architecture

Security must be considered throughout the WordPress implementation.

The architecture requires:

- Secure input handling
- Sanitization
- Escaping
- Nonce protection where applicable
- Appropriate authorization checks
- No secrets in source code
- No sensitive information in client-side code
- Controlled administrative access
- Secure dependency management
- HTTPS in production
- Appropriate backup and recovery mechanisms

Detailed implementation controls will be defined during Technical Design.

---

# 10. Accessibility Architecture

Accessibility is a first-class architectural concern.

The implementation must support the requirements of:

**SPEC-025 — Accessibility Compliance**

including:

- Semantic HTML
- Keyboard accessibility
- Visible focus states
- Accessible form labels
- Accessible error messages
- Appropriate heading hierarchy
- Sufficient color contrast
- Meaningful link text
- Appropriate alternative text
- Reduced-motion consideration
- Accessible navigation

Target:

**WCAG 2.2 AA**

---

# 11. Performance Architecture

The architecture favors:

- Minimal JavaScript
- Minimal CSS
- Minimal dependencies
- Optimized assets
- Appropriate image handling
- Avoidance of unnecessary third-party resources
- Efficient WordPress queries
- Lightweight templates
- No heavy page-builder framework

Core Web Vitals requirements defined in `SPEC-027` remain architectural constraints.

Primary targets:

- LCP ≤ 2.5s
- INP ≤ 200ms
- CLS ≤ 0.1

Mobile performance is the primary consideration.

---

# 12. SEO Architecture

The architecture must support:

- Semantic HTML
- Proper heading structure
- Descriptive page titles
- Meta descriptions
- Canonical URLs
- Search-engine crawlability
- XML sitemap
- Appropriate internal linking
- Meaningful URLs
- Social sharing metadata

SEO implementation must not require unnecessary plugin dependencies.

---

# 13. Backup and Recovery

Production must have a backup and recovery strategy covering:

- WordPress database
- Uploaded media
- Relevant configuration

Backups must be tested periodically through restoration verification.

Detailed backup frequency, retention and restoration procedures will be defined during Technical Design / Deployment Planning.

---

# 14. Architecture Constraints

The following are explicitly outside the architecture for V1:

- Page builders
- User accounts
- Comments
- E-commerce
- Newsletter infrastructure
- Multilingual architecture
- Social networking
- Complex backend applications
- Large-scale CMS architecture
- GitHub API integration
- Complex animations
- Heavy media infrastructure
- Analytics infrastructure

These exclusions are derived from the approved scope and requirements.

---

# 15. Deferred Decisions

The following are intentionally deferred to Technical Design:

1. Exact WordPress directory/file structure
2. Exact Custom Post Type registration design
3. Project fields
4. Gutenberg block/pattern structure
5. Whether ACF is actually required
6. Exact custom blocks, if any
7. CSS architecture
8. JavaScript architecture
9. WordPress hooks
10. Contact form implementation details
11. Email delivery mechanism
12. Spam mitigation mechanism
13. Hosting provider
14. Staging provider/environment details
15. Deployment mechanism
16. Backup frequency and retention
17. Exact SEO implementation
18. Asset optimization strategy
19. Testing tooling

These decisions must be made during **Phase 4 — Technical Design**, not implicitly during coding.

---

# 16. Approved Architectural Decisions

| ADR | Decision | Status |
|---|---|---|
| ADR-001 | Custom WordPress Block Theme | Approved |
| ADR-002 | Hybrid Content Architecture | Approved |
| ADR-003 | Minimal/Native First Plugin Strategy | Approved |
| ADR-004 | Custom Contact Form | Approved |
| ADR-005 | Native Gutenberg First; ACF/custom blocks only when justified | Approved |
| ADR-006 | Local → Git → Staging → Production | Approved |

---

# 17. Architecture Traceability

The architecture is derived from the approved specifications.

Examples:

```text
REQ-005
  ↓
SPEC-005
  ↓
Hybrid Content Architecture
  ↓
Gutenberg / structured content
```

```text
REQ-006
  ↓
SPEC-006
  ↓
Projects CPT
  ↓
Technical project data model
```

```text
REQ-016–020
  ↓
SPEC-016–020
  ↓
Custom Contact Form Architecture
  ↓
Technical form implementation
```

```text
NFR-001–004
  ↓
SPEC-025–028
  ↓
Accessibility + Performance Architecture
  ↓
Technical implementation + testing
```

---

# 18. Architecture Status

**Phase 3 Architecture: Approved**

The architecture is intentionally simple and appropriate for a personal professional portfolio.

The next phase is:

**Phase 4 — Technical Design**

No production implementation should begin until the relevant technical design and implementation plan are approved.