---
name: weniger-ui
description: Use when the user wants their site, app or screen in the style of Dieter Rams, or asks for Weniger. Reworks an existing interface (or builds a new one) with 20 principles for purpose, depth, measure, colour and motion, plus tokens for light and dark.
---

# Weniger UI (v0.5)

Weniger gives a site the look of a Dieter Rams product: warm greys, controls you can feel, one accent, and nothing placed by accident. The name is half of his motto, "Weniger, aber besser": less, but better. The approach is honest, quiet and thorough down to the last detail. Nothing is on screen without a reason, and every pixel is decided.

The skill changes the interface. It does not change what the site says or how it is organised.

Naming: say "inspired by Dieter Rams". Never use the Braun name or logo in a product name, and never claim affiliation.

## How to work

### Reworking an existing site (the usual case)

1. Take stock. Read the styles and the shared components before touching anything. List the pages, the components in use, and the current colours, type sizes, radii, shadows and motion. Note the brand accent and typeface if the site has them.
2. Tokens first. Define colour, radius, shadow and motion tokens for light and dark (see "Token starter"). Keep the site's brand accent as `--accent` if it has one; otherwise use the starter's orange.
3. Rework the shared layer: base styles, buttons, fields, cards, navigation. Most of the site changes here.
4. Go through the pages one by one and rework what the shared layer did not reach.
5. Check your own work against the 20 principles, one by one. Fix what fails before you show anything.
6. Report back (see "Report" at the end).

Leave alone, unless the user asks otherwise: copy, content, images, the logo, page structure, navigation items, routes, links and behaviour. If a principle cannot be met without changing one of these, say so in the report and do not change it.

On a large site, do steps 1 to 3 and one page, show that, and ask before going through the rest.

### Building something new

Start at step 2: tokens, then the component or screen, then the check and the report.

If the user's brand needs another accent, ground colour or typeface, change the tokens. The principles stay.

## The 20 principles

### Purpose: every element earns its place

1. **Every element has a job.** If you cannot say what it does, remove it. No decoration, no filler icons, no ornamental gradients.
2. **A label names the function.** Short, in sentence case, set beside the control it belongs to. No capitals for emphasis, no marketing words on controls.
3. **State shows without colour.** Position, depth or a lamp says on or off; colour only confirms it. Selected, pressed, disabled and focused must each be distinguishable in greyscale.
4. **One primary action per view.** Everything else steps back a level. If two things look equally important, decide.

### Depth: the eye knows what can be pressed

5. **Three levels only: sunk, resting, raised.** Sunk holds input and tracks. Resting is the surface. Raised is what you can press or move. A fourth level makes the eye stop believing any of them.
6. **Light comes from above.** A 1 px highlight on the top edge and two shadows below (one tight, one soft and offset down). Never a single grey blur on all sides.
7. **Radii are concentric.** Inner radius = outer radius minus the padding between them. A 26 px tile with 10 px padding holds a 16 px card.
8. **Pressed means lower.** A pressed or selected control sinks a level and its label moves 1 px with it. It never only changes colour.

### Measure: nothing looks placed by accident

9. **Everything sits on a 4 px grid.** Spacing comes from 4, 8, 12, 16, 24, 32, 48, 64. Controls are 36, 40 or 44 high; touch targets at least 44 on phones.
10. **Four text styles, no more.** Label, text, heading, number. Size and weight carry the hierarchy; capitals and colour do not.
11. **Content never moves its frame.** Numbers are tabular. Text may wrap or truncate with an ellipsis. Nothing overflows its card or pushes a neighbour. Size against the page or container, never the browser window.
12. **One stroke weight.** The same weight for every icon and line. Hairlines divide rows; empty space alone does not.

### Colour: the one thing that matters stands out

13. **Tokens, never raw values.** Every colour has a name and one place where it changes.
14. **One accent, used as a signal.** It marks the active thing, the primary action or a live value. If everything is orange, nothing is.
15. **No flat surfaces.** Two tones a few percent apart, top to bottom, and shadows tinted warm instead of pure black.
16. **Dark is designed, not inverted.** In the dark, raised parts get lighter, sunk parts get darker, and shadows give way to edges and highlights.

### Motion: it feels handled, not animated

17. **Springs travel, easing stays in.** Use a spring where a part moves freely. Use plain easing, with no overshoot, wherever it must stay inside a frame (a thumb in a track, a needle in a scale).
18. **Every part keeps its own rhythm.** Stagger entrances and loops. Nothing on the page changes on the same beat.
19. **Nothing jumps.** Numbers roll, lists shift to their new place, a reset eases back, a theme cross-fades.
20. **Motion answers the hand.** Feedback starts within a tenth of a second, can always be interrupted, and respects `prefers-reduced-motion`. A touch may also answer with one short tick, felt on a phone or heard as a sound: only in reply to the hand, never as the only signal, and with a way to turn it off.

## Never

- One uniform drop shadow under everything.
- Purple-to-blue gradients, glassmorphism, or glow as decoration.
- A bounce on a control that lives in a track.
- Pure black shadows or pure white cards on pure grey.
- More than one accent colour in the same view.
- Viewport units (`vw`) for sizes inside a component; use container units.
- Generic class names (`.t`, `.card`, `.on`) in anything that will be embedded next to other code. Prefix them.
- Text clipped mid-line, or a card cut off behind a fade.

## Token starter

```css
:root{
  /* ground and three levels (light) */
  --ground-a:#E8E6DF; --ground-b:#DDDAD2;
  --rest-a:#F3F1EB;  --rest-b:#EBE9E2;      /* resting tile */
  --raise-a:#FFFFFF; --raise-b:#F6F4EE;     /* raised control */
  --sunk-a:#D9D6CE;  --sunk-b:#E3E1DA;      /* sunk well */
  --fg:#161614; --mu:#5F5D56; --line:rgba(74,62,40,.14);
  --accent:#EE5A1B; --ok:#4FA36A;
  /* shadows, tinted warm */
  --sh-raise: inset 0 1px 0 #fff, 0 0 0 1px rgba(74,62,40,.07),
              0 1px 2px rgba(74,62,40,.09), 0 5px 9px -5px rgba(74,62,40,.22);
  --sh-sunk:  inset 0 1px 2px rgba(60,50,30,.18), 0 1px 0 rgba(255,255,255,.7);
  /* radii: tile, card inside 10px padding, control */
  --r-tile:26px; --r-card:16px; --r-key:12px;
}
.dark{
  --ground-a:#141413; --ground-b:#0A0A09;
  --rest-a:#252523;  --rest-b:#1C1C1A;
  --raise-a:#4A4944; --raise-b:#3A3935;
  --sunk-a:#0E0E0D;  --sunk-b:#171716;
  --fg:#F3F1EB; --mu:#A6A39A; --line:rgba(255,255,255,.08);
  --sh-raise: inset 0 1px 0 rgba(255,255,255,.14), 0 0 0 1px rgba(0,0,0,.4),
              0 1px 2px rgba(0,0,0,.35), 0 5px 9px -5px rgba(0,0,0,.7);
  --sh-sunk:  inset 0 1px 2px rgba(0,0,0,.7), 0 1px 0 rgba(255,255,255,.06);
}
```

Text styles: label 12/16 medium, text 13/18 semibold, heading 15/20 semibold, number 32/36 semibold with `font-feature-settings:'tnum'`.

## Motion starter

```css
:root{
  --soft: cubic-bezier(.22,.8,.22,1);            /* inside a frame */
  --spring: linear(0,0.006,0.025 2.8%,0.101 6.1%,0.539 18.9%,0.721 25.3%,
            0.849 31.5%,0.937 38.1%,0.968 41.8%,0.991 45.7%,1.006 50.1%,
            1.015 55%,1.017 63.9%,1.001 85.9%,1);  /* free travel */
}
.thumb-in-track{ transition: transform .55s var(--soft); }
.free-part{ transition: transform .8s var(--spring); }
.press:active{ transform: translateY(1px); transition-duration:.12s; }
@media (prefers-reduced-motion: reduce){ *{ animation:none!important; transition:none!important } }
```

A pressed key: give the control the sunk background, and put the raised surface on a `::before` that fades out when pressed. That way the change animates, and depth (not colour) carries the state.

A haptic tick (principle 20) is optional: offer it, and add it when the user wants it. Where `navigator.vibrate` exists, call `navigator.vibrate(10)` from the tap or from each step of a drag. iPhone has no vibration API. The only route there is a workaround: the finger lands on an invisible `<label>` laid over the control, and that label belongs to a hidden `<input type="checkbox" switch>`, which ticks when it flips. It gives one tick per tap and nothing while dragging, and Apple may close it, so no control may depend on it. Give a dragged control tappable steps if it should tick on iPhone.

A sound (principle 20) is optional too: offer it, and add it when the user wants it. Synthesise it with the Web Audio API, so there are no files to ship, and create the `AudioContext` inside the first tap, because a browser allows nothing sooner. Put a sound switch on the page and remember the choice. Never play a sound that is not the answer to a touch.

The sound is one soft knock: a sine that falls in pitch, with a few milliseconds of filtered noise on top. The noise is what carries it on a phone speaker.

```js
// f: register (1 = 300 Hz), d: length (1 = 70 ms), c: click, g: level, bend: where the pitch ends
function knock(ac, out, noiseBuffer, f, d, c, g, bend) {
  var t = ac.currentTime + 0.004, len = Math.max(0.018, 0.07 * d);
  var o = ac.createOscillator(), e = ac.createGain();
  o.frequency.setValueAtTime(300 * f, t);
  o.frequency.exponentialRampToValueAtTime(300 * f * (bend || 0.57), t + len);
  e.gain.setValueAtTime(0.0001, t);
  e.gain.exponentialRampToValueAtTime(0.5 * g, t + 0.002);
  e.gain.exponentialRampToValueAtTime(0.0001, t + len);
  o.connect(e); e.connect(out); o.start(t); o.stop(t + len + 0.02);
  if (!c) return;
  var n = ac.createBufferSource(), b = ac.createBiquadFilter(), ne = ac.createGain();
  n.buffer = noiseBuffer; b.type = 'bandpass'; b.frequency.value = 2600; b.Q.value = 0.9;
  ne.gain.setValueAtTime(0.24 * g * c, t); ne.gain.exponentialRampToValueAtTime(0.0001, t + 0.006);
  n.connect(b); b.connect(ne); ne.connect(out); n.start(t); n.stop(t + 0.02);
}
```

Give each kind of control its own voice, by what it is for. A large or weighty control sounds lower and longer, a small one higher and shorter, and the direction of the pitch follows the direction of the state.

| The control | f | d | c | g | Notes |
|---|---|---|---|---|---|
| Primary action | 0.62 | 1.6 | 0.8 | 1 | the one button that matters |
| Ordinary key | 1 | 1 | 1 | 0.85 | |
| Small choice (chip, radio, day, digit) | 1.5 | 0.65 | 1 | 0.7 | |
| A position (dial, segments, ruler) | 1.2 | 0.6 | 1.6 | 0.8 | pitch follows the position, one octave across the range |
| A step while dragging | 1.75 | 0.25 | 1.3 | 0.4 | pitch follows the value; at most one every 22 ms |
| Something that opens | 0.8 | 1.5 | 0.3 | 0.6 | |
| Switch on / off | 0.8 / 1.1 | 0.9 | 1.4 | 0.9 | bend 1.45 for on (rises), 0.55 for off (falls) |
| Confirmed | 1, then 1.5 | 1.3, 1.6 | 0.6 | 0.85 | two knocks, 110 ms apart |
| Refused | 0.5 | 0.8 | 0 | 0.8 | three knocks, 75 ms apart, no click |

## Responsive bento pattern

One grid, 70 px rows, 12 px gap. Make the board a container and switch columns with container queries: 12 columns from 1360 px, 6 from 700 px, 2 below. Place every tile explicitly per layout with CSS variables, so nothing reflows by accident. Keep the same row span across layouts.

## Report

When you hand work back, say in a few lines:

- what you reworked, and what you left alone on purpose;
- which of the 20 principles you checked and which, if any, you could not meet and why;
- what you verified by looking (widths, light and dark, overflow) and what you assumed;
- the tokens the user should change to make it their own.
