# Bento boards

For a board of tiles, like the Weniger page itself. A normal site does not need this.

One grid, 70 px rows, 12 px gap. Make the board a container and switch columns with container queries: 12 columns from 1360 px, 6 from 700 px, 2 below. Place every tile explicitly per layout with CSS variables, so nothing reflows by accident. Keep the same row span across layouts.
