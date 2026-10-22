# CS180 portfolio

Open [Project 0](proj0/index.html), [Project 1](proj1/index.html),
[Project 2](proj2/index.html), or [Project 3](proj3/index.html) in a browser.
These are ordinary static HTML pages with local image files.

The private Project 1 code is in `lab/`. Its 17 original scans are already local:

```sh
cd lab
uv run main.py
```

The script saves color JPEGs to `lab/output/pyramid-ncc/` and prints the offsets.
See [the short code README](lab/README.md) for single-scale and MSE runs.

Only the static portfolio belongs on GitHub Pages. Keep `lab/` private, and omit
original image files from the course's code submission.

Project 2 uses the same portfolio styles and includes the selected filtering,
sharpening, hybrid, and blending results. Its private notebook and image credits
are documented in [lab/proj2/README.md](lab/proj2/README.md).

Project 3 includes Parts A and B and uses the same portfolio styles. Private Colab
notebooks, checks, and results are under `lab/proj3/parta/` and `lab/proj3/partb/`.
Only the report and selected image outputs belong in the public `proj3/` folder.
