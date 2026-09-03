# Design

## Source of truth

- **Status:** Active
- **Date:** 2026-09-02
- **Product surfaces:** CS 180 portfolio landing page and Project 0 write-up
- **Evidence reviewed:** the existing static repository, the [Fall 2026 Project 0 brief](https://cal-cs180.github.io/fa26/hw/proj0/index.html), and the approved [LaTeX.css reference](https://latex.vercel.app/)

This file governs presentation and interaction. The course handout governs required academic content and deliverables.

## Brand

- **Personality:** scholarly, restrained, precise, photographic
- **Trust signals:** semantic headings, figure numbering, descriptive captions, concise method notes, and print-safe layout
- **Avoid:** app-like cards, heavy gradients, novelty fonts, decorative animation, copied course prose, and visual effects that compete with the photographs

## Product goals

- Make all three Project 0 experiments easy to scan and grade.
- Present the final photographs and observations without visible editing scaffolds.
- Preserve the document-like character of the LaTeX.css reference on screen and in a printed PDF.
- **Non-goals:** image processing, a CMS, account features, or reproducing the reference site's content.
- **Success signals:** every required experiment has labeled figures and completed observations; no horizontal overflow at mobile width; the page prints cleanly.

## Personas and jobs

- **Student author:** review the finished report, publish through GitHub Pages, and print a PDF.
- **Course grader:** identify each part, compare image pairs, read captions and observations, and verify the public URL.
- **Classmate or visitor:** understand the perspective experiment without course context.

## Information architecture

- `/index.html`: compact portfolio landing page with a link to Project 0.
- `/proj0/index.html`: title and abstract, contents, Parts 1–3, final reflection, and footer.
- The Project 0 page follows the assignment order: portrait perspective, architectural perspective compression, then dolly zoom.

## Design principles

1. **Photographs are evidence.** Captions and observations sit beside the relevant figures.
2. **Document, not dashboard.** Use a single reading column, book typography, rules, and figure labels instead of product UI chrome.
3. **Sound like the author.** Use direct first-person observations grounded in the actual photographs.
4. **Print is a first-class surface.** Navigation disappears from the PDF while figures avoid awkward page breaks.

## Visual language

- **Color:** warm white paper, near-black ink, muted gray metadata, oxblood links, and pale ivory draft areas.
- **Typography:** LaTeX.css/Latin Modern when available, with Georgia and Times New Roman fallbacks; monospace only for filenames.
- **Spacing:** a narrow `80ch` reading measure with generous section breaks and compact caption spacing.
- **Shape/elevation:** square corners, thin rules, no shadows, and restrained observation callouts.
- **Motion:** none except the student-provided dolly-zoom GIF; respect reduced-motion preferences.
- **Imagery/iconography:** original student photographs only; no ornamental icons are needed.

## Components

- **Document header:** centered title, author line, course and date metadata.
- **Contents:** numbered internal links matching the report order.
- **Photo pair:** responsive two-column figure comparison that stacks on narrow screens.
- **Photo frame:** bordered final `<img>` with a descriptive caption.
- **Observation:** compact left-rule callout containing the student's analysis.
- **Tokens:** custom properties in `/styles.css` own color, measure, rule, and spacing decisions.

## Accessibility

- Target WCAG 2.2 AA for text contrast and keyboard access.
- Use semantic headings, landmarks, figures, captions, lists, and tables.
- Every final image has a specific visual description rather than generic filename text.
- Links retain underlines; `:focus-visible` receives a high-contrast outline.
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
- **Success:** all five referenced media assets load from relative repository paths.
- **Offline/slow network:** custom fallback styling keeps the report readable if the external LaTeX.css stylesheet is unavailable.
- There are no disabled controls or form submission states.

## Content voice

- First person, concise, observational, and technically grounded.
- Use “close-up,” “zoomed,” “camera position,” “focal length,” and “perspective” consistently.
- Captions state what changed; observations explain what became visually different and why.
- Keep technical explanations tied to visible evidence in the paired images.

## Implementation constraints

- Plain static HTML and CSS; no build step, client-side script, or new dependency.
- Relative URLs must work on GitHub Pages from both the repository root and `/proj0/`.
- LaTeX.css supplies the approved reference's base typography; `/styles.css` supplies local fallback and project-specific figures.
- The 1440×1200 reference capture and QA artifacts live under `.omx/artifacts/visual-ralph/project0/`.
- Verify HTML structure, local links, media existence, responsive overflow, and print rules before completion.

## Open questions

- [x] **Student:** Confirm `Bryan Li` and the report date; impact: submission identity.
- [x] **Student:** Choose final subjects and write original observations; impact: graded content.
- [x] **Student:** Provide accurate descriptions for the selected photographs; impact: accessibility.
- [ ] **Student:** Confirm the public GitHub Pages URL before printing; impact: required PDF header.
