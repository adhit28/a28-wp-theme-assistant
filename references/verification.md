# Theme verification

Scale checks to changed behavior and available runtime. Fix observed defects before handing off; clearly report checks blocked by missing WordPress, design access, or dependencies.

## Static and build checks

- Run PHP syntax checks on changed PHP files and existing relevant lint/build commands. Validate Twig through installed tooling or actual rendering.
- Check changed ACF definitions parse and have stable unique keys, intended locations, and matching return formats.
- Confirm asset URLs/build manifests and Composer bootstrap match the deployment workflow. Do not invent a test framework solely for a minor edit.

## WordPress behavior

- Exercise requested pages and relevant fallbacks: front page versus blog index, single/page, archives, search results/no results, pagination, and 404 where affected.
- Verify registered menus, links, calls to action, content filtering, plugin hooks, responsive images, and missing optional fields/media.
- When authorized in a local/test runtime, verify ACF fields appear in the correct editor, save content, and preview the rendered result. Avoid production content edits as testing.
- Check PHP logs and browser console/network failures. Verify missing required dependencies fail with an actionable message rather than an undefined class/function fatal.

## Design and usability

- Compare rendered screenshots with the relevant Figma frames at matching sizes and content. Check typography, layout, spacing, crop, assets, and specified interaction states.
- Check narrow and wide widths, long headings, empty optional sections, keyboard navigation, focus visibility, semantic controls, and horizontal overflow.
- Use existing browser tools and project browser versions. For Puppeteer on macOS prefer the project's matching Headless Shell with `headless: 'shell'` unless a different browser is explicitly required. Do not set a global browser executable. If sandbox startup is blocked, request narrow test permission instead of repeated launches or weakening application security.

## Handoff

Summarize pages/components delivered, how editors change their content, tested behavior, remaining design deviations, and installation/build dependencies. State separately if editor save/preview or visual comparison could not be performed. Do not activate or deploy a theme outside the user's authorization.
