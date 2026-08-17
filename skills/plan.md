# Phase 1: Plan

Read `references/trip-planning.md` for full methodology.

## Core sequence

1. **Extract hard constraints** — dates, flight times, terminals, hotel location
2. **Group wishlist** — city-easy / needs-reservation / far-suburbs / pass-through
3. **Cut high-risk items first** — too far, holiday-crowded, weather-dependent. Say what was cut and why.
4. **Arrange by area** — one main area per day, first day light, last day close to airport
5. **Fill in meals** — daily-area candidates first, 大众点评 + 小红书 signals second, fame last
6. **Add tickets & transport** — only critical ones (museum tickets, airport transfer)
7. **Write reference doc** — conclusion first, then daily plan, weather-sensitive spots, meal areas, what was cut

## Key principles

- Not everything the user listed fits. Delete for them.
- One area per day. One reservation-required spot per day max.
- Itineraries should be smooth, not packed.
- All user-facing questions follow the **4-beat format**: Re-ground → Simplify → Recommend → Options.
  See `references/trip-planning.md` § 用户交互 for examples and anti-patterns.

## Output

Hand off to Phase 2 with: city name, travel dates, day-by-day areas, meal slots per day.
