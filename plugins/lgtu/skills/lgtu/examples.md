# LGTU · Example reviews

Five reviews that show the tone and the bar: Ship after fixes, Ship it, two times Rethink first, and a follow-up on a new version. Match the judgement and the voice, not the wording. Notice how short they are, how each point names the thing and what it costs the user, and that good work gets a plain "Ship it".

---

## 1. Ship after fixes: an AI-built landing page

**Input:** a screenshot of the landing page for Pebble, a team-planning app, with "Is this ready to ship?". A purple-to-blue gradient, three badges (New, AI-powered, Beta), the headline "Unlock the future of seamless productivity", a light grey subline, three equal white buttons (Get started, Book a demo, Learn more), and three feature cards at different heights and corner radii.

### My read
The landing page for Pebble, a planning app for teams. A visitor should understand what Pebble does in a few seconds and start. Tell me if I'm off.

### Verdict: Ship after fixes
The product comes through in the cards, but the page hides it behind a headline that could be anyone's, three competing buttons and text that's hard to read.

### Fix before you ship
1. **Three buttons, all shouting.** A visitor can't tell which one is the next step, so they hesitate. Fix: one filled button, "Get started". "Book a demo" becomes a quiet link. "Learn more" goes. (2. One job)
2. **The headline promises everything and says nothing.** After reading it, you still don't know what Pebble does. Fix: say the job in the visitor's words: "Plan your team's week in five minutes." (4. Start where they are)
3. **Light text on a busy gradient.** The grey subline looks like about 2.5:1 (estimate). Many people can't read it comfortably. Fix: a plain background and body text at 4.5:1 or more. (9. Built for real life)

### Ask yourself
- Do "New", "AI-powered" and "Beta" help a visitor decide anything? If not, they go. (3. Cut first)

### Prompt for your agent
On the landing page: make "Get started" the only filled button, turn "Book a demo" into a text link and remove "Learn more". Change the headline to "Plan your team's week in five minutes." Remove the three badges. Replace the gradient with a plain light background and keep all body text at 4.5:1 contrast or more. Left-align the hero on the same grid as the cards, and give the three cards one corner radius and equal height in one row.

### Keep
The card copy: "Drag tasks into days", "See who has room", "One question on Friday". Each says what the feature does in the user's words, in four words or fewer.

---
LGTU by studio zazeno · zazeno.com/lgtu

---

## 2. Ship it: an onboarding step

**Input:** "Run LGTU on the invite step." Tally, a time-tracking app for small teams. The last step of onboarding: "Step 2 of 2 · Tally", the heading "Invite your team", the line "Tally works best when everyone logs their hours. You can always do this later.", one field for email addresses ("Separate with commas"), "They join as Member · change", a "Skip for now" link and a filled "Send invites" button.

### My read
The last onboarding step for Tally. A new account owner should invite their team, or move on without feeling stuck. Tell me if I'm off.

### Verdict: Ship it
It has one job and does it: one field, one button, a clear way out, and the role is decided for you.

### Ask yourself
- What happens when someone pastes a list with a typo or a name instead of an address? Make sure the error says which address is wrong and keeps the rest. (9. Built for real life)
- Do you know how many teams invite someone in week one? That's the number this step exists for. (10. Know if it worked)

### Keep
"Tally works best when everyone logs their hours. You can always do this later." One sentence gives the reason to invite and removes the pressure to do it now. And "They join as Member · change" makes the decision for them while leaving a door open.

---
LGTU by studio zazeno · zazeno.com/lgtu

---

## 3. Rethink first: a form generated from the data model

**Input:** "Is this ok?" ProjectHub, a project-management tool. The "New Project" screen a new user sees when they create their first project. Two columns of fields: project_name *, project_slug *, Workspace ID * (placeholder "ws_"), Owner (user_id), Visibility, Default task status, Timezone and Currency (all "-- select --"), Start date and End date ("YYYY-MM-DD"), Budget, Color (hex). Six toggles: notifications, webhooks, time tracking, Gantt view, archive on completion, allow guests. Buttons: Cancel, Reset and a green Submit.

### My read
The first thing a new ProjectHub user does: create a project so they can start adding tasks. Tell me if I'm off.

### Verdict: Rethink first
This is the database table, not a screen. Someone who wants to start a project now has to make eighteen decisions first, several of them about things the system already knows.

### Fix before you ship
1. **Eighteen decisions before any value.** Every field and toggle is a reason to leave, and most have an obvious answer. Fix: ask for one thing, the project name. Everything else gets a default and lives in project settings, for later. (6. Decide for them)
2. **The system asks for what it knows.** Workspace ID, owner, slug and timezone are all known or can be derived. Asking for them tells the user this wasn't built for them. Fix: fill them in automatically and don't show them. (4. Start where they are)
3. **System words.** "project_name", "user_id", "-- select --", "Submit", "Reset". Fix: one label, "Name your project", and one button that says what happens: "Create project". (7. Speak human)

### Ask yourself
- Which of these settings do people actually change in their first month? Only those earn a place in settings; the rest can go. (3. Cut first)

### Prompt for your agent
Replace the New Project form with a single field labelled "Name your project" and a primary button "Create project", plus a "Cancel" link. Generate the slug from the name; set workspace and owner from the current user; set timezone from the browser; default visibility to the workspace setting, task status to "To do", currency to the workspace currency. Remove dates, budget, colour and all toggles from this step and move them to project settings. Remove the Reset button. After creating, open the new project with its empty state ready for the first task.

---
LGTU by studio zazeno · zazeno.com/lgtu

---

## 4. Rethink first: a dashboard that doesn't answer the question

**Input:** "Review this analytics page." Letterly, a newsletter tool for solo creators. They usually open this right after sending. "Analytics overview": eight equal number tiles (total subscribers 1,284; open rate 41.2%; click rate 6.8%; unsubscribes 12; bounce rate 0.9%; avg. read time 2m 14s; spam reports 1; net growth +38), then six charts: subscribers over time, opens by device, top countries, opens by hour, an empty "Click map" and "Engagement score (beta)". Dark theme, no labels on the axes.

### My read
Where a solo creator lands after sending a post. Their question is "how did that one do?", and maybe "am I growing?". Tell me if I'm off.

### Verdict: Rethink first
Everything is here except the answer. There's no sign of the post they just sent, and fourteen equal blocks leave them to work out what matters themselves.

### Fix before you ship
1. **It doesn't answer the question they came with.** The page shows the account, not the post. Fix: lead with the latest post: its opens and clicks, compared with their own average, in one sentence ("Opened by 48% of readers, above your usual 41%"). (2. One job)
2. **Fourteen blocks, all the same weight.** Squint and nothing stands out, so nothing is read. Fix: one answer at the top, growth below it, and the rest behind "More stats". Cut the empty click map and the beta score until they work. (3. Cut first)
3. **Numbers without a "so what".** Is 6.8% good? Is +38 a lot? A creator can't tell. Fix: show each key number against their own past, with a plain word: up, down, as usual. (5. Show the next step)

### Ask yourself
- Is "spam reports: 1" something a creator should act on? If so, it's a warning, not a tile. If not, it goes. (6. Decide for them)

### Prompt for your agent
Restructure the analytics page. Top: a card for the most recent post with its title, send date, open rate and click rate, each compared with the creator's average over the last ten posts, and one plain sentence summarising it. Below: a subscribers-over-time chart with net growth for the last 30 days. Move bounce rate, read time, devices, countries and opens by hour behind a "More stats" disclosure. Remove the click map and the engagement score. Show spam reports only as a warning banner when they're above zero, with what to do. Label chart axes.

---
LGTU by studio zazeno · zazeno.com/lgtu

---

## 5. Follow-up on a new version

**Input:** after review 1, a new screenshot of the Pebble page: plain light background, left-aligned hero, headline "Plan your team's week in five minutes", one filled "Get started" button with "or book a demo" as a link, no badges, three cards in a row. The subline is still light grey.

**Review:**

Much better. The page now says what Pebble does in one line, and there's one obvious next step. The badges are gone and everything sits on one edge, so it finally looks like a product of its own instead of a template.

One thing left: the subline is still light grey on white, around 3:1 (estimate). Darken it to your body-text colour.

Verdict: **Ship it**, after that one change.
