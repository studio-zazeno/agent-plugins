# Weniger in Tailwind and shadcn/ui

The principles do not change per stack. Only where the tokens live does.

## Name clash first

shadcn/ui already has a variable called `--accent`, and it means something else: a quiet hover surface, not the one signal colour. In a project with shadcn/ui, prefix every Weniger token with `w-` (`--w-accent`, `--w-raise-a`, `--w-sh-raise`), so the two never meet. Do the same in any project that already has tokens with these names.

## shadcn/ui

Keep the components; point their variables at Weniger's tokens, in light and in dark.

```css
:root, .dark, [data-theme="dark"]{
  --background: var(--w-ground-a);   --foreground: var(--w-fg);
  --card: var(--w-rest-a);           --card-foreground: var(--w-fg);
  --popover: var(--w-raise-a);       --popover-foreground: var(--w-fg);
  --primary: var(--w-accent);        --primary-foreground: var(--w-on-accent, #fff);
  --secondary: var(--w-raise-a);     --secondary-foreground: var(--w-fg);
  --muted: var(--w-sunk-a);          --muted-foreground: var(--w-mu);
  --accent: var(--w-rest-b);         --accent-foreground: var(--w-fg);  /* shadcn's hover surface */
  --border: var(--w-line);           --input: var(--w-line);
  --ring: var(--w-accent);
  --radius: var(--w-r-key);
}
```

Then, in the component files themselves:

- **Button and Card:** replace the `shadow-xs` / `shadow-sm` with the raised shadow, and give pressed and selected states the sunk background. A press moves the button down 1 px (`active:translate-y-px`).
- **Input, Select, Slider track, Switch track:** sunk background and the sunk shadow; the thumb is raised.
- **Radii:** shadcn sets one radius for everything. Weniger's radii are concentric (principle 7): set the tile, card and key radius per component, not one value for all.

## Tailwind v4

Map the tokens once in `@theme`, then use them as ordinary classes.

```css
@theme inline{
  --color-ground: var(--w-ground-a);
  --color-rest: var(--w-rest-a);
  --color-raise: var(--w-raise-a);
  --color-sunk: var(--w-sunk-a);
  --color-fg: var(--w-fg);
  --color-mu: var(--w-mu);
  --color-line: var(--w-line);
  --color-signal: var(--w-accent);
  --radius-tile: var(--w-r-tile);
  --radius-card: var(--w-r-card);
  --radius-key: var(--w-r-key);
  --shadow-raise: var(--w-sh-raise);
  --shadow-sunk: var(--w-sh-sunk);
}
```

Now `bg-raise shadow-raise rounded-key` is a raised key, and `bg-sunk shadow-sunk` a well. The signal colour is called `signal`, not `accent`, so it never mixes with shadcn's.

- **Two tones per surface (principle 15):** `bg-linear-to-b from-(--w-rest-a) to-(--w-rest-b)`. Put it in a component class instead of repeating it on every element.
- **Spacing:** Tailwind's scale already steps in 4 px (`p-1` is 4 px). Use 1, 2, 3, 4, 6, 8, 12, 16 only, which is the 4, 8, 12, 16, 24, 32, 48, 64 of principle 9.
- **No arbitrary values** (`p-[13px]`, `text-[#333]`): they are raw values with a different name (principle 13).

## Tailwind v3

The same mapping goes in `theme.extend` in `tailwind.config.js`, with the values written as `var(--w-…)`.
