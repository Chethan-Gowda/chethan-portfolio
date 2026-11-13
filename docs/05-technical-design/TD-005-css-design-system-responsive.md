# TD-005 — CSS, Design System & Responsive Architecture

**Status:** Approved  
**Phase:** Phase 4 — Technical Design  
**Related Architecture:** ARCHITECTURE-001  
**Related ADRs:** ADR-001, ADR-003  
**Related Technical Design:** TD-001, TD-003, TD-004

---

# 1. Purpose

This document defines the visual design system, CSS architecture, responsive behavior, and design-token strategy for the portfolio WordPress theme.

The design follows the approved decision:

> **Use `theme.json` as the primary design-system configuration layer and keep custom CSS minimal.**

The objective is to provide a consistent, accessible, responsive, and maintainable visual system without introducing unnecessary CSS frameworks or abstractions.

---

# 2. Design Principles

The visual architecture follows these principles:

1. `theme.json` is the primary source for design tokens.
2. Native WordPress block styling is preferred.
3. Custom CSS is introduced only when required.
4. Design values should be reusable rather than repeatedly hardcoded.
5. Responsive behavior should be handled primarily through CSS and WordPress block capabilities.
6. Accessibility must be considered while defining colors, typography, spacing, and interactive states.
7. The design should remain simple and professional.
8. The CSS architecture should be understandable without requiring a CSS framework.
9. No unnecessary frontend framework should be introduced.
10. Visual consistency should be achieved through a small set of deliberate design tokens.

---

# 3. Design System Architecture

The design system will follow:

```text
theme.json
    ↓
Design Tokens
    ↓
WordPress Global Styles
    ↓
Block Styles
    ↓
Patterns
    ↓
Minimal Custom CSS
```

The design system will primarily be configured through:

```text
theme.json
```

The existing `styles/` directory defined in TD-001 should only contain additional configuration if a demonstrated need emerges.

`theme.json` remains the authoritative design configuration file.

---

# 4. Design Tokens

The initial design system will define tokens for:

- Colors
- Typography
- Font sizes
- Font weights
- Line heights
- Spacing
- Content width
- Wide content width
- Border radius
- Borders where required
- Shadows where required

The number of tokens should remain intentionally small.

Do not create a token for every individual CSS value.

---

# 5. Color System

The color system should define semantic roles rather than isolated color values.

Example conceptual structure:

```text
Primary
Secondary
Background
Surface
Text
Muted Text
Border
Accent
Link
Focus
```

The actual color values will be finalized during the visual design stage.

### Accessibility Requirement

Color combinations must satisfy the project's accessibility requirements.

The design must not rely on color alone to communicate:

- Errors.
- Success.
- Status.
- Interactive state.
- Important information.

---

# 6. Typography

Typography will be configured through `theme.json`.

The system should define:

- Primary font family.
- Heading font family if different.
- Body font size.
- Heading sizes.
- Small text size.
- Line heights.
- Font weights.

The typography system should use a limited scale.

Example conceptual scale:

```text
Small
Body
Large
Heading 3
Heading 2
Heading 1
Display
```

The exact values will be selected during visual design implementation.

---

# 7. Typography Accessibility

Typography must support readability and accessibility.

The design should:

- Use readable font sizes.
- Maintain appropriate line height.
- Maintain sufficient contrast.
- Avoid overly long text lines.
- Avoid excessive use of uppercase text.
- Maintain clear heading hierarchy.
- Avoid relying on font weight alone to communicate meaning.

Text should remain readable when users increase browser text size.

---

# 8. Spacing System

Spacing should be defined using a small, consistent scale.

Conceptually:

```text
XS
SM
MD
LG
XL
2XL
3XL
```

The actual values will be defined in `theme.json`.

Spacing should be used consistently for:

- Section spacing.
- Component spacing.
- Card padding.
- Button spacing.
- Text relationships.
- Layout gaps.

Avoid introducing arbitrary spacing values throughout custom CSS.

---

# 9. Layout System

The theme will use a responsive content-container model.

Conceptually:

```text
Viewport
│
├── Full-width section
│
└── Content container
      ├── Main content
      └── Optional wide content
```

The design system should define:

- Content width.
- Wide content width.
- Horizontal padding.
- Section spacing.

Native WordPress layout settings should be preferred wherever practical.

---

# 10. Content Width

The theme should provide a readable maximum content width.

The exact width will be established during visual implementation.

The goal is to:

- Prevent excessively long text lines.
- Maintain visual hierarchy.
- Provide consistent alignment across sections.
- Support desktop and mobile layouts.

---

# 11. Wide Content

Certain sections may require a wider layout.

Examples may include:

- Project grids.
- Hero sections.
- Visual project content.

Wide content should still maintain appropriate viewport padding.

---

# 12. Responsive Architecture

The website must support:

- Mobile.
- Tablet.
- Desktop.

The design should follow a responsive-first approach.

Conceptually:

```text
Mobile
   ↓
Tablet
   ↓
Desktop
```

The design should not depend on a fixed desktop layout being scaled down.

---

# 13. Responsive Breakpoints

Breakpoints should be introduced only when required by the design.

Avoid creating a large number of breakpoints.

The implementation should primarily use:

- Fluid layouts.
- CSS Grid.
- Flexbox.
- Responsive WordPress block settings.
- Fluid typography where appropriate.

Breakpoints should be based on layout requirements rather than specific device models.

---

# 14. Mobile Behavior

On mobile:

- Navigation must remain usable.
- Content should stack naturally.
- Multi-column sections should collapse appropriately.
- Buttons and interactive elements must remain easy to use.
- Text must remain readable.
- Images must scale without causing horizontal overflow.
- Cards should adapt to the available width.

The implementation should avoid unnecessary JavaScript for responsive layout behavior.

---

# 15. Tablet Behavior

Tablet layouts should provide an intermediate layout where required.

Examples:

```text
Desktop:
3-column project grid

Tablet:
2-column project grid

Mobile:
1-column project grid
```

Actual layouts will be determined by the final visual design.

---

# 16. Desktop Behavior

Desktop layouts should:

- Use available space effectively.
- Maintain readable content widths.
- Avoid excessive horizontal content.
- Preserve consistent section alignment.
- Provide appropriate whitespace.

Desktop should not simply maximize the width of every element.

---

# 17. Buttons

Buttons should use the global design system.

The system should define:

- Primary button.
- Secondary button where required.
- Hover state.
- Focus state.
- Active state.
- Disabled state where applicable.

Buttons must have:

- Sufficient contrast.
- Clear labels.
- Visible focus indicators.
- Appropriate clickable area.

The design should avoid white button text unless the chosen background provides sufficient contrast and the design specification explicitly requires it.

---

# 18. Links

Links should have clearly distinguishable interactive states.

At minimum:

```text
Default
Hover
Focus
Active
```

Links must remain distinguishable from surrounding text.

The design must not rely only on subtle color differences that may be difficult for users to perceive.

---

# 19. Focus States

Keyboard focus must remain visible.

Custom CSS must not remove the browser's focus indication without providing an equally visible or better alternative.

Focus styling should be consistent across:

- Navigation.
- Buttons.
- Links.
- Form controls.
- Other interactive elements.

---

# 20. Cards

Project cards will use a consistent visual structure.

Conceptually:

```text
Project Card
├── Image
├── Title
├── Description
├── Technologies
└── Link / CTA
```

Card styling should be implemented using native block styling where practical.

Custom CSS should only be introduced for visual requirements that cannot reasonably be achieved through `theme.json` and block configuration.

---

# 21. Border Radius

Border radius should be treated as a design token.

A limited number of radius values should be defined.

Avoid having different arbitrary radius values across components.

---

# 22. Shadows

Shadows should be used sparingly.

The portfolio should not rely heavily on:

- Large shadows.
- Multiple layered effects.
- Excessive gradients.
- Decorative visual effects.

The goal is a professional and lightweight visual design.

---

# 23. CSS Architecture

Custom CSS will be kept minimal.

Where custom CSS is required, it should be organized according to responsibility.

Initial structure:

```text
assets/
└── css/
    └── editor.css
```

If frontend CSS becomes necessary beyond `theme.json`, a dedicated frontend stylesheet may be introduced through the SDD change process.

The CSS should avoid becoming a large monolithic file.

---

# 24. CSS Naming

Custom CSS classes should use clear, descriptive names.

Avoid:

```text
.red-box
.big-text
.left-section
.box1
.custom-style
```

Prefer names that describe purpose or component responsibility.

For example:

```text
project-card
project-meta
contact-form
social-links
```

Class names should not be tightly coupled to purely visual properties.

---

# 25. CSS Specificity

The CSS architecture should maintain low specificity.

Avoid excessive:

```css
!important
```

and deeply nested selectors.

Prefer:

- Classes.
- WordPress block classes.
- Theme style configuration.
- Small, targeted selectors.

---

# 26. JavaScript Boundary

JavaScript should not be used for visual styling or responsive layout when CSS can achieve the requirement.

JavaScript may be introduced for behavior that genuinely requires interaction logic.

Examples may include:

- Interactive navigation behavior not supported natively.
- Form enhancements.
- Other approved interactive functionality.

JavaScript architecture will be documented separately where necessary.

---

# 27. Theme.json Responsibilities

`theme.json` should be responsible for:

- Color palette.
- Typography.
- Font sizes.
- Spacing.
- Layout widths.
- Block-level style configuration.
- Global styles.
- Editor/frontend consistency.

The configuration should be kept readable and intentionally small.

---

# 28. Theme.json vs CSS

The following decision rule applies:

| Requirement | Preferred Solution |
|---|---|
| Global colors | `theme.json` |
| Typography | `theme.json` |
| Font sizes | `theme.json` |
| Global spacing | `theme.json` |
| Content width | `theme.json` |
| Block styles | `theme.json` |
| Simple layout | WordPress blocks |
| Responsive layout | Blocks + CSS |
| Complex visual behavior | Custom CSS if justified |
| Interaction behavior | JavaScript if required |

Custom CSS should not duplicate values already defined in `theme.json` unless there is a clear reason.

---

# 29. Editor and Frontend Consistency

The editor experience should approximate the frontend design wherever practical.

The theme should avoid a situation where:

```text
WordPress Editor
       ≠
Frontend
```

Global styles and block configuration should therefore be defined through `theme.json` whenever possible.

Editor-specific CSS should only be introduced when required.

---

# 30. Accessibility

The design system must support the project's accessibility goals.

The implementation must consider:

- Color contrast.
- Text readability.
- Focus visibility.
- Keyboard navigation.
- Touch target size.
- Heading hierarchy.
- Link distinction.
- Form control clarity.
- Reduced reliance on color.
- Responsive text behavior.
- Zoom/text resizing.

Accessibility testing will be performed during the Testing phase.

---

# 31. Reduced Motion

The design should avoid unnecessary animation.

If animation is introduced later, it must:

- Serve a meaningful purpose.
- Remain subtle.
- Not interfere with usability.
- Respect the user's `prefers-reduced-motion` preference.

Decorative animation should not be introduced merely for visual effect.

---

# 32. Images

Images should:

- Use appropriate dimensions.
- Be optimized.
- Use modern formats where practical.
- Include appropriate alternative text.
- Avoid causing layout shifts where possible.
- Be responsive.

Large images should not be unnecessarily downloaded on small screens.

Image optimization will be validated during performance testing.

---

# 33. Performance

The visual architecture should support good Core Web Vitals.

The implementation should avoid:

- Large CSS frameworks.
- Unnecessary JavaScript.
- Excessive web fonts.
- Large unoptimized images.
- Layout-shifting components.
- Heavy animation.
- Unnecessary third-party visual libraries.

The design system should remain lightweight by default.

---

# 34. Browser Compatibility

The website should support current versions of major browsers.

The implementation should prioritize modern browser capabilities supported by the project's browser requirements.

Browser-specific hacks should not be introduced unless testing demonstrates a genuine compatibility requirement.

---

# 35. Out of Scope

The following are explicitly out of scope:

- Bootstrap.
- Tailwind CSS.
- Material UI.
- Large CSS frameworks.
- CSS-in-JS.
- Sass/SCSS unless a future requirement justifies it.
- CSS utility frameworks.
- Complex design-token build pipelines.
- Frontend component libraries.
- Animation frameworks.
- Heavy visual-effects libraries.

The portfolio should not introduce a frontend build system simply to manage a small amount of CSS.

---

# 36. Dependencies

TD-005 depends on:

- **ARCHITECTURE-001 — WordPress Architecture**
- **TD-001 — Theme & Folder Structure**
- **TD-003 — Templates & Components**
- **TD-004 — WordPress Hooks & PHP Architecture**
- Approved accessibility requirements.
- Approved performance requirements.
- Final visual/design direction.

---

# 37. Acceptance Criteria

TD-005 is considered complete when:

- [ ] `theme.json` is established as the primary design-system configuration layer.
- [ ] Color token strategy is defined.
- [ ] Typography strategy is defined.
- [ ] Spacing strategy is defined.
- [ ] Layout/container strategy is defined.
- [ ] Responsive strategy is defined.
- [ ] Mobile behavior is defined.
- [ ] Tablet behavior is defined.
- [ ] Desktop behavior is defined.
- [ ] Button and link states are defined.
- [ ] Focus behavior is defined.
- [ ] Card styling approach is defined.
- [ ] CSS organization rules are defined.
- [ ] JavaScript is not used for layout unnecessarily.
- [ ] Accessibility considerations are defined.
- [ ] Performance considerations are defined.
- [ ] `theme.json` vs custom CSS responsibilities are defined.
- [ ] Unnecessary CSS frameworks are explicitly excluded.

---

# 38. Traceability

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

TD-005 is related to:

```text
ARCHITECTURE-001
        ↓
ADR-001
        ↓
ADR-003
        ↓
TD-001
        ↓
TD-003
        ↓
TD-004
        ↓
TD-005
```

Implementation tasks and tests will be mapped to TD-005 during the Implementation Planning and Testing phases.

---

# 39. Specification Change Rule

If implementation requires a visual-system or CSS approach that is not defined by this technical design, the change must be evaluated before implementation.

If implementation differs from TD-005 without updating the design:

> **This introduces specification drift.**

The team must decide whether to:

1. Change the implementation to match TD-005, or
2. Update TD-005 and any affected specifications, architecture decisions, and requirements.

---

# 40. Decision Summary

The portfolio will use:

```text
theme.json
    ↓
Primary design system
    ↓
WordPress Global Styles
    ↓
Native Block Styling
    ↓
Minimal Custom CSS
```

The design intentionally avoids introducing a CSS framework or frontend design system library.

The goal is to demonstrate that a professional responsive WordPress site can be built using the native WordPress Block Theme architecture while maintaining:

- Consistent visual design.
- Accessibility.
- Responsive behavior.
- Performance.
- Maintainability.
- Simplicity.

---

**Document:** TD-005  
**Title:** CSS, Design System & Responsive Architecture  
**Phase:** Phase 4 — Technical Design  
**Status:** Approved