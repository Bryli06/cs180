# Design

## Source of truth

- **Status:** Active
- **Date:** 2026-10-27
- **Product surfaces:** CS 180 portfolio landing page and Project 0–4 reports
- **Evidence reviewed:** existing `index.html`, `proj0/index.html`, shared `styles.css`, the [Fall 2026 Project 0 brief](https://cal-cs180.github.io/fa26/hw/proj0/index.html), [Project 1 brief](https://cal-cs180.github.io/fa26/hw/proj1/index.html), the local Project 1 scaffolding plan, and the approved [LaTeX.css reference](https://latex.vercel.app/) with its saved 1440×1200 capture under `.omx/artifacts/visual-ralph/project0/`

This file governs presentation and interaction. The course handout governs required academic content and deliverables.

Project 2 evidence: the existing Project 0/1 HTML and CSS, saved Project 1 desktop/mobile
screenshots, the Fall 2026 Project 2 handout, and the selected figures, source notes,
and measured results under the private `lab/proj2/` directory.

## Brand

- **Personality:** scholarly, restrained, precise, photographic
- **Trust signals:** semantic headings, figure numbering, descriptive captions, concise method notes, and print-safe layout
- **Avoid:** app-like cards, heavy gradients, novelty fonts, decorative animation, copied course prose, and visual effects that compete with the photographs

## Product goals

- Make all three Project 0 experiments easy to scan and grade.
- Explain Project 1's alignment, image similarity, and binomial pyramids for readers who know mathematics; supply computer-vision context where needed.
- Keep Project 1 derivations beside measured photographic evidence; visibly distinguish illustrative numbers from measured results and link primary references near the claims they support.
- Explain Project 2's seven required parts in assignment order, with source-grounded
  methods, measured checks, and the selected hybrid and blending examples.
- Present the final photographs and observations without visible editing scaffolds.
- Preserve the document-like character of the LaTeX.css reference on screen and in a printed PDF.
- **Non-goals:** in-browser image processing, a CMS, account features, or reproducing the reference site's content. Project 1 computation is an authorized private authoring step. Gradient-magnitude alignment is an optional experiment; further extensions are outside its present scope.
- **Success signals:** every required experiment has labeled figures and completed observations; no horizontal overflow at mobile width; the page prints cleanly.

## Personas and jobs

- **Student author:** review the finished report, publish through GitHub Pages, and print a PDF.
- **Course grader:** identify each part, compare image pairs, read captions and observations, and verify the public URL.
- **Classmate or visitor:** understand each experiment without course context. Project 1 assumes familiarity with standard mathematical notation and focuses on the choices behind the method.

## Information architecture

- `/index.html`: compact portfolio landing page with links to Projects 0, 1, and 2.
- `/proj0/index.html`: title and abstract, contents, Parts 1–3, final reflection, and footer.
- The Project 0 page follows the assignment order: portrait perspective, architectural perspective compression, then dolly zoom.
- `/proj1/index.html`: descriptive title and short abstract, leading reconstruction, contents, three exposures, similarity and single-scale results, filter derivation, coarse-to-fine alignment and full results, Emir failure analysis and edge-alignment comparison, three additional photographs, offsets and timing, and linked references. Link the Emir caption to its analysis and distinguish measured checks from likely causes. Label the original gallery and measurements as the raw-intensity baseline; compare the edge experiment with crops from the same blue-coordinate region.
- Project 1 is a static report. Its photographs and measured offsets are saved in ordinary HTML; the image-processing script does not generate or export the webpage.
- `/proj2/index.html`: title/abstract, a leading planet blend, contents, convolution,
  finite differences, DoG, a sigma/threshold comparison, sharpening, three selected hybrids, Gaussian/Laplacian
  stacks, three blends, reflection, and references. The selected custom hybrids
  are FREEDOM/SLAVERY and Burger King/McDonald's; all three hybrids are grayscale. The custom blends
  are red/giant pandas and Neptune/Uranus. Other trials are not portfolio selections.

## Design principles

1. **Photographs are evidence.** Captions and observations sit beside the relevant figures.
2. **Document, not dashboard.** Use a single reading column, book typography, rules, and figure labels instead of product UI chrome.
3. **Sound like the author.** Use direct first-person observations grounded in the actual photographs.
4. **Print is a first-class surface.** Navigation disappears from the PDF while figures avoid awkward page breaks.
5. **Derive before naming.** Introduce a concrete need, show the simplest construction, then name it. Keep detailed mathematical explanations readable as prose and distinguish identities from engineering choices.

## Visual language

- **Color:** warm white paper, near-black ink, muted gray metadata, oxblood links, and pale ivory draft areas.
- **Typography:** LaTeX.css/Latin Modern when available, with Georgia and Times New Roman fallbacks; monospace for filenames and the course-requested convolution snippets.
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
- **Project 2 additions:** `/proj2/styles.css` reuses the shared tokens and document
  components, adding readable kernel/stack grids, short code excerpts, and native-size
  hybrid frames with actual-size distant previews. No product-style cards or sliders.
- **Project 2 equations:** LaTeX source in `\(...\)` and `\[...\]`, rendered by
  locally bundled KaTeX. Keep the initialization script small; include upstream
  assets and license separately. No handwritten equation HTML or MathML.

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
- Project 2's full-size hybrids may scroll inside a labeled figure on narrow screens;
  their small previews must never be stretched. The document itself must not overflow.
- Project 2 groups related panels under one figure caption. Individual stack levels
  get short labels; the shared explanation appears once. Section numbers belong
  in the heading, without a separate eyebrow or repeated observation callout.
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

- Plain HTML and CSS with no build step. Project 2's user-requested LaTeX rendering
  uses bundled KaTeX and one small initialization script; no other client-side
  framework or rendering dependency is needed.
- Relative URLs must work on GitHub Pages from the repository root, `/proj0/`, and `/proj1/`.
- Project 2 uses the same relative-URL contract at `/proj2/`. Copy only selected
  public media into `proj2/images/`; never expose `lab/`, raw metadata, or the full
  implementation. The assignment explicitly requests limited convolution snippets
  in the report, so those excerpts are the documented exception.
- LaTeX.css supplies the approved reference's base typography; `/styles.css` supplies local fallback and project-specific figures.
- The 1440×1200 reference capture and QA artifacts live under `.omx/artifacts/visual-ralph/project0/`.
- Verify HTML structure, local links, media existence, responsive overflow, and print rules before completion.
- The private uv-managed script reads the local originals and saves reconstructed JPEGs. The separate public site contains static HTML and its media, never implementation source or the private environment.
- Check Project 1 at 320, 768, and 1440 pixels and in print. Use the saved scholarly reference for visual verdicts; photography, derivations, and result galleries are intentional content differences.
- Check Project 2 at 320, 768, and 1440 pixels, including image loading, anchor
  navigation, native hybrid sizes, and print layout. Use the saved Project 1 views
  as the style reference. Browser verification uses an isolated local preview of
  the new public page; the private computation directory is never served.

## Project 3 extension (2026-10-20)

- `/proj3/index.html` follows the Part A assignment order: interpolation, Gaussian
  blur, one-step denoising, velocity diagnostics, Euler denoising, conditional
  samples, guidance, image edits, text-guided edits, visual anagrams, and hybrids.
- Retain the shared document typography, color tokens, numbered figures, concise
  captions, and local KaTeX already bundled for Project 2. No new UI dependency.
- Part B follows with MNIST noising, denoising, pure-noise training, time and class
  conditioning, checkpoint samples, and the scheduler comparison. Keep plots and
  digit grids at their actual aspect ratios with one numbered caption each.
- Show individual 512-pixel results with labels. Split seven-time editing sweeps
  into readable groups with the original shown first. Hybrid distant previews
  remain 64 pixels on screen; do not enlarge them alongside full-size images.
- Distinguish measured reconstruction error from visual interpretation. Prompt
  names describe intended subjects; observations describe what the saved output
  actually shows. Keep seed, prompt, step size, guidance, and shared diagnostic
  scales explicit.
- Credit the Shirogane Blue Pond image to Jarrett Kow / 4K Wallpapers at the
  supplied source URL. Describe the monochrome drawing's white square padding
  before resizing, and the pond's reuse in the web-image experiment.
- Keep implementation, source images, model files, tensor caches, and complete
  run metadata in the private `lab/` tree. Copy selected report images into
  `proj3/images/`. Check mobile overflow and the rendered PDF before delivery.

## Project 4 extension (2026-10-27)

- `/proj4/index.html` follows Part A: source photo sets, homography equations
  and numbered correspondences, two rectifications with both interpolation
  methods, and three feather-blended mosaics. The HTML is the report's single
  source; do not duplicate its prose in a generator. Show each result once.
- Reuse the shared typography, color tokens, bordered images, numbered captions,
  local KaTeX, and navigation. Add only report-specific layout in
  `/proj4/styles.css`; no new framework or rendering dependency.
- Present images at their actual aspect ratios. Source and rectification panels
  use a three-column desktop grid and stack on mobile. Keep the skyline result
  narrower to avoid an excessively tall figure. Link images to their larger
  assets; preserve transparent mosaic boundaries.
- Show measured point-fit errors and interpolation timings from the saved run.
  Describe the mosaic landmarks and rectification corners as visually selected
  on enlarged images. State that target rectangle proportions were
  chosen, not measured. Do not claim perfect alignment or hide railing ghosting.
- Keep source code, environments, raw HEICs, and working metadata under `lab/`.
  Public `proj4/images/` contains only the selected metadata-free working photos,
  annotated figures, and computed results needed by the report.
- Verify links, math rendering, all images, 320/768/1440-pixel layouts, and print
  styles. Compare against the saved portfolio screenshots using visual-verdict.
  Preview only a public-file staging directory, never the private `lab` tree.

## Existing open questions

- [x] **Student:** Confirm `Bryan Li` and the report date; impact: submission identity.
- [x] **Student:** Choose final subjects and write original observations; impact: graded content.
- [x] **Student:** Provide accurate descriptions for the selected photographs; impact: accessibility.
- [ ] **Student:** Confirm the public GitHub Pages URL before printing; impact: required PDF header.
- [ ] **Implementation owner:** Verify frozen Project 1 alignment results, timings, source attribution, and all generated figures before publication; impact: report claims and grading evidence.
