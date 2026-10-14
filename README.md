# Flight-Themed Study Timer

**Study Flight Deck** turns a real flight into a study session. Choose a departure and a destination airport. The flight's real block time becomes your session length, split into study blocks ("seatbelt on") and breaks ("seatbelt off").

## Use it

Open `index.html` in any browser. There's no build step and no dependencies. Keep the `geo/` folder next to it, because it holds the map data and imagery. The satellite map needs the page to be served over http(s), for example by GitHub Pages, the claude.ai artifact or `python3 -m http.server`. Opened straight from disk, the page falls back to a drawn map.

1. **File a flight plan.** Pick From and To from 217 airports, grouped by region: East and Southeast Asia, the Philippines, South Asia, the Middle East, Central Asia and the Caucasus, Europe, Africa, North America, Central America and the Caribbean, South America and Oceania. The block time comes from the great-circle distance (cruise around 830 km/h plus 30 min for taxi, climb and approach). You can change the hours and minutes if you want a different session length.
2. **Set your rhythm.** Add your name for the ticket. The defaults are 50 min study blocks with 10 min breaks. The last study block runs until landing.
3. **Print my ticket.** An automatically generated ticket appears, with your name, flight number, gate, seat, departure and arrival times, the study itinerary and a barcode. Press **Board & depart**, or it boards by itself after 30 seconds. **Change flight** takes you back to the planner.
4. **In flight.** The flight deck shows:
   - the seatbelt sign: cyan **Fasten seatbelt: study** or amber **Seatbelt off: take a break**
   - a countdown for the current block, plus the time of the next change
   - phase, altitude, ground speed, distance to go, time to go and ETA
   - a large moving map, like the ones on airline seat-back screens:
     - **Follow** is a tilted chase view behind the aircraft, with the curved horizon and atmosphere. **Route** shows the whole flight. **Flat** is a classic map.
     - NASA Blue Marble satellite imagery with hill shading
     - city labels with each city's **local time**
     - the route as a gold band (flown) and a white band (still to fly), with maroon pins marking departure and arrival
     - a shaded 3D Boeing 747-style jumbo jet (upper-deck hump, four engines, winglets, cabin windows, navy tail with a coral stripe) with navigation lights and a ground shadow
     - **Daylight** lighting, or **Live sun**, which shows real day and night with city lights
     - drag to look around, + and − to zoom
   - the timer and flight data float over the map: phase, altitude, speed, distance, time to go, arrival, and the time at your destination
5. A two-note cabin chime (rising for study, falling for a break) plays when the sign changes and when you land. If you allow notifications, you also get one.

Controls: **Enter holding** pauses (or press Space), **Skip to next** jumps to the next block, **Divert** ends the flight early. Every flight is saved in the **Pilot logbook** with the study time you put in. If you reload the page mid-flight, the flight carries on where it was.

All data stays in your browser's local storage.

## Map data

- `geo/earth-day.jpg`, `geo/earth-night.jpg`, `geo/earth-relief.png` and `geo/earth-water.png` are NASA Blue Marble / Black Marble imagery, elevation and water mask (public domain, NASA Earth Observatory), taken from the example images shipped with the `three-globe@2.31.0` npm package.

`geo/world.js` holds country outlines from [Natural Earth](https://www.naturalearthdata.com/) at 1:50m scale (public domain), taken from the `world-atlas@2.0.2` package and repacked into a compact form for the nav display.

The page is set in Times New Roman. Where that font isn't installed, it uses Tinos from Google Fonts, which has the same letter widths.

The look is a daylight cabin: a bright window-seat sky with slowly drifting clouds, white frosted cards, navy type and coral accents.

## Background music

The music bar under the header plays generative cabin music inspired by instruments from around the world. It's synthesised live in the browser, so nothing is downloaded and it never loops the same way twice.

| Style | Instruments |
|---|---|
| Japan | koto & shakuhachi |
| China | guzheng & dizi |
| Philippines | kulintang, agung & dabakan |
| Bali | gamelan, with gong cycles and interlocking kotekan |
| India | sitar, tanpura & tabla |
| Egypt & the Middle East | oud, ney & riq, in maqam Hijaz |
| Central Asia | dutar & doira |
| West Africa | kora & balafon |
| Ireland & Scotland | harp, tin whistle & bodhrán |
| Peru & Bolivia | pan flute, charango & bombo |
| Trinidad & Tobago | steel pan |
| Hawaii | ukulele & slack-key guitar |

**Auto** picks the style that matches your destination. Study blocks are sparse and calm, breaks are fuller with percussion, and holding pauses the music. The music dips while a chime plays. Volume and the on/off setting are remembered.

## Chime volume

The **Chime** control in the header sets how the study and break changes sound:

| Setting | What you hear |
|---|---|
| Off | Nothing |
| Soft | One quiet chime |
| Normal | The chime twice |
| Loud | The chime three times at full volume |

Notes fade in gently, so even Loud never starts with a sudden click. Picking a setting plays a sample.

## Ranks, challenges and rankings

- **Pilot rank:** you go up a rank as your total study grows, from Cadet through Private Pilot, First Officer and Captain up to Ace of the Skies. An epaulette shows the stripes, with a progress bar to the next rank.
- **Streaks:** your current and best daily streak. A day counts when you study at least 25 minutes.
- **Challenges:** 18 in total.
  - daily and weekly goals
  - streaks
  - milestones: Long haul, Red-eye, Early bird, Clean record
  - exploration: Island hopper (Philippines), Grand tour (Europe), Into Africa, Silk Road (Central Asia), Isthmus run (Central America), Six continents
  - Centurion, for 100 hours of study

  Newly completed challenges and promotions show when you land.
- **Rankings:** this week and all time.

## Where your history is kept

Every flight is saved in the browser. When the page is opened as the published claude.ai artifact while signed in, history is also saved to the person's private part of the artifact's database. That means it comes back whenever they reopen the link, even on another device. A summary row is also saved to a shared leaderboard that everyone on the page can see.

## Moving history from the old link

The app's home is now the claude.ai link. Each person's history is stored in their own browser, under the site address they used, so the old GitHub Pages site (or a downloaded copy) keeps its own separate history.

When the app runs on the old site, it shows a **"Study Flight Deck has moved"** banner. **Move my history to the new link** opens the new link with the person's flights packed (compressed) into the address. The new link checks the flights, asks before adding them, and skips any that are already there. The added flights then count toward rank, streaks, challenges and the leaderboard, and sync to the person's Claude account. If a browser drops the packed data from the link, **Copy transfer code** on the old site plus **Bring flights from an old link** under the Pilot logbook does the same job.
