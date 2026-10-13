# Flight-Themed Study Timer

**Study Flight Deck** turns a real flight into a study session. Choose a departure and a destination airport. The flight's real block time becomes your session length, split into study blocks ("seatbelt on") and breaks ("seatbelt off").

## Use it

Open `index.html` in any browser. It's a single file with no build step and no dependencies.

1. **File a flight plan.** Pick From and To. The block time comes from the great-circle distance (cruise around 830 km/h plus 30 min for taxi, climb and approach). You can change the hours and minutes if you want a different session length.
2. **Set your rhythm.** The defaults are 50 min study blocks with 10 min breaks. The last study block runs until landing.
3. **Push back & depart.** The flight deck shows:
   - the seatbelt sign: cyan **Fasten seatbelt: study** or amber **Seatbelt off: take a break**
   - a countdown for the current block, plus the time of the next change
   - phase, altitude, ground speed, distance to go, time to go and ETA
   - a nav display with your aircraft moving along the route (amber diamonds mark the breaks)
4. A cabin chime plays when the sign changes and when you land. If you allow notifications, you also get one.

Controls: **Enter holding** pauses (or press Space), **Skip to next** jumps to the next block, **Divert** ends the flight early. Every flight is saved in the **Pilot logbook** with the study time you put in. If you reload the page mid-flight, the flight carries on where it was.

All data stays in your browser's local storage.
