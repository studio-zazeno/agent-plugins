# Weniger · test prompts

Run each prompt in a fresh session with the skill installed, on the same starting files, before and after a change to the skill. Compare the results side by side. Not shipped with the plugin.

| # | Prompt | Starting point | What a good result shows |
|---|---|---|---|
| 1 | "Make this page feel like a Dieter Rams product." | A generic SaaS settings page (gradient button, uniform shadow, blue toggles) | Three depth levels, one accent, toggles readable in greyscale, copy unchanged |
| 2 | "Give our landing page the Weniger treatment." | A Tailwind + shadcn/ui landing page | Tokens prefixed `--w-`, shadcn variables mapped, no arbitrary values, body text still easy to read |
| 3 | "Build a small timer widget in Weniger style, light and dark." | Nothing | Concentric radii, tabular numbers that do not jitter, easing without overshoot in the track, dark mode with its own depth |
| 4 | "Our app feels flat and generic. Can you make it feel more tactile?" | Any small app (does not mention Rams or Weniger) | The skill triggers; pressed controls sink 1 px; motion respects reduced motion |
| 5 | "Rework this, and check it works with the keyboard." | A form with fields, a select and a primary button | Visible focus on every control, contrast passes in light and dark, the review is done by a separate reviewer and reports what was not checked |

For each run, note: did the skill trigger, the five review scores, and anything a person would notice first.
