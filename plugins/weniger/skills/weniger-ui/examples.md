# Weniger · Example rework

One rework from start to report, to show the bar. Match the judgement, not the wording.

---

## The request

"Make our settings page feel like a Rams product." A notifications screen in a small SaaS app: a white card on light grey with one soft grey shadow on all sides, the heading "NOTIFICATION SETTINGS ⚙️", four rows each with an icon, a label and a blue toggle, a purple-to-blue "Save changes" button and a grey "Cancel" button of the same size. The toggles are blue when on and grey when off. Spacing between rows is 14, 18, 14 and 20 px.

## What the rework does

**Take stock.** One card, four rows, two buttons. Colours: white, #F4F5F7, blue #3B82F6, a gradient. One shadow. Three type sizes plus capitals. No dark mode. The brand has no accent of its own, so the starter's orange becomes `--accent`.

**Tokens first.** Ground, three levels and shadows for light and dark, from the starter.

**Shared layer.**
- The card becomes a resting tile on the ground; its radius is 26 px with 10 px padding, so the rows inside are 16 px (principle 7).
- The heading becomes "Notifications" in the heading style. The capitals and the gear go: the label names the function, and the gear has no job on a page that is already settings (principles 1, 2, 10).
- The four row icons go. Each repeated what the label already said (principle 1).
- Row spacing becomes 12 px everywhere, rows 44 px high (principle 9). A hairline divides the rows (principle 12).
- The toggles become a sunk track with a raised thumb. On means the thumb sits right and a small lamp beside it lights in the accent. In greyscale the position alone still says on or off (principles 3, 5, 14). The thumb eases without overshoot (principle 17).
- "Save changes" becomes the one raised button with the accent; "Cancel" becomes a quiet text button. The gradient goes (principles 4, 14, Never).

**Left alone.** The labels' wording, the order of the rows, what Save and Cancel do.

## The report

> Reworked the notifications page: tokens for light and dark, the card, the rows, the toggles and the two buttons. Left the copy, the order and the behaviour as they were.
>
> Review by a fresh subagent with only DESIGN.md and the page, at 390, 768 and 1280 px, light and dark. Two rounds.
> - Purpose 5: no icons or ornament left; "Save changes" is the only action that leads.
> - Depth 4: the thumb is raised and the track sunk; the pressed Save button sinks 1 px. Round 1 scored 3: Cancel still had a shadow, so it looked pressable at the same level as Save.
> - Measure 5: rows 44 px, 12 px apart, nothing wraps at 390 px.
> - Colour 4: the accent appears only on the lamps and on Save. Dark mode has its own depth; the hairlines are slightly faint at 390 px.
> - Motion 4: toggles ease and can be interrupted; reduced motion is respected. Not checked: the theme cross-fade, because the app has no theme switch.
>
> Every principle met.
>
> To make it yours: change `--accent` to your brand colour, and `--ground-a` / `--ground-b` if you want a cooler grey.
