# TD-002 — Content & Data Model

**Status:** Approved  
**Phase:** Phase 4 — Technical Design  
**Architecture Reference:** ARCHITECTURE-001  
**Related Decision:** Minimal/native-first WordPress architecture

## 1. Purpose

Define how portfolio content is represented and managed in WordPress.

The content model must allow portfolio content to be managed through WordPress without requiring changes to theme code, while avoiding unnecessary custom content types or complex data structures.

---

## 2. Content Architecture

The portfolio will use the following content structure:

```text
WordPress
│
├── Pages
│   ├── Home
│   ├── About
│   └── Contact
│
├── Projects
│   ├── Project 1
│   ├── Project 2
│   └── Project 3
│
└── Navigation
```

---

## 3. Custom Post Type

A single Custom Post Type will be introduced:

```text
project
```

The `project` CPT will represent individual portfolio projects.

No additional Custom Post Types will be introduced initially.

Potential future CPTs must be justified by a new requirement and reviewed through the SDD change process.

---

## 4. Project Data Model

Each Project will contain the following information.

| Field | Type | Required | Purpose |
|---|---|---:|---|
| Title | WordPress title | Yes | Project name |
| Short Description | Text/Textarea | Yes | Brief project summary |
| Featured Image | WordPress featured image | Yes | Project visual |
| Technologies | Text | Yes | Technologies used |
| Role | Text | Yes | User's role/contribution |
| Project URL | URL | No | Link to live project when available |

The initial implementation will intentionally avoid additional project metadata.

---

## 5. Project Content

The project title and defined metadata will provide the structured information required for:

- Project listing cards
- Featured project sections
- Individual project pages
- Project archive pages

The project body/content area may be used for additional project information where required, without introducing additional custom fields.

---

## 6. Standard WordPress Pages

The following content will remain standard WordPress Pages:

- Home
- About
- Contact

These pages will use Gutenberg/block content and the theme's templates and patterns.

Skills, experience, certifications, and similar information will initially be managed as normal page content rather than separate Custom Post Types.

---

## 7. Content vs Presentation Responsibility

Content must remain independent of theme presentation.

```text
WordPress Database
        │
        ├── Pages
        └── Projects
              │
              ▼
        Theme Templates
              │
              ▼
        Patterns / Components
              │
              ▼
        Frontend
```

Changing the theme presentation must not require rewriting project content.

Similarly, adding or editing a project must not require modifying theme PHP files.

---

## 8. Taxonomy Decision

No custom taxonomy will be introduced initially.

Project categorization will only be added if a concrete requirement emerges for filtering or grouping projects.

---

## 9. Data Validation

Project metadata must be validated according to its intended type.

Examples:

- Project URL must be a valid URL.
- Required text fields must not be stored as empty values.
- Technology and role information should be stored as plain content rather than executable code.

All output must be escaped appropriately when rendered by the theme.

---

## 10. Extensibility Rule

The minimal model is intentional.

Future requirements may justify adding:

- Project categories
- Client/company
- Project date
- Industry
- Case-study fields
- Gallery
- External links

Such additions must follow the SDD change process:

```text
New Requirement
      ↓
Requirement Update
      ↓
Specification Update
      ↓
Technical Design Update
      ↓
Implementation
      ↓
Testing
```

No fields should be added simply because they might be useful later.

---

## 11. Acceptance Criteria

TD-002 is satisfied when:

1. A `project` Custom Post Type exists.
2. Projects can be created and edited through WordPress.
3. Projects contain the defined minimal metadata.
4. Project content can be displayed independently of theme code.
5. Home, About, and Contact remain standard WordPress Pages.
6. No additional CPTs are introduced without an approved requirement.
7. No custom taxonomy is introduced without a demonstrated requirement.
8. Project URLs are validated and safely rendered.
9. Project metadata is safely escaped when displayed.
10. The content model remains compatible with the approved native-first architecture.