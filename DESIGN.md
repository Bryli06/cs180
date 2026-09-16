# Design

## Source of truth

- **Status:** Active
- **Date:** 2026-09-14
- **Product surfaces:** CS 180 portfolio landing page and Project 0 and Project 1 reports
- **Evidence reviewed:** existing `index.html`, `proj0/index.html`, shared `styles.css`, the [Fall 2026 Project 0 brief](https://cal-cs180.github.io/fa26/hw/proj0/index.html), [Project 1 brief](https://cal-cs180.github.io/fa26/hw/proj1/index.html), the local Project 1 scaffolding plan, and the approved [LaTeX.css reference](https://latex.vercel.app/) with its saved 1440×1200 capture under `.omx/artifacts/visual-ralph/project0/`

This file governs presentation and interaction. The course handout governs required academic content and deliverables.

## Brand

- **Personality:** scholarly, restrained, precise, photographic
- **Trust signals:** semantic headings, figure numbering, descriptive captions, concise method notes, and print-safe layout
- **Avoid:** app-like cards, heavy gradients, novelty fonts, decorative animation, copied course prose, and visual effects that compete with the photographs

## Product goals

- Make all three Project 0 experiments easy to scan and grade.
- Explain Project 1's alignment, image similarity, and binomial pyramids for readers who know mathematics; supply computer-vision context where needed.
- Keep Project 1 derivations beside measured photographic evidence; visibly distinguish illustrative numbers from measured results and link primary references near the claims they support.
- Present the final photographs and observations without visible editing scaffolds.
- Preserve the document-like character of the LaTeX.css reference on screen and in a printed PDF.
- **Non-goals:** in-browser image processing, a CMS, account features, or reproducing the reference site's content. Project 1 computation is an authorized private authoring step. Gradient-magnitude alignment is an optional experiment; further extensions are outside its present scope.
- **Success signals:** every required experiment has labeled figures and completed observations; no horizontal overflow at mobile width; the page prints cleanly.

## Personas and jobs

- **Student author:** review the finished report, publish through GitHub Pages, and print a PDF.
- **Course grader:** identify each part, compare image pairs, read captions and observations, and verify the public URL.
- **Classmate or visitor:** understand each experiment without course context. Project 1 assumes familiarity with standard mathematical notation and focuses on the choices behind the method.

## Information architecture

- `/index.html`: compact portfolio landing page with links to Projects 0 and 1.
- `/proj0/index.html`: title and abstract, contents, Parts 1–3, final reflection, and footer.
- The Project 0 page follows the assignment order: portrait perspective, architectural perspective compression, then dolly zoom.
- `/proj1/index.html`: descriptive title and short abstract, leading reconstruction, contents, three exposures, similarity and single-scale results, filter derivation, coarse-to-fine alignment and full results, Emir failure analysis and edge-alignment comparison, three additional photographs, offsets and timing, and linked references. Link the Emir caption to its analysis and distinguish measured checks from likely causes. Label the original gallery and measurements as the raw-intensity baseline; compare the edge experiment with crops from the same blue-coordinate region.
- Project 1 is a static report. Its photographs and measured offsets are saved in ordinary HTML; the image-processing script does not generate or export the webpage.

## Design principles

1. **Photographs are evidence.** Captions and observations sit beside the relevant figures.
2. **Document, not dashboard.** Use a single reading column, book typography, rules, and figure labels instead of product UI chrome.
3. **Sound like the author.** Use direct first-person observations grounded in the actual photographs.
4. **Print is a first-class surface.** Navigation disappears from the PDF while figures avoid awkward page breaks.
5. **Derive before naming.** Introduce a concrete need, show the simplest construction, then name it. Keep detailed mathematical explanations readable as prose and distinguish identities from engineering choices.

## Visual language

- **Color:** warm white paper, near-black ink, muted gray metadata, oxblood links, and pale ivory draft areas.
- **Typography:** LaTeX.css/Latin Modern when available, with Georgia and Times New Roman fallbacks; monospace only for filenames.
- **Spacing:** a narrow `80ch` reading measure with generous section breaks and compact caption spacing.
- **Shape/elevation:** square corners, thin rules, no shadows, and restrained observation callouts.
- **Motion:** none except the student-provided dolly-zoom GIF; respect reduced-motion preferences.
- **Imagery/iconography:** original student photographs for Project 0; attributed Prokudin-Gorskii archival scans and computed reconstructions for Project 1. Small authored diagrams may teach coordinates or sampling. No decorative generated assets or ornamental icons.

## Components

- **Document header:** centered title, author line, course and date metadata.
- **Contents:** numbered internal links matching the report order.
- **Photo pair:** responsive two-column figure comparison that stacks on narrow screens.
- **Photo frame:** bordered final `<img>` with a descriptive caption.
- **Observation:** compact left-rule callout containing the student's analysis.
- **Tokens:** custom properties in `/styles.css` own color, measure, rule, and spacing decisions.
- **Project 1 equations:** static, accessible math with concise context and wrapping on small screens; no rendering dependency.
- **Project 1 result gallery:** existing photo frames with reserved image dimensions, lazy loading below the leading figure, labeled offsets, linked archival sources, and consistent comparisons.
- **Project 1 additions:** `/proj1/styles.css` owns only report-specific equation, diagram, gallery, table, and print layout. Reuse shared tokens; do not duplicate them.

## Accessibility

- Target WCAG 2.2 AA for text contrast and keyboard access.
- Use semantic headings, landmarks, figures, captions, lists, and tables.
- Every final image has a specific visual description rather than generic filename text.
- Links retain underlines; `:focus-visible` receives a high-contrast outline.
- Mathematical displays have readable text or explicit accessible descriptions. Tables identify row and column headers; explanatory diagrams include a title and description. Color never carries a distinction without a text label.
- The page does not rely on motion. A reduced-motion preference pauses animated GIFs only when the browser supports doing so; a static first frame should still be understandable.

## Responsive behavior

- Base layout is single-column and usable from 320px upward.
- Photo comparisons become two columns at `48rem` and collapse below it.
- Wide metadata tables scroll horizontally within the reading column.
- Touch and hover present the same information; no content is hover-only.
- Print uses a clean white background, hides `.no-print`, and keeps figures and captions together where practical.

## Interaction states

- **Loading:** optimized images reserve their intrinsic proportions without scripted layout changes.
- **Empty/error:** missing final media is a publishing error and should be caught by validation.
- **Success:** every referenced media asset loads from a relative repository path; measurements describe the recorded reconstructions. No pending-result placeholders remain in a finished report.
- **Offline/slow network:** custom fallback styling keeps the report readable if the external LaTeX.css stylesheet is unavailable.
- There are no disabled controls or form submission states.

## Content voice

- First person, concise, observational, and technically grounded.
- Use “close-up,” “zoomed,” “camera position,” “focal length,” and “perspective” consistently.
- Captions state what changed; observations explain what became visually different and why.
- Keep technical explanations tied to visible evidence in the paired images.
- For Project 1, assume readers know sums, norms, dot products, and basic algebra. Explain image-specific conventions and the reasons for algorithmic choices without elementary math tutorials. Discuss uncertainty plainly; a high numerical score does not itself establish correct alignment.
- Use one descriptive heading per section. Cut repeated captions, decorative section labels, and commentary about what the report explains. State an engineering choice or limitation once, beside the relevant method or result.

## Implementation constraints

- Plain static HTML and CSS; no build step, client-side script, or new dependency.
- Relative URLs must work on GitHub Pages from the repository root, `/proj0/`, and `/proj1/`.
- LaTeX.css supplies the approved reference's base typography; `/styles.css` supplies local fallback and project-specific figures.
- The 1440×1200 reference capture and QA artifacts live under `.omx/artifacts/visual-ralph/project0/`.
- Verify HTML structure, local links, media existence, responsive overflow, and print rules before completion.
- The private uv-managed script reads the local originals and saves reconstructed JPEGs. The separate public site contains static HTML and its media, never implementation source or the private environment.
- Check Project 1 at 320, 768, and 1440 pixels and in print. Use the saved scholarly reference for visual verdicts; photography, derivations, and result galleries are intentional content differences.

## Open questions

- [x] **Student:** Confirm `Bryan Li` and the report date; impact: submission identity.
- [x] **Student:** Choose final subjects and write original observations; impact: graded content.
- [x] **Student:** Provide accurate descriptions for the selected photographs; impact: accessibility.
- [ ] **Student:** Confirm the public GitHub Pages URL before printing; impact: required PDF header.
- [ ] **Implementation owner:** Verify frozen Project 1 alignment results, timings, source attribution, and all generated figures before publication; impact: report claims and grading evidence.
