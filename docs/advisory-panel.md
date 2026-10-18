# Advisory panel — everyone who should have a say

The first version of the prompt had three experts (teacher, game designer, frontend developer). A game for children touches many more disciplines. In the full prompt the model must **answer in each advisor's voice at every stop point** and record disagreements instead of silently choosing.

| # | Advisor | Owns | Concrete rule they contribute | Example |
|---|---|---|---|---|
| 1 | **Israeli EFL teacher / curriculum specialist** | Alignment with English Curriculum 2020, Band I words, Grammar Band I | ≤10–12 new words per lesson; every word from Band I (flag exceptions); can-do goal per lesson | "Lesson 3: *I can say how old I am.* Chunk: *I am nine.*" |
| 2 | **Learning scientist** | Retrieval, spacing, mastery, feedback | Every encounter after first exposure is a retrieval; 8–12 retrievals/word across days; review ladder same session → 1d → 3d → 1w → 2–3w | "'sister' reappears Monday, Wednesday, next Sunday" |
| 3 | **Reading / phonics specialist** | Phonemic awareness, letter–sound, CVC, sight words | Systematic order; decodable stories use only taught patterns; tricky words taught separately | Week 2 teaches *a, m, s, t*; story: "Sam sat. Mat." |
| 4 | **Phonetician (Hebrew L1)** | Interference: short vowels, th, w/v, b/d | Minimal-pair strand; separate confusable words across days | *ship/sheep, three/tree, west/vest*; b/d anchor "**b**ed" |
| 5 | **Game designer (kids)** | Core loops, pacing, variety | 3 different mechanics per lesson; mini-games ≤2 min; meaningful unlocks, no shop | Unlock "Family Album" page after lesson 3 |
| 6 | **Motivation psychologist** | Self-determination, feedback tone, wellbeing | Informative praise; unexpected recognition; no leaderboards; no streak shaming; session ≤15–20 min | "You read the whole sentence by yourself!" |
| 7 | **Child UX / UI designer** | Layout, touch targets, RTL shell + LTR content | ≥48px targets; calm screens; animation only as feedback; one task per screen | English words always LTR inside a Hebrew RTL UI |
| 8 | **Special-needs & accessibility advisor** | Dyslexia/ADHD-friendly design, a11y | Multi-sensory by default; adjustable speed; font choice; reduced motion; no flashing | "Slow" audio variant for every word |
| 9 | **Speech-tech engineer** | Recording, ASR, playback | Child ASR errors 15–25% → never gate progress; compare own recording to model | "Say *apple*" → play yours, then the model; no score |
| 10 | **Voice director / audio producer** | TTS quality, pacing, consistency | One voice per language per character; slow variants; phonetic spellings for letter sounds | `ls_b` = "buh", short and clipped |
| 11 | **Art director / animator** | Visual identity, character, media list | Original characters only; consistent style; transparent backgrounds; list every asset with a generation prompt | `char_guide_cheer`: owl claps wings, 2s |
| 12 | **Bilingual content editor** | Natural Hebrew, gender forms, translation accuracy | Short, unambiguous Hebrew; f/m variants; avoid TTS-fragile words | Female default, `_m` variant for male profile |
| 13 | **Frontend engineer** | React/TS/PWA, drag & drop, offline | Content-as-JSON; schema validation; Pointer Events; audio fallback to speechSynthesis | Missing mp3 → warn + synth |
| 14 | **Backend / data architect (Go/C#)** | Future sync, progress model | Storage interface now; API sketch later; event log of attempts | `attempt{word, activity, correct, ts}` |
| 15 | **Privacy & child-safety reviewer** | Data minimisation, consent | No PII, no ads, no external links in play; if a backend is added, review applicable child-privacy law (Israel, COPPA, GDPR-K) | Local-only progress in the pilot |
| 16 | **Parent coach** | Adult involvement (the GraphoGame lesson) | Weekly 5-minute "read it to me" card; parent screen shows words to celebrate | "This week: ask her to introduce her family in English" |
| 17 | **Assessment / evaluation researcher** | Measuring whether it works | Pre/post word check; log retrievals; plan a small comparison; align to the ABLE KIT screener where relevant | 20-word check at start and after unit |
| 18 | **Playtest facilitator (kids)** | Real-child testing | 10-minute observation protocol; note confusions, not just scores | "Where did she hesitate? What did she ask?" |
| 19 | **Ethics reviewer (anti-dark-patterns)** | Manipulation, screen time | No guilt notifications, no countdown pressure, no lives that block practice; end-of-session "great stopping point" | "That's enough for today — see you tomorrow!" |

## How the panel is used
- **Stage gate:** at each stop point the model prints a short *Panel review* — one line per relevant advisor ("✔ / ⚠ + why"), plus any unresolved disagreement for the human to decide.
- **Conflict rules:** child safety/privacy (15, 19) and learning evidence (2, 3) beat visual preference; accessibility (8) beats animation; the human parent decides the rest.
