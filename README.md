# Screen Probe

A single self-contained HTML page for checking, on a real device, that

- a tap lands on the element it was aimed at,
- the screen is rendered at its true aspect ratio,
- nothing is cropped at the edges,
- and the page notices when the viewport changes size.

Useful when a remote or streamed view of a device sits between you and the screen,
or when the screen itself changes shape mid-session.

## What is on the page

| Element | What it tells you |
|---|---|
| Labelled grid (`R3C5`) filling the viewport | Tap a named cell; the log names the cell actually hit. A mismatch means coordinates are being scaled wrongly. |
| Square with an inscribed circle | Rendered as a rectangle or an ellipse when the image is stretched. |
| Corner-to-corner diagonals | Should meet exactly at the centre and touch all four corners. |
| Red border and `TL` / `TR` / `BL` / `BR` markers | A missing side or marker means the image is cropped. |
| Readout | CSS viewport, device pixel ratio, physical pixels, `screen.*`, orientation, and a resize counter with time since the last change. |
| Tap log | Last five taps, each with the cell hit and the coordinates in CSS and physical pixels. |

The readout flashes on every viewport change, so a screenshot taken afterwards shows
whether the page saw it.

## Use

Open the page and leave it full screen. `grid` cycles the density (3×5, 5×8, 7×12);
`clear` resets the log.

No build step, no dependencies, no network calls — `index.html` is the whole thing,
so it works equally from a web server, from a local file, or from anywhere you can
put one file.
