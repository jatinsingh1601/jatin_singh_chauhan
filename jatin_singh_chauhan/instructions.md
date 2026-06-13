# Mossback Arcade - Work Instructions

## Context

Mossback Games is a small independent game studio. We need a website called Mossback Arcade where visitors can browse a catalog of small games, open any one of them, and play it in the browser with no download and no sign up. The website is the deliverable. The developer builds five games for the launch, and the catalog is set up so the studio can keep adding more games from its own side later, with no other page changes.

The whole site is built with plain HTML5, CSS3, and vanilla JavaScript. No frameworks, no build step, no backend, no database. Everything the visitor does, such as high scores, favorite games, the chosen skin, the sound setting, a local nickname, tokens, and badges, is stored in their own browser using localStorage. The site must run by opening `index.html` in a browser, or by serving the folder with any static file server.

There are two deliverables: the website source folder and at least three screenshots of the finished site. A folder of code with games that do not run is not enough.

## Tech Stack

1. The site uses HTML5 for markup.
2. The site uses CSS3 for styling, with no CSS preprocessor required.
3. The site uses vanilla JavaScript (ES2015 or later) for all logic.
4. The site stores all visitor data in the browser using localStorage only.
5. The site uses Google Fonts: Press Start 2P for the logo and short arcade labels, and Inter for body text and interface labels.
6. The site uses an open icon set such as Material Symbols, Feather Icons, or Heroicons.
7. The site uses no front end framework such as React, Vue, Angular, or Svelte.
8. The site uses no UI or CSS framework such as Bootstrap or Tailwind.
9. The site uses no game engine or game library such as Phaser, Pixi.js, or Kaboom.
10. The site uses no backend, no server code, and no database.

## Brand and Visual Style

11. The site name shown everywhere is `Mossback Arcade`, written as an original pixel style wordmark next to a small arcade cabinet icon. Do not use any existing brand logo or font style.
12. The studio name shown in the footer is `Mossback Games`.
13. The overall look is a retro pixel arcade. The page background is a dark texture, such as a carbon fiber or woven pattern, not a flat color.
14. Buttons, cards, and panels have a neon outline that glows, in white or in an accent color.
15. Headings, the logo, and game titles use the Press Start 2P pixel font.
16. Body text, descriptions, and labels use Inter, with a base size of 16 px and a line height near 1.5.
17. The site uses this color palette over the dark textured background.

| Purpose | Name | Hex |
| --- | --- | --- |
| Primary neon | Cyan | `#36E0E0` |
| Secondary neon | Magenta | `#FF3D9A` |
| Token and coins | Gold | `#FFC83D` |
| Skin and logo accent | Purple | `#9B5DE5` |
| Arcade category | Green | `#2FE6A0` |
| Puzzle category | Orange | `#FF9A3D` |
| Board category | Blue | `#3D9AFF` |
| Action category | Pink | `#FF3D9A` |
| Background base | Near black | `#0B0E14` |
| Panel and cards | Slate | `#141A24` |
| Text | White | `#F4F8FF` |
| Muted text | Gray | `#8A93A2` |

18. Game cards show a pixel art thumbnail for each game.
19. Card corners are rounded.

## Arcade Skins (theme system)

20. The site has three named skins, chosen from a dropdown in the header. The skins are `Nebula`, `Synthwave`, and `Matrix`.
21. The `Nebula` skin is the default. It uses deep space purple and cyan over the dark texture, with a slow starfield particle layer.
22. The `Synthwave` skin uses magenta and orange neon over the dark texture, with a faint sunset grid.
23. The `Matrix` skin uses green neon over near black, with a faint layer of falling dots.
24. The header skin switcher shows the name of the current skin.
25. The chosen skin is saved in localStorage and is applied on every page on the next visit.
26. Text in every skin keeps a contrast ratio of at least 4.5 to 1 against its background for body text.

## Animated Background

27. Every page has an animated particle layer that sits behind the content, drawn with CSS or an HTML5 canvas.
28. The animated background never sits on top of buttons or links and never blocks clicks.
29. The animated background style matches the active skin, for example a starfield in the `Nebula` skin.
30. When the browser reports a reduced motion preference, the background animation stops and shows a still version.

## Site Structure and Files

31. Deliver the site in a single folder named `mossback-arcade/` with this layout.

```
mossback-arcade/
├── index.html
├── games.html
├── play.html
├── scores.html
├── profile.html
├── about.html
├── css/
│   └── styles.css
├── js/
│   ├── main.js
│   ├── storage.js
│   ├── profile.js
│   └── games/
│       ├── snake.js
│       ├── memory.js
│       ├── tilemerge.js
│       ├── lockout.js
│       └── reaction.js
├── assets/
│   ├── img/
│   ├── avatars/
│   ├── icons/
│   └── sounds/
├── data/
│   └── games.json
└── README.md
```

32. All six HTML pages share one stylesheet, `css/styles.css`.
33. All six HTML pages share one main script, `js/main.js`, for the header, skins, sound, and shared behavior.
34. `js/storage.js` holds the helper functions that read and write localStorage.
35. `js/profile.js` holds the logic for the nickname, avatar, tokens, and badges.
36. Each game lives in its own file under `js/games/`.

## Game Catalog (data/games.json)

37. The home and library pages build their game cards from `data/games.json`. The card list is not hard coded separately on each page.
38. `data/games.json` is an array of game objects.
39. Each game object has these keys: `id`, `title`, `category`, `description`, `thumbnail`, `controls`, `scoreLabel`, `isNew`, `isPopular`.
40. `id` is a short lowercase string used in the play link, for example `snake`.
41. `category` is one of `Arcade`, `Puzzle`, `Board`, or `Action`.
42. `scoreLabel` is the unit shown next to the saved best, for example `points`, `moves`, or `seconds`.
43. The catalog lists all five built in games described in the Games section.

## Adding More Games (extensibility)

44. A new game is added by appending one object to `data/games.json` and adding one matching file under `js/games/`.
45. Each game file defines a start function that the play page calls with the play area element and a callback used to report the final score.
46. The README includes a short section named `Adding a game` that lists these two steps.
47. No change to the other pages is required to add a game beyond the catalog entry and the game file.

## Header, Navigation, and Footer (all pages)

48. Every page has the same header with the arcade cabinet icon and the `Mossback Arcade` wordmark on the left that links to the home page.
49. The header navigation has five pill buttons, each with an icon and a label: Home, Games, Leaderboard, Profile, and About.
50. The pill button for the current page is shown with a stronger neon outline than the others.
51. The header shows the skin switcher as a dropdown that displays the name of the current skin.
52. The header shows a sound on or off toggle.
53. The header shows a token counter with a coin icon and the visitor current token balance.
54. The header shows the visitor avatar and nickname when a nickname is set, or a `Set name` link when it is not.
55. On screens narrower than 768 px the navigation collapses into a menu button that opens and closes the links.
56. Every page has the same footer showing `Mossback Games` and a copyright line.

## Sound

57. The games play short sound effects, for example a pickup sound or a hit sound.
58. The header sound toggle turns all game sound on or off.
59. When sound is off, no game plays any sound.
60. The sound setting is saved in localStorage and is read on the next visit.
61. Every sound file is listed in the README with its source link and license.

## Tokens

62. The visitor earns 1 token each time a game reaches its end state, whether a game over or a win.
63. The visitor earns 5 extra tokens when a game result beats the saved best for that game.
64. The token balance is saved in localStorage.
65. The token balance shown in the header updates after a game ends.

## Badges

66. The site has a fixed set of six badges that unlock from local play.
67. The `First Play` badge unlocks after the visitor finishes any game once.
68. The `Century` badge unlocks when the Snake score reaches 100 points or more in one game.
69. The `Sharp Memory` badge unlocks when Memory Match is finished in 20 moves or fewer.
70. The `Tile Master` badge unlocks when a 256 tile is reached in Tile Merge.
71. The `Unbeaten` badge unlocks after three wins in a row in Grid Lockout.
72. The `Quick Hands` badge unlocks when Reaction Rush reaches 20 hits or more in one round.
73. Unlocked badges are saved in localStorage and shown on the Profile page.

## Home Page (index.html)

74. The home page shows a featured carousel at the top with a Game of the Day, a game title, a short line of text, and a Play button that opens that game.
75. The Game of the Day is chosen from the current date so it is the same for every visitor on a given day and changes the next day.
76. The featured carousel shows dot indicators and cycles through a few highlighted games.
77. The home page shows a Popular section of game cards.
78. The home page shows a New Games section of cards for games flagged `isNew`, each with a `New` badge.
79. Each of the Popular, New Games, and Recently Played sections has a `View all` link that opens the library.
80. The home page shows a Recently Played row built from the games the visitor has opened, read from localStorage.
81. The Recently Played row shows a short message when the visitor has not played any game yet.
82. Each Recently Played card shows the game best score.
83. The home page shows a Browse by Category row with one button per category.
84. Each Browse by Category button shows the category icon, the category name, and the number of games in that category.
85. Each game card shows the thumbnail, the title, the category, and a favorite toggle.
86. Clicking a card outside the favorite toggle opens that game play page.
87. The favorite toggle shows a filled state when the game is a favorite and an empty state when it is not.

## Games Library (games.html)

88. The library shows a grid of cards for every game in the catalog.
89. A search box filters the visible cards by title as the visitor types.
90. The search match is case insensitive.
91. The search updates the grid without reloading the page.
92. Category filter buttons are shown for All, Arcade, Puzzle, Board, and Action.
93. Selecting a category shows only games in that category.
94. Selecting All shows every game.
95. A Favorites filter shows only the games the visitor has marked as favorite.
96. The search box and the category filter work together on the same grid.
97. When a search or filter returns no games, the page shows a short `No games found` message.

## Play Page (play.html)

98. The play page reads the game to load from the URL query string, for example `play.html?game=snake`.
99. When the game value is missing or does not match a catalog entry, the page shows a short message with a link back to the library.
100. The play page shows the game title.
101. The play page shows a how to play note that lists the controls for the game.
102. The play page runs the selected game in a play area.
103. The play page shows a high score panel with the saved best for that game.
104. The high score panel shows a `No score yet` message when there is no saved best.
105. The play page shows a favorite toggle for the current game.
106. Opening a game adds it to the Recently Played list in localStorage.

## Games

Each game is an original build of a classic style of play. No game copies the art, logo, sound, or name of any branded product. Each game runs inside the play page play area.

### Snake (Arcade)
107. The Snake snake moves on a grid one step at a time.
108. Pressing an arrow key changes the Snake direction.
109. The Snake cannot reverse straight back into itself.
110. Eating a food item makes the Snake grow by one segment.
111. Eating a food item increases the Snake score.
112. The Snake game ends when the snake hits a wall or its own body.
113. The Snake saved best is the highest score in points.

### Memory Match (Puzzle)
114. Memory Match shows a grid of face down cards in matching pairs.
115. Clicking a card flips it face up.
116. Two flipped cards that match stay face up.
117. Two flipped cards that do not match flip back down after a short pause.
118. A move counter increases on each pair attempt.
119. A timer counts the seconds during the round.
120. Memory Match is won when all pairs are matched.
121. The Memory Match saved best is the fastest time in seconds in a won game.

### Tile Merge (Puzzle)
122. Tile Merge shows a four by four grid of numbered tiles.
123. Pressing an arrow key slides all tiles in that direction.
124. Two tiles with the same number merge into one tile with the sum.
125. A new tile appears after each move that changes the grid.
126. The score increases by the value of each merge.
127. Tile Merge ends when no move can change the grid.
128. The Tile Merge saved best is the highest score in points.

### Grid Lockout (Board)
129. Grid Lockout is a three by three board where the player marks are X.
130. Clicking an empty cell places the player mark.
131. A computer opponent places its mark after the player move.
132. Grid Lockout detects a win for either side along a row, a column, or a diagonal.
133. Grid Lockout detects a draw when the board fills with no winner.
134. The Grid Lockout saved best is the longest run of wins in a row against the computer.

### Reaction Rush (Action)
135. In Reaction Rush a target appears at a random spot in the play area.
136. Clicking or tapping the target before it moves scores a hit.
137. The score increases by one for each hit.
138. A round lasts 30 seconds.
139. Reaction Rush shows the final score when the round ends.
140. The Reaction Rush saved best is the highest number of hits in one round.

## Shared Game Rules

141. Every game shows a game over or a win message when it ends.
142. Every game has a restart control that starts a new game after it ends.
143. Every game saves its best result to localStorage under a key that names the game.
144. A saved best is only replaced when a new result is better by the rule named for that game.

## Leaderboard Page (scores.html)

145. The Leaderboard page lists every game in the catalog with the best saved result on the device.
146. Each saved best is shown with its unit from the `scoreLabel` field, for example points or moves.
147. A game with no saved best shows a `No score yet` line.
148. The Leaderboard shows the visitor nickname when one is set.
149. The numbers on the Leaderboard match the saved best shown on each game play page.

## Profile Page (profile.html)

150. The Profile page lets the visitor type and save a nickname.
151. The saved nickname is shown in the header on every page.
152. The Profile page lets the visitor pick an avatar from a set of preset arcade character images.
153. The chosen avatar is shown in the header.
154. The Profile page shows the current token balance.
155. The Profile page shows the six badges and marks which ones are unlocked.
156. The Profile page lists the visitor favorite games.
157. The Profile page has a reset button that clears the visitor saved data after a confirm step.

## About Page (about.html)

158. The About page shows a short description of Mossback Games.
159. The About page shows one contact line.

## First Visit Defaults

160. On a first visit with empty storage the site uses the `Nebula` skin.
161. On a first visit with empty storage the sound is on.
162. On a first visit the token balance is zero, there are no badges, no favorites, no recently played games, and no saved scores.
163. The site loads without errors when localStorage is empty.

## Responsive Layout

164. The layout works at a mobile width of 320 px and up.
165. The layout works at a tablet width of 768 px and up.
166. The layout works at a desktop width of 1024 px and up.
167. Content is centered with a maximum width near 1200 px on large screens.
168. Game card grids show one column on a narrow screen and more columns on a wide screen.
169. Each game play area fits inside a small screen without overflowing the page.

## Assets and Licensing

170. The site uses only royalty free assets that are openly licensed under CC0, CC BY, public domain, or a stated free commercial license.
171. Fonts come from Google Fonts.
172. Icons come from an open icon set.
173. Game thumbnails and avatars are original images by the developer or openly licensed images.
174. No asset copies a copyrighted or trademarked image, logo, sound, or name.
175. The README lists every external asset with its name, source link, and license type.

## Code Quality

176. The code is split across the files listed in the structure, not packed into one file.
177. JavaScript functions carry short comments where the purpose is not obvious.
178. Variable and function names describe what they hold or do.
179. The delivery contains no dead code and no commented out blocks.
180. The delivery contains no leftover debugging console output.
181. No page or game throws an error in the browser console during normal use.

## README

182. The README explains how to run the site by opening `index.html` or by serving the folder with a static server such as `python -m http.server`.
183. The README lists the five games and the controls for each.
184. The README includes the `Adding a game` section.
185. The README includes the full asset credit list with sources and licenses.

## Originality

186. All code is written by the developer or taken from openly licensed snippets with the source noted in a comment.
187. The delivery contains no copied proprietary code.

## Scope Boundaries

The following items are out of scope and must not be included.

188. No backend or server code.
189. No database.
190. No user accounts, login, or sign up.
191. No online or networked multiplayer.
192. No global online leaderboard. Scores stay local to the device.
193. No advertising or analytics scripts.
194. No payments or in app purchases.
195. No app store packaging such as APK, IPA, or a PWA install flow.
196. No front end framework, UI framework, or game engine.
197. No content management system or admin panel.

## Submission Instructions

198. Deliver the complete `mossback-arcade/` folder packaged as a single zip archive.
199. Include the README with the run steps and the asset credit list.
200. Confirm the site has been tested in at least two browsers before delivery.
201. Provide at least three screenshots of the finished site.
202. All code must be original. Plagiarized or unedited AI boilerplate is not accepted.
