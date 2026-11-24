---
name: weniger-ui
description: Use when the user wants their site, app or screen in the style of Dieter Rams, or asks for Weniger, or wants an interface that feels tactile, quiet and precise instead of flat or generic. Reworks an existing interface (or builds a new one) with 20 principles for purpose, depth, measure, colour and motion, plus tokens for light and dark.
license: "© 2026 studio zazeno. CC BY-ND 4.0: use it, also at work, and share it unchanged, with credit and a link to zazeno.com/weniger. https://creativecommons.org/licenses/by-nd/4.0/"
metadata:
  version: "0.7"
---

# Weniger UI

Weniger gives a site the look of a Dieter Rams product: warm greys, controls you can feel, one accent, and nothing placed by accident. The name is half of his motto, "Weniger, aber besser": less, but better. The approach is honest, quiet and thorough down to the last detail. Nothing is on screen without a reason, and every pixel is decided.

The skill changes the interface. It does not change what the site says or how it is organised.

Naming: say "inspired by Dieter Rams". Never use the Braun name or logo in a product name, and never claim affiliation.

## How to work

### Reworking an existing site (the usual case)

1. Take stock. Read the styles and the shared components before touching anything. List the pages, the components in use, and the current colours, type sizes, radii, shadows and motion. Note the brand accent and typeface if the site has them. Look for a `DESIGN.md` in the project: if there is one, it is the bar your work is scored against. If there is none, offer to add the template that comes with this skill (`DESIGN.md`, next to this file); add it only when the user agrees.
2. Tokens first. Define colour, radius, shadow and motion tokens for light and dark (see "Token starter"). Keep the site's brand accent as `--accent` if it has one; otherwise use the starter's orange.
3. Rework the shared layer: base styles, buttons, fields, cards, navigation. Most of the site changes here.
4. Go through the pages one by one and rework what the shared layer did not reach.
5. Have it scored by someone who did not build it (see "Review"). Fix what scores below 4 and have it scored again, at most three rounds, before you show anything.
6. Report back (see "Report" at the end).

`examples.md` next to this file shows one rework from start to report: read it before your first one.

Leave alone, unless the user asks otherwise: copy, content, images, the logo, page structure, navigation items, routes, links and behaviour. If a principle cannot be met without changing one of these, say so in the report and do not change it.

On a large site, do steps 1 to 3 and one page, show that, and ask before going through the rest.

### Building something new

Start at step 2: tokens, then the component or screen, then the review and the report.

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
/* dark: use the switch the site already has */
.dark, [data-theme="dark"]{
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

If the site has no dark switch, follow the system: put the same dark values inside `@media (prefers-color-scheme: dark){ :root{ … } }`.

Text styles: label 12/16 medium, text 13/18 semibold, heading 15/20 semibold, number 32/36 semibold with `font-feature-settings:'tnum'`.

## Motion starter

```css
:root{
  --t-travel:.55s; --t-spring:.8s; --t-fade:.2s;
  --soft: cubic-bezier(.22,.8,.22,1);            /* inside a frame */
  --spring: linear(0,0.006,0.025 2.8%,0.101 6.1%,0.539 18.9%,0.721 25.3%,
            0.849 31.5%,0.937 38.1%,0.968 41.8%,0.991 45.7%,1.006 50.1%,
            1.015 55%,1.017 63.9%,1.001 85.9%,1);  /* free travel */
}
.thumb-in-track{ transition: transform var(--t-travel) var(--soft); }
.free-part{ transition: transform var(--t-spring) var(--spring); }
.fade{ transition: opacity var(--t-fade) ease; }
.press:active{ transform: translateY(1px); transition-duration:.12s; }
@media (prefers-reduced-motion: reduce){
  :root{ --t-travel:.01ms; --t-spring:.01ms; --t-fade:.12s; }
  *,*::before,*::after{ animation-iteration-count:1!important; scroll-behavior:auto!important; }
}
```

With reduced motion, nothing travels and nothing loops, but a fade stays, shortened: the change is still seen, without the movement. Durations go to .01 ms rather than zero, so scripts that wait for a transition to end still hear it.

A pressed key: give the control the sunk background, and put the raised surface on a `::before` that fades out when pressed. That way the change animates, and depth (not colour) carries the state.

A touch may also answer with a tick or a sound (principle 20). Both are optional; offer them, and when the user wants one, read `touch.md` next to this file.

For a board of tiles, read `bento.md`. For Tailwind or shadcn/ui, read `stacks.md` before you write the tokens.

## Review

An agent that checks its own work tends to approve it. So the check is done by a separate reviewer, against the five criteria in `DESIGN.md` (the project's own, or the template next to this file).

- **Who:** if you can start a subagent, start a fresh one. Give it `DESIGN.md` and the address of the built page, nothing else: not your notes, not your reasoning, not what you hoped to achieve. If you cannot, do a separate pass after the build, with only `DESIGN.md` and the page in front of you, and say in the report that the review was not independent.
- **How:** in a browser, at 390, 768 and 1280 px, light and dark. Score purpose, depth, measure, colour and motion from 1 to 5, each with evidence: the element and what was seen. Look for the weakest point first.
- **No evidence, no score.** Whatever could not be seen (no browser, no dark mode, a state that never showed), name as not checked; never fill it in from the code or from memory.
- **Pass** is a 4 or higher on every criterion. Below that, fix and score again. After three rounds, stop and hand the last scores to the user; the call is theirs.

## Report

When you hand work back, say in a few lines:

- what you reworked, and what you left alone on purpose;
- the review: the five scores with their evidence, who scored (a subagent or a separate pass), how many rounds it took, and anything not checked;
- which principles, if any, you could not meet and why;
- the tokens the user should change to make it their own.
