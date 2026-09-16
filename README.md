# CS180 portfolio

Open [Project 0](proj0/index.html) or [Project 1](proj1/index.html) in Brave.
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
