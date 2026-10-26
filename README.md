# LHC Mystery Night

Five-stage detective game for the Lebanese Heritage Club (AUB) Mystery Night.

- `/` : team page. One phone per team: register the team (name + 4 members), then eliminate one suspect per clue. Teams never see points or whether an answer was right; at the end each phone shows only the team's rank.
- `/host` : host page (PIN protected). Open each stage when the clue is handed out, watch answers and scores live, end the game to reveal ranks, show a join QR code.

Backend: Supabase project `lhc-mystery-night`. All game data sits behind row level security; players can only call the game functions (`register_team`, `team_state`, `submit_answer`). The answer key and scoring live only in the database. Answer times use the server clock, so "who answered first" is fair across phones.

Scoring: stages 1 and 2 give 10 / 8 / 6 to the first three correct teams and 1 to every later correct team; stages 3 and 4 give 1 per correct team; stage 5 gives 20 / 18 / 16 then 10. Wrong answers score 0. Ties on total are broken by who answered stage 5 earlier.
