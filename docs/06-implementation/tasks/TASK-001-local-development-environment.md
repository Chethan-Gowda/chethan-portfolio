# TASK-001 — Local Development Environment

## Objective

Set up and verify the local WordPress development environment for the portfolio website using LocalWP on Windows 11.

The environment must provide a working WordPress installation that can be used to develop and test the custom portfolio theme.

## References

- Architecture — WordPress local development environment
- ADR-006 — Local → Git → Staging → Production Deployment Architecture
- TD-001 — Theme & Folder Structure
- TD-004 — WordPress Hooks & PHP Architecture

## Environment

| Item | Decision |
|---|---|
| Operating System | Windows 11 |
| Local Development Tool | LocalWP |
| LocalWP Site Location | LocalWP default location |
| WordPress | Managed by LocalWP |
| Theme Location | `wp-content/themes/portfolio-theme/` |
| Version Control | Git |
| Database | LocalWP-managed |
| Web Server | LocalWP-managed |
| PHP | LocalWP-managed |
| HTTPS | LocalWP-managed where applicable |

## Scope

This task includes:

1. Create the portfolio WordPress site using LocalWP.
2. Use LocalWP's default site storage location.
3. Verify that WordPress is accessible locally.
4. Verify WordPress administrative access.
5. Verify the local WordPress installation is functioning correctly.
6. Identify the WordPress `wp-content/themes/` location where the custom theme will be created.
7. Confirm the environment is ready for TASK-002.

## Out of Scope

The following are intentionally excluded from TASK-001:

- Custom theme development
- Theme templates
- Theme styling
- Gutenberg patterns
- Project CPT
- Contact form
- SEO configuration
- Accessibility implementation
- Production configuration
- Staging configuration
- Deployment
- Git repository setup
- Custom plugins
- Custom JavaScript
- Custom CSS

These will be handled by subsequent implementation tasks.

## Acceptance Criteria

### AC-001 — Local WordPress Site Created

A WordPress site for the portfolio project exists in LocalWP.

### AC-002 — WordPress Accessible

The local site loads successfully in a browser without server or PHP errors.

### AC-003 — WordPress Administration Accessible

The WordPress administrator dashboard can be accessed successfully.

### AC-004 — Local Environment Functional

The following basic WordPress operations work:

- Login to WordPress
- Open the dashboard
- Open the site's frontend
- Create or edit a test page
- Save the page successfully
- View the page on the frontend

### AC-005 — Theme Directory Identified

The site's theme directory is accessible at:

```text
wp-content/themes/
```

The custom portfolio theme will subsequently be created under:

```text
wp-content/themes/portfolio-theme/
```

The theme itself is **not created as part of TASK-001**.

### AC-006 — No Environment Errors

The local environment does not have unresolved errors that would prevent theme development.

### AC-007 — Environment Ready for Next Task

The local WordPress installation is ready for TASK-002 — WordPress Baseline Configuration.

## Verification

The following checks must be performed before marking TASK-001 complete:

| Check | Expected Result |
|---|---|
| LocalWP site status | Running |
| Frontend URL | Loads successfully |
| `/wp-admin` | Accessible |
| WordPress login | Successful |
| Dashboard | Loads without blocking errors |
| Test page creation | Successful |
| Test page frontend | Displays successfully |
| Theme directory | Accessible |
| PHP/WordPress runtime | No blocking errors |

## Definition of Done

TASK-001 is complete when:

- The LocalWP site is running.
- WordPress frontend works.
- WordPress administration works.
- Basic content creation works.
- Theme directory has been identified.
- No blocking environment issues remain.
- All acceptance criteria have been verified.
- No specification drift has been introduced.

## Expected Output

A working LocalWP WordPress environment ready for TASK-002.

No production code is expected from this task.