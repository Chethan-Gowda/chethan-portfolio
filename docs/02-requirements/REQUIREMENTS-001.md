# REQUIREMENTS-001 — Personal Professional Portfolio

**Status:** Draft for Approval  
**Version:** 1.0  
**Phase:** Phase 1 — Requirements  
**Source Vision:** VISION-001  
**Methodology:** Spec-Driven Development (SDD)

---

# 1. Purpose

This document defines the functional and non-functional requirements for the Personal Professional Portfolio website.

The requirements are derived from `VISION-001`.

These requirements define **what the website must provide** and the quality characteristics it must satisfy.

Implementation technologies, WordPress architecture, plugins, theme structure, content models, and hosting decisions are intentionally deferred to later SDD phases.

---

# 2. Requirement Priority

The project uses the following priority levels:

- **Must** — Required for V1 release.
- **Should** — Important but can be deferred if necessary without preventing the V1 release.
- **Could** — Desirable but not required for V1.

All requirements marked **Must** require acceptance criteria before implementation.

---

# 3. Functional Requirements

## 3.1 Professional Profile & Homepage

### REQ-001 — Homepage Professional Identity

**Priority:** Must

The homepage shall present the owner as a **Senior Tech Lead** and communicate his professional positioning, technical expertise, and AI expertise.

The homepage shall include:

- Name
- Senior Tech Lead title
- Professional positioning statement
- Key technology expertise
- AI / AI-assisted development expertise
- Primary call-to-action

**Acceptance Criteria:**

- The owner's name is displayed.
- The title "Senior Tech Lead" is displayed.
- A concise positioning statement is displayed.
- Key technical expertise is represented.
- AI / AI-assisted development expertise is represented.
- A primary call-to-action is available.
- The information is visible and understandable on desktop and mobile layouts.

---

### REQ-002 — Primary Contact CTA

**Priority:** Must

The website shall provide a primary call-to-action that directs visitors to the contact mechanism.

**Acceptance Criteria:**

- A primary contact CTA is available on the homepage.
- Activating the CTA takes the visitor to the contact mechanism.
- The CTA is accessible using keyboard navigation.
- The CTA has an accessible name.

The exact visual treatment and final CTA wording will be defined during specification/design.

---

### REQ-003 — Homepage About Section

**Priority:** Must

The homepage shall include a concise professional About section describing the owner's background, technical leadership experience, team leadership, technical expertise, and current focus.

**Acceptance Criteria:**

- An About section is present on the homepage.
- The section communicates professional background.
- The section communicates technical leadership/team leadership.
- The section communicates relevant technical expertise.
- The section communicates the owner's current professional focus.
- No separate About page is required for V1.

---

# 3.2 Professional Experience

### REQ-004 — Professional Experience

**Priority:** Must

The website shall provide a dedicated Experience page containing the owner's professional career history in **reverse chronological order**, with the most recent experience first.

Each relevant experience entry shall communicate:

- Role/title
- Organization
- Employment period
- Key responsibilities
- Relevant achievements or contributions

The experience history shall support multiple roles within the same organization where applicable.

**Acceptance Criteria:**

- An Experience page is available.
- Experience entries are displayed in reverse chronological order.
- The current role can be identified as current/ongoing.
- Multiple roles within the same organization can be represented.
- Each published experience entry contains the required professional information.
- Only information approved for public disclosure is published.

---

# 3.3 Skills & Technology

### REQ-005 — Technical Skills

**Priority:** Must

The website shall present the owner's relevant technical skills and technology expertise in clearly grouped areas.

The content shall cover relevant expertise such as:

- WordPress
- PHP and web technologies
- Architecture and solutioning
- AI-assisted development
- AI agents
- Development tools and platforms

**Acceptance Criteria:**

- Technical skills are available to visitors.
- Skills are grouped into understandable categories.
- The categories and technologies reflect the owner's actual expertise.
- No unsupported or misleading proficiency claims are presented.
- Skill information can be updated without modifying unrelated website functionality.

The website shall not require percentage-based or self-rated proficiency indicators.

---

# 3.4 Professional Projects

### REQ-006 — Professional and Personal Projects

**Priority:** Must

The website shall provide a Projects section containing selected relevant professional and personal/experimental projects.

Projects may represent:

- WordPress/web projects
- AI/AI-agent projects
- Architecture and technical work
- AI innovation and experiments
- Other significant work relevant to the owner's professional positioning

There shall be no artificial minimum number of projects.

**Acceptance Criteria:**

- A Projects section is available.
- Both professional and personal/experimental projects can be represented.
- Projects are selected based on relevance and professional value.
- Each published project complies with the confidentiality requirement.
- No project is published if its content is prohibited by client, employer, NDA, or other confidentiality obligations.

---

### REQ-007 — Project Presentation

**Priority:** Must

All V1 projects shall be presented within a single Projects page.

V1 shall not require:

- Project filtering
- Individual project detail pages

Each project entry shall contain enough information to understand the project without requiring navigation to another portfolio page.

**Acceptance Criteria:**

- All V1 projects are accessible from the Projects page.
- No project filtering is required.
- No individual project detail page is required.
- Each project can be understood from its published project entry.

---

### REQ-008 — Project Information

**Priority:** Must

Each published project shall provide:

- Project title
- Project category
- Project purpose or problem addressed
- Owner's role/contribution
- Relevant technologies or capabilities
- Outcome or impact where information can be publicly disclosed
- Optional external link where appropriate

**Acceptance Criteria:**

- Every published project has a title.
- Every published project has a category.
- Every published project describes its purpose/problem.
- The owner's contribution is identified.
- Relevant technologies/capabilities are identified.
- An outcome/impact is included where appropriate and publicly available.
- External links are optional and shall only be included when valid and appropriate.

---

### REQ-009 — Project Confidentiality

**Priority:** Must

The website shall not publish confidential, proprietary, restricted, or client-owned information without appropriate permission.

This includes, but is not limited to:

- Client names where restricted
- Proprietary screenshots
- Internal systems or architecture details
- Confidential business information
- Source code
- Private data
- Client logos where permission is required

**Acceptance Criteria:**

- Published project content has been reviewed for confidentiality.
- Restricted information is not publicly exposed.
- Client/project information is published only where disclosure is permitted.
- Private repositories or systems are not linked publicly without authorization.

---

# 3.5 Achievements, Certifications & Talks

### REQ-010 — Professional Achievements

**Priority:** Should

The website should present selected professional achievements and contributions that strengthen the owner's professional positioning.

**Acceptance Criteria:**

- Achievements can be presented as portfolio content.
- Published achievements are factual and supportable.
- Empty achievement sections are not displayed when no relevant content exists.

---

### REQ-011 — Certifications & Learning

**Priority:** Should

The website should present relevant certifications, professional learning, and technology upskilling.

**Acceptance Criteria:**

- Relevant certifications can be presented.
- Relevant learning/upskilling activities can be presented.
- In-progress learning can be clearly distinguished from completed certifications where applicable.
- Verification links may be provided where appropriate.
- Empty certification/learning sections are not displayed when no relevant content exists.

---

### REQ-012 — Presentations & Talks

**Priority:** Should

The website should present relevant presentations, talks, workshops, or knowledge-sharing activities.

**Acceptance Criteria:**

- Relevant talks/presentations can be presented.
- Each published item identifies its title and relevant context.
- External links may be provided where appropriate.
- Heavy embedded media is not required for V1.
- Empty sections are not displayed when no relevant content exists.

---

# 3.6 Resume

### REQ-013 — Resume PDF

**Priority:** Must

The website shall provide access to the owner's current professional resume as a downloadable PDF.

The resume shall be accessible from the homepage and primary navigation.

**Acceptance Criteria:**

- A resume link is available from the homepage.
- A resume link is available through primary navigation.
- The linked file is a PDF.
- The PDF can be successfully accessed/downloaded.
- The link clearly identifies that the resource is a PDF.
- The resume content is consistent with the current professional experience presented on the website.
- The resume contains only information approved for public distribution.

The accessibility and indexing requirements for the PDF shall be defined during specification.

---

# 3.7 Professional Links

### REQ-014 — LinkedIn

**Priority:** Must

The website shall provide a link to the owner's LinkedIn profile.

**Acceptance Criteria:**

- A valid LinkedIn link is available.
- The link points to the intended profile.
- The link has an accessible name.
- The link remains functional at release.

---

### REQ-015 — GitHub

**Priority:** Must

The website shall provide a link to the owner's GitHub profile.

V1 shall provide a profile link only and shall not require GitHub activity feeds or API integration.

**Acceptance Criteria:**

- A valid GitHub link is available.
- The link points to the intended profile.
- The link has an accessible name.
- No GitHub API/activity integration is required.

---

# 3.8 Contact

### REQ-016 — Contact Form

**Priority:** Must

The website shall provide a contact form containing the following required fields:

- Name
- Email
- Subject
- Message

**Acceptance Criteria:**

- All four fields are present.
- All four fields are required.
- The form can be completed using keyboard navigation.
- Each field has an appropriate accessible label.
- Visitors can submit a valid enquiry.

---

### REQ-017 — Contact Validation

**Priority:** Must

The contact form shall validate submitted information before accepting a submission.

Validation shall occur on the server regardless of client-side validation.

The form shall appropriately handle:

- Missing required values
- Invalid email addresses
- Whitespace-only input
- Excessively long input
- Unexpected markup/script content
- Unicode and non-Latin names
- Duplicate submissions

**Acceptance Criteria:**

- Invalid required fields prevent successful submission.
- Invalid email addresses prevent successful submission.
- Validation is enforced server-side.
- User input is handled safely.
- Legitimate Unicode names can be submitted.
- Validation errors are understandable to the visitor.

---

### REQ-018 — Contact Submission Delivery

**Priority:** Must

Valid contact form submissions shall be delivered to the owner's designated email address.

Contact submissions shall **not be stored in WordPress**.

**Acceptance Criteria:**

- A valid test submission reaches the designated recipient.
- The submission contains the visitor's submitted information.
- The submission does not depend on WordPress database storage.
- The owner's email address is not unnecessarily exposed publicly.
- Delivery failure is handled without exposing technical information to visitors.

The exact delivery mechanism shall be determined during architecture/technical design.

---

### REQ-019 — Contact Form Feedback

**Priority:** Must

The website shall provide clear feedback for contact form validation, successful submission, and failed submission.

**Acceptance Criteria:**

- Successful submission produces a clear success message.
- Invalid input produces clear validation feedback.
- Delivery failure produces a clear failure message.
- Error messages are associated with the relevant fields where applicable.
- Errors do not rely solely on colour.
- The visitor is provided with an alternative contact method when submission cannot be completed.
- Technical implementation details are not exposed to visitors.

---

### REQ-020 — Contact Spam Protection

**Priority:** Must

The contact mechanism shall reduce automated/spam submissions while maintaining accessibility, performance, privacy, and usability.

**Acceptance Criteria:**

- Legitimate visitors can submit the form without an inaccessible challenge.
- Basic automated/spam submissions are appropriately mitigated.
- Excessive repeated submissions can be controlled.
- Spam protection does not introduce an unnecessary third-party dependency.
- Any third-party service used for spam protection must be evaluated against privacy, accessibility, and performance requirements.

The specific spam protection mechanism shall be decided during architecture.

---

### REQ-021 — Privacy Notice

**Priority:** Must

The website shall provide a privacy notice explaining the collection and use of contact form information.

The notice shall explain that contact information is collected for the purpose of responding to enquiries.

**Acceptance Criteria:**

- A privacy notice is publicly accessible.
- The contact form provides access to the relevant privacy information.
- The purpose of collecting contact information is explained.
- The notice reflects the actual data-handling behavior.
- Contact form submissions are not stored in WordPress.

Applicable privacy/legal requirements shall be confirmed before production deployment.

---

# 3.9 Navigation & User Experience

### REQ-022 — Primary Navigation

**Priority:** Must

The website shall provide clear primary navigation to the main portfolio areas.

Primary navigation shall provide access to at least:

- Home
- Experience
- Projects
- Resume
- Contact

**Acceptance Criteria:**

- All required destinations are accessible through primary navigation.
- Navigation works on desktop and mobile.
- The current page/location can be identified.
- Navigation can be operated using keyboard controls.
- Navigation does not create horizontal scrolling on supported screen sizes.

---

### REQ-023 — Consistent Navigation

**Priority:** Must

Navigation shall remain consistent across the website.

**Acceptance Criteria:**

- Primary navigation appears consistently across applicable pages.
- Navigation labels remain consistent.
- Equivalent navigation controls behave consistently.
- The current page can be identified.

---

### REQ-024 — Mobile Navigation

**Priority:** Must

The website shall provide usable navigation on mobile screen sizes.

**Acceptance Criteria:**

- Navigation is usable at a minimum viewport width of 320 CSS pixels.
- Navigation does not require horizontal scrolling.
- Navigation is keyboard accessible where applicable.
- Navigation is accessible to assistive technologies.
- Interactive navigation controls have appropriate accessible names.

---

# 4. Non-Functional Requirements

## 4.1 Accessibility

### NFR-001 — WCAG Conformance

**Priority:** Must

The website shall conform to **WCAG 2.2 Level AA** requirements.

Accessibility applies to the website's public content and interactive functionality.

Accessibility considerations include, but are not limited to:

- Keyboard accessibility
- Focus visibility
- Semantic structure
- Heading hierarchy
- Form labels
- Error messaging
- Colour contrast
- Alternative text
- Accessible navigation
- Screen-reader compatibility
- Reduced-motion preferences
- Page language
- Zoom and reflow

**Acceptance Criteria:**

- No known critical accessibility blockers remain at release.
- All primary pages can be navigated using a keyboard.
- Interactive controls have accessible names.
- Forms provide accessible labels and error feedback.
- Content remains usable at increased zoom levels.
- Reduced-motion preferences are respected where motion exists.

---

### NFR-002 — Accessibility Verification

**Priority:** Must

Accessibility shall be verified using automated and manual testing before release and after significant changes.

**Acceptance Criteria:**

- Automated accessibility testing is performed.
- A keyboard-only walkthrough is completed.
- Primary pages are tested with an appropriate screen-reader/browser combination.
- Zoom/reflow behavior is checked.
- Colour contrast is checked.
- Identified critical/serious accessibility issues are resolved or formally documented before release.

Specific testing tools will be selected during the testing phase.

---

# 4.2 Performance

### NFR-003 — Core Web Vitals

**Priority:** Must

The website shall target good Core Web Vitals performance on representative production pages.

Targets:

- LCP ≤ 2.5 seconds
- INP ≤ 200 milliseconds
- CLS ≤ 0.1

Representative pages shall include:

- Home
- Experience
- Projects
- Contact

Mobile performance shall be treated as the primary performance consideration.

**Acceptance Criteria:**

- Performance is measured before production release.
- Representative pages are tested.
- Lab testing is used for pre-release validation.
- Field data is monitored after sufficient production traffic becomes available.
- Performance issues affecting the defined targets are reviewed before release.

---

### NFR-004 — Performance Efficiency

**Priority:** Must

The website shall avoid unnecessary assets, scripts, third-party services, and functionality that negatively affect performance.

**Acceptance Criteria:**

- Unused functionality is not loaded on production pages.
- Third-party services are reviewed for performance impact.
- Large media assets are appropriately optimized.
- Performance regressions are reviewed before release.

---

# 4.3 SEO

### NFR-005 — On-Page SEO

**Priority:** Must

Public pages shall implement appropriate on-page SEO fundamentals.

This shall include:

- Unique page titles
- Appropriate meta descriptions
- Appropriate heading structure
- Semantic HTML
- Descriptive URLs
- Appropriate alternative text
- Canonical URLs
- Internal linking where appropriate
- Declared page language

**Acceptance Criteria:**

- Each primary public page has an appropriate title.
- Each primary public page has an appropriate meta description.
- Each primary page has an appropriate H1.
- Canonical URLs are correctly defined.
- Page language is declared.
- Images requiring alternative text have appropriate text.

---

### NFR-006 — Search Engine Discoverability

**Priority:** Must

The production website shall expose only intended public portfolio content to search engines.

Non-production environments shall not be indexed.

Unwanted WordPress-generated content such as unused author archives, date archives, tag archives, attachment pages, or other unintended thin/duplicate pages shall not be unnecessarily exposed or indexed.

**Acceptance Criteria:**

- Production portfolio pages can be indexed.
- Non-production environments are prevented from indexing.
- Unintended archive/index pages are disabled or prevented from indexing where applicable.
- The XML sitemap contains intended public content.
- The resume PDF follows the separately defined indexing decision.

---

### NFR-007 — Social Sharing Metadata

**Priority:** Should

Primary public pages should provide appropriate social sharing metadata.

**Acceptance Criteria:**

- Primary public pages have appropriate sharing titles/descriptions.
- A suitable default sharing image is available where applicable.
- Sharing metadata does not expose confidential information.

---

# 4.4 Security

### NFR-008 — WordPress Security

**Priority:** Must

The website shall follow appropriate WordPress and web application security practices.

The implementation shall protect against common web security risks and shall include appropriate:

- Input validation
- Sanitization
- Output escaping
- Authentication protection
- Access control
- Secure contact handling
- HTTPS
- Security headers where appropriate
- Protection against unnecessary endpoint exposure

**Acceptance Criteria:**

- HTTPS is enabled for production.
- No known critical security vulnerabilities remain at release.
- Contact input is handled securely.
- Administrative access follows appropriate security practices.
- A security review/checklist is completed before release.

---

### NFR-009 — Dependency Security

**Priority:** Must

WordPress core, plugins, themes, libraries, and other third-party dependencies shall use supported versions and shall not contain known critical security vulnerabilities at release.

**Acceptance Criteria:**

- Dependencies are reviewed before release.
- No dependency with a known critical security vulnerability is knowingly deployed.
- Security updates are reviewed periodically after launch.
- Dependency additions are documented.

---

# 4.5 Responsive Design & Browser Compatibility

### NFR-010 — Responsive Design

**Priority:** Must

The website shall provide a usable and coherent experience across desktop, tablet, and mobile screen sizes.

**Acceptance Criteria:**

- The site works at approximately 320px, 768px, and 1280px+ viewport widths.
- No unintended horizontal scrolling occurs.
- Content remains readable at supported viewport sizes.
- Navigation and forms remain usable across supported sizes.
- Important functionality remains available on mobile.

---

### NFR-011 — Browser Compatibility

**Priority:** Should

The website should support the latest two major versions of mainstream:

- Chrome
- Edge
- Firefox
- Safari
- iOS Safari
- Android Chrome

**Acceptance Criteria:**

- Primary pages are tested against supported browsers.
- Core functionality works across supported browsers.
- Unlisted browsers should still provide readable content where technically feasible.

---

# 4.6 Maintainability

### NFR-012 — Maintainable Implementation

**Priority:** Must

The website shall use maintainable WordPress development practices and avoid unnecessary custom complexity.

**Acceptance Criteria:**

- The implementation follows applicable WordPress coding standards.
- WordPress core is not modified directly.
- Third-party components are not modified in ways that prevent safe updates.
- Custom functionality is documented where necessary.
- A code/review checklist is completed before release.

---

### NFR-013 — Dependency Minimization

**Priority:** Must

Every plugin, library, framework, or third-party service included in the production solution shall have a documented purpose.

**Acceptance Criteria:**

- Every production dependency has a defined purpose.
- Duplicate functionality is avoided.
- Unnecessary dependencies are removed.
- Third-party services are evaluated for performance, security, accessibility, privacy, and maintainability impact.

---

### NFR-014 — Content Maintainability

**Priority:** Must

The owner shall be able to update portfolio content without modifying application code.

This shall include, where applicable:

- Projects
- Experience
- Skills
- Certifications
- Talks
- Resume PDF
- Contact recipient configuration

**Acceptance Criteria:**

- The owner can update portfolio content through the WordPress administration interface.
- Updating content does not require modifying PHP/CSS/JavaScript code.
- Content updates do not require modifying unrelated functionality.
- The content management approach does not introduce unnecessary CMS complexity.

The specific WordPress content architecture shall be defined during the Architecture phase.

---

# 5. Content & Privacy Requirements

### REQ-025 — Public Content Readiness

**Priority:** Must

No placeholder, sample, or unfinished content shall be published on the production website.

**Acceptance Criteria:**

- All production text is final or approved.
- All production images are approved.
- The production resume is current.
- No placeholder text remains.
- No broken or missing content references remain.

---

### REQ-026 — Public Personal Information

**Priority:** Must

The website shall only publish personal information intentionally approved for public display.

**Acceptance Criteria:**

- Public contact information is deliberately selected.
- Sensitive personal information is not unintentionally exposed.
- Resume content is reviewed before publication.
- Personal information displayed on the website is consistent with the privacy approach.

---

### REQ-027 — Empty Optional Sections

**Priority:** Should

Optional content sections shall not be displayed when there is no meaningful content available.

**Acceptance Criteria:**

- Empty achievements sections are not displayed.
- Empty certification sections are not displayed.
- Empty talks sections are not displayed.
- Empty optional project content is not displayed.

---

# 6. Reliability & Error Handling

### REQ-028 — 404 Handling

**Priority:** Should

The website should provide a useful response when a visitor accesses a page that does not exist.

**Acceptance Criteria:**

- A user-friendly 404 page is provided.
- The visitor can navigate back to the main portfolio.
- The 404 page does not expose technical information.

---

### REQ-029 — Internal Link Integrity

**Priority:** Must

All internal links required for primary portfolio functionality shall resolve correctly at release.

**Acceptance Criteria:**

- No broken internal links exist on primary pages at release.
- Navigation links resolve correctly.
- Resume links resolve correctly.
- Contact CTA links resolve correctly.

---

# 7. Backup & Recovery

### NFR-015 — Backup and Recovery

**Priority:** Must

The production website and its required content shall have an appropriate backup and recovery mechanism.

**Acceptance Criteria:**

- Website content can be backed up.
- Required configuration can be restored.
- A recovery procedure is documented.
- Backup frequency is defined before production deployment.
- A restoration test is performed before or during production readiness validation.

The specific backup technology and hosting mechanism shall be decided during architecture/deployment planning.

---

# 8. SDD Process Requirements

These requirements govern the development process rather than runtime website behavior.

## PRC-001 — Requirement Traceability

**Priority:** Must

Every Must requirement shall be traceable through the SDD lifecycle:

**Requirement → Specification → Design → Implementation Task → Implementation → Test**

**Acceptance Criteria:**

- A traceability matrix exists.
- Every Must requirement has a corresponding specification.
- Every Must specification has corresponding implementation tasks.
- Every implemented Must requirement has corresponding tests.
- No unexplained gaps exist in the Must-requirement traceability chain.

---

## PRC-002 — Change Control

**Priority:** Must

Changes to approved requirements shall be explicitly reviewed for downstream impact.

Affected artifacts shall be identified, where applicable:

- Vision
- Requirements
- Specifications
- Architecture
- Technical Design
- Implementation Plan
- Tests
- Documentation

**Acceptance Criteria:**

- Requirement changes are documented.
- Impacted downstream artifacts are identified.
- Specifications are updated when required.
- Tests are updated when behavior changes.
- No intentional specification drift is left undocumented.

---

# 9. V1 Explicit Exclusions

The following functionality is explicitly out of scope for V1:

### EXC-001 — Case Studies

Full case-study content/pages are excluded from V1.

Projects will remain lightweight portfolio entries.

### EXC-002 — Project Filtering

Project filtering is excluded from V1.

### EXC-003 — Individual Project Pages

Individual project detail pages are excluded from V1.

### EXC-004 — Separate About Page

A separate About page is excluded from V1.

The About content will be presented on the homepage.

### EXC-005 — HTML Resume

An HTML resume page is excluded from V1.

The resume will be provided as a PDF.

### EXC-006 — User Accounts

User registration/login functionality is excluded.

### EXC-007 — Comments

Comments functionality is excluded.

### EXC-008 — E-commerce

E-commerce functionality is excluded.

### EXC-009 — Newsletter

Newsletter/subscription functionality is excluded.

### EXC-010 — Custom Administration Dashboard

A custom administration dashboard is excluded.

### EXC-011 — Multilingual

Multilingual functionality is excluded.

### EXC-012 — Complex Animations

Complex animation systems are excluded.

### EXC-013 — Complex Backend Applications

The portfolio shall not evolve into a complex backend application.

### EXC-014 — Social Networking

Social networking functionality is excluded.

### EXC-015 — Large-Scale CMS

The solution shall not become a general-purpose large-scale CMS.

### EXC-016 — Analytics

Analytics functionality is explicitly deferred and is not part of V1.

### EXC-017 — GitHub Integration

GitHub API/activity-feed integration is excluded. A profile link is sufficient.

### EXC-018 — Heavy Media Embedding

Heavy video/media integrations are excluded unless specifically approved later.

---

# 10. Architecture Constraints / Deferred Decisions

The following decisions have been identified but are intentionally deferred to later SDD phases.

## ARCH-DEC-001 — Content Editing

The preferred content editing experience is the **native WordPress Gutenberg/block editor**.

This is an architectural preference and shall be evaluated during the Architecture phase.

The requirements do not prescribe:

- Custom block implementation
- ACF
- Custom Post Types
- Theme structure
- Plugin selection
- Specific content storage model

---

## ARCH-DEC-002 — Contact Delivery

The technical mechanism for delivering contact form submissions is deferred to Architecture/Technical Design.

Requirements only define the outcome:

> Valid submissions must reach the designated email recipient and must not be stored in WordPress.

---

## ARCH-DEC-003 — Spam Protection

The technical spam mitigation mechanism is deferred to Architecture.

Any solution must satisfy:

- Accessibility
- Performance
- Privacy
- Security
- Usability

---

## ARCH-DEC-004 — Hosting

Hosting/platform selection is deferred to Architecture and Deployment planning.

---

# 11. Traceability to Vision

| Vision Area | Requirement Coverage |
|---|---|
| Professional identity | REQ-001, REQ-003 |
| Career experience | REQ-004 |
| Technical expertise | REQ-005 |
| WordPress projects | REQ-006 to REQ-009 |
| AI / AI-agent work | REQ-006 to REQ-009 |
| Architecture/technical work | REQ-006 to REQ-009 |
| AI innovation/experiments | REQ-006 to REQ-009 |
| Achievements | REQ-010 |
| Certifications/learning | REQ-011 |
| Presentations/talks | REQ-012 |
| Resume | REQ-013 |
| LinkedIn | REQ-014 |
| GitHub | REQ-015 |
| Contact | REQ-016 to REQ-021 |
| Navigation | REQ-022 to REQ-024 |
| Accessibility | NFR-001, NFR-002 |
| Performance | NFR-003, NFR-004 |
| SEO | NFR-005 to NFR-007 |
| Security | NFR-008, NFR-009 |
| Responsive | NFR-010, NFR-011 |
| Maintainability | NFR-012 to NFR-014 |
| Privacy/content | REQ-025 to REQ-027 |
| Reliability | REQ-028, REQ-029 |
| Backup/recovery | NFR-015 |
| SDD traceability | PRC-001, PRC-002 |

---

# 12. Requirements Approval

**Status:** Pending Owner Approval

Before this requirements document is marked **Approved**, the owner shall review:

1. Functional requirements
2. Non-functional requirements
3. Acceptance criteria
4. Explicit exclusions
5. Deferred architecture decisions
6. Traceability to `VISION-001`

Once approved, this document becomes the baseline for **Phase 2 — Specification**.

Any subsequent change shall follow the project's SDD change-control process.