# RASTER KVADRATNE MATRICE

**Web reconstruction of a 1987 Atari ST program by M. Sijanec**

| | |
|---|---|
| Original title | RASTER KVADRATNE MATRICE ("raster of square matrices") |
| Original author | M. Sijanec (listing signed *by M.SIJANEC 03.08.'87*) |
| Original date | 3 August 1987 |
| Original platform | Atari ST, GFA BASIC, 640 x 400 monochrome screen, mouse-driven |
| This version | Single HTML file, `Raster_kvadratne_matrice.html` |
| Runs on | Any modern browser (Chrome, Edge, Firefox, Safari), offline, no install |

---

## 1. What it is

RASTER KVADRATNE MATRICE is a small **interactive editor for square dot matrices**. You choose a size N (from 8 to 22), and the program gives you **two N x N grids of on/off cells**:

- **FORM** (shape, pattern), the main figure you draw, and
- **MASK**, a second grid of the same size that you draw separately.

You paint cells with the mouse, and the program shows the two matrices side by side as small thumbnails and in a combined **FINAL** view. The program is a graphical tool: its output is a visible dot pattern on the screen, not a calculation or a text result.

## 2. Where it comes from

This page is not the original program. It is a reconstruction made from a **scanned printout of the original GFA BASIC listing** (file `1987_Raster_kvadratne_matrice_Marjan_Sijanec.pdf`). The listing is signed *RASTER KVADRATNE MATRICE by M.SIJANEC 03.08.'87*.

What the listing itself shows:

- It was written in **GFA BASIC** for the **Atari ST** high-resolution monochrome screen (640 x 400 pixels, black and white only).
- The user interface is entirely **mouse driven**, with dialog texts in a South Slavic language (for example *BROJ ELEMENATA* = "number of elements", *INPUT NIJE DOBAR* = "input is not good", *birajte od 8 - 22* = "choose from 8 - 22").
- It uses two arrays, `Form(Kol,Kol)` and `Mask(Kol,Kol)`, where `Kol` is the number of elements per side.
- The main loop reads the mouse, sets or clears a cell (`Mous.rut`), and redraws the affected cell and the preview panels (`Draw`).
- A flag called `Boja` ("colour") toggles the screen palette, and a flag `Ponasob` switches editing on after you choose FORM or MASK.
- Four procedures for shifting the matrix (`Shift_levo`, `Shift_desno`, `Shift_gore`, `Shift_dole`, meaning left, right, up and down) exist in the listing but are **empty** (just `Return`), so the arrow buttons were not finished in this printout.
- Pencil notes on the printout mention a **ROTACIJA** (rotation) button and some coordinates. They look like planned additions and are **not** part of the printed program.

## 3. What it is used for

The listing contains **no written description of its purpose**, so the following is an interpretation from how the program is built, not a statement from the author.

The program lets you design **small binary raster patterns**: square grids where each cell is either on or off. A second grid, the mask, lets you design a companion pattern of the same size, and the program shows the combination. Tools of this kind were typically used in the 1980s for:

- designing **tile and fill patterns** and small bitmap shapes for screen or print graphics,
- designing **stencil or screen masks** that are combined with a shape,
- experimenting with how two dot patterns overlay each other (the "raster" in the title).

If you know what the original was actually used for, please tell me and I will correct this section.

## 4. How to use it

1. **Open** `Raster_kvadratne_matrice.html` in a browser.
2. **Type a number from 8 to 22** and press **Enter**. This is the number of cells per side. Any other number brings up the alert *INPUT NIJE DOBAR !! (birajte od 8 - 22)* and asks again.
3. **Draw.** Click inside the grid.
   - **Left mouse button** sets a cell to 1 (filled).
   - **Right mouse button** sets a cell to 0 (empty).
   - You can **hold the button and drag** to paint several cells.
4. **Switch matrix.** Click the **FORM** tab or the **MASK** tab at the top. The tab that is on is shown filled, and the status line reads *FORM = ON* or *MASK = ON*.
5. **See the result.** Click **START** (or the **FINAL** tab). The big grid switches to the FINAL view:
   - solid cells are on in both FORM and MASK,
   - a dense dot pattern means on in FORM only,
   - a sparse dot pattern means on in MASK only.

   The FINAL view is read-only. Click the FORM or MASK tab to return to editing.
6. **End the program.** Press any letter or number key (as in the original). Click to start again.

### Buttons

| Button | What it does |
|---|---|
| START | Shows the FINAL view (see above). |
| DEMO | Fills the current matrix with a test pattern (FORM: diagonal stripes, MASK: checkerboard). |
| COLOR | Inverts the screen (black on white / white on black), like the original `Setcolor` toggle. |
| ERASE ALL | Clears both matrices. |
| ERASE | Clears the matrix you are currently editing. |
| LEVO / DESNO / GORE / DOLE | Shift the current matrix one cell left / right / up / down, wrapping around the edges. |

The thumbnails on the right show FORM and MASK at a small scale all the time. A small additional picture below them shows the cells that are on in **both** matrices.

## 5. What is faithful and what is inferred

**Taken from the listing (reliable):**

- The size prompt and its 8 to 22 limit, with the original alert text.
- Two N x N matrices called FORM and MASK.
- Left mouse sets a cell, right mouse clears it.
- The FORM / MASK / FINAL tabs, the COLOR / ERASE ALL / ERASE buttons, and the arrow buttons.
- The COLOR palette toggle and the "any key ends the program" behavior.
- The author, title and date shown on screen.

**Approximated or inferred (check against the paper):**

- **Pixel positions.** The original computes positions with `Fn X` and `Fn Y` from variables `X1` and `Y1`. Parts of the constants in the scan are not clearly legible, so the on-screen layout here is close to the original but not pixel-exact.
- **How FORM and MASK are combined** in FINAL. The listing's drawing code uses several fill patterns for the combinations, but I could not read the exact rule, so this version shows all three cases (both / FORM only / MASK only).
- **DEMO, ERASE and ERASE ALL.** Their code is not legible in the scan. The behavior here is a reasonable guess.
- **The shift buttons** do nothing in the printed original. Here they work, as a convenience.
- The pencil-note **ROTACIJA** feature is not implemented.

## 6. Files

| File | Purpose |
|---|---|
| `Raster_kvadratne_matrice.html` | The program. Open it in a browser. |
| `Raster_kvadratne_matrice_transcription.txt` | Best-effort transcription of the original GFA BASIC listing. Uncertain tokens are marked `[?]`, unreadable blocks `[...]`. |
| `README.md` | This file. |

## 7. Limitations

- Works with mouse or trackpad. On a touch screen you can set cells (a tap sets a cell to 1) but cannot clear them, because there is no right button.
- The original saved nothing and printed nothing, and neither does this version. There is no save or export.
- The transcription of the original is partial. A higher-resolution, upright scan would allow the uncertain parts to be corrected.

## 8. Credits

- **Original program and concept:** M. Sijanec, 1987.
- **Web reconstruction:** produced with Claude from the scanned listing. All rights to the original design remain with its author.
