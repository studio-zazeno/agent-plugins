# DESIGN.md

The design bar for this project. Whoever builds reads it before touching the interface; a separate reviewer scores the built page against it. One file, so both work to the same standard.

Make it yours: change the examples, add your own picks, tighten a score. Weniger only needs the five criteria to stay.

## Principles

The look and the rules come from the 20 principles in the Weniger skill (`weniger-ui/SKILL.md`). This file does not repeat them; it says how they are checked.

## Tokens

Every colour, radius, shadow and motion value comes from a token, for light and dark. Four text styles: label, text, heading, number (with tabular figures).

## Hard checks

Check these first. If one fails, fix it before anyone scores the page.

- No raw colour values (`#hex`, `rgb()`, `hsl()`) outside the token block.
- Spacing on the 4 px grid: 4, 8, 12, 16, 24, 32, 48, 64.
- No `vw` units inside a component.
- A `prefers-reduced-motion` rule wherever there is motion.
- Every control shows a visible focus ring when reached with the keyboard.
- Text contrast at least 4.5:1, or 3:1 for text from 24 px (19 px bold), in light and dark. Text on the accent included.
- No serious or critical accessibility issues, in light and dark.

## Quality bar

Five criteria, one per group of principles. The reviewer scores each from 1 to 5 on the built page, in a browser, at 390, 768 and 1280 px, light and dark. Every score needs evidence: the element and what the reviewer saw. Pass means every criterion scores 4 or higher.

### 1. Purpose (principles 1–4)
Every element has a job, labels name functions, state reads in greyscale, one primary action per view.
- **5**: Nothing could be removed. In greyscale every state is still clear. One action leads each view.
- **3**: Mostly clean, but a decorative element, a vague label or two competing actions remain.
- **1**: Filler icons or ornament, marketing words on controls, state shown by colour alone.

### 2. Depth (principles 5–8)
Three levels (sunk, resting, raised), light from above, concentric radii, pressed means lower.
- **5**: Every pressable thing looks raised; pressed controls sink and their label moves 1 px. Inner radii match the outer radius minus the padding.
- **3**: The levels read, but a shadow is uniform, a radius is off, or a press only changes colour.
- **1**: Flat or one blur under everything; you cannot tell what can be pressed.

### 3. Measure (principles 9–12)
4 px grid, four text styles, content never moves its frame, one stroke weight.
- **5**: Nothing overflows or reflows at any of the three widths; numbers are tabular; strokes are equal.
- **3**: Aligned overall, but one fifth text style, a number that jitters, or a cramped card at one width.
- **1**: Text clipped mid-line, cards cut off, mixed strokes, sizes that look guessed.

### 4. Colour (principles 13–16)
Tokens only, one accent as a signal, no flat surfaces, dark designed rather than inverted.
- **5**: The accent marks only the active thing or the primary action. Surfaces have two close tones. Dark mode has its own depth.
- **3**: The accent shows up in places that are not signals, or dark mode looks partly inverted.
- **1**: Several accents, pure black shadows, pure white cards on grey, decorative gradients or glow.

### 5. Motion (principles 17–20)
Springs travel, easing stays in its frame, own rhythm per part, nothing jumps, motion answers the hand.
- **5**: Thumbs in tracks ease without overshoot; free parts spring; entrances are staggered; feedback starts within 100 ms and can be interrupted; reduced motion is respected.
- **3**: Mostly right, but something moves on the same beat as another, or one value jumps.
- **1**: Bounce in a track, everything animating at once, motion that ignores the hand.

## How the reviewer works

- The reviewer is not the builder. It gets this file and the page, not the builder's notes or reasoning.
- It looks for the weakest point in each criterion before it looks for what works.
- No evidence, no score. What it could not see (a width, dark mode, a state), it names as not checked; it does not guess.
- Below 4 on any criterion: the builder fixes it and the reviewer scores again. At most three rounds; then the last scores go to the person who asked, and they decide.

## Examples

Calibration for the reviewer.

Always a fail:
- One uniform drop shadow under everything.
- Purple-to-blue gradients, glassmorphism, or glow as decoration.
- A bounce on a control that lives in a track.
- More than one accent colour in the same view.
- Text clipped mid-line, or a card cut off behind a fade.

Your picks: add an entry each time you choose between two variants: what you chose, what you turned down, and one line on why.
- _(none yet)_

---

This template comes with Weniger by studio zazeno ([zazeno.com/weniger](https://zazeno.com/weniger)). Unlike the skill, it is dedicated to the public domain ([CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/)): change it, keep it in your repository, no credit needed.
