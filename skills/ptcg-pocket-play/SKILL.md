---
name: ptcg-pocket-play
description: Play Pokémon TCG Pocket through iPhone mirroring, especially solo battles. Track beginner victory missions, choose type-advantaged rental decks, and verify each move and result from the screen.
---

# Pokémon TCG Pocket play

Use this skill when the user asks Codex to play Pokémon TCG Pocket through iPhone Mirroring, especially when progressing through solo-battle missions.

## Keep the mission goal clear

- Read the current screen before acting. Confirm the battle mode and difficulty (for example, 初級), the selected expansion, opponent deck name, and visible task progress.
- Follow the user's stated finish line. If they ask to complete all beginner victory missions, continue through every expansion until each beginner deck's win task is visibly complete. Do not stop after one win or after clearing only the current expansion.
- Treat the game screen as the source of truth. After a battle, verify the victory screen and updated task count/checkmarks before deciding the next deck.
- If a deck row is already complete, skip it. If a task or count is ambiguous, open the deck's detail screen and inspect its challenges before starting.

## Research and choose a deck

- Search current game rules or a specific opponent deck when the screen does not explain the task, card weakness, or legal move. Prefer official game guidance; use reputable card references for card-specific details. Do not guess when a wrong choice could invalidate a challenge.
- Within an expansion, choose the first incomplete beginner deck. When none remain, open the expansion selector, inspect the available packs, and move to the next pack with an incomplete beginner win task. Continue until all relevant packs are verified complete.
- Read every challenge on the opponent deck detail screen. A win may not finish its separate challenge tasks.
- Choose a rental deck that both satisfies the required challenge and exploits the opponent's weakness when possible. Use the in-game attribute search (magnifying glass) to filter rentals. Check the actual deck name/type and rental uses before selecting it. If no single deck meets both goals, meet the required challenge first while preserving the best available matchup.
- Select older rental decks only when no suitable type-advantaged rental is available, as the user requested.

## Use the iPhone mirror carefully

- Use `cua_repl` for all computer and iPhone-mirroring interaction. Read the tool documentation if it is not already available.
- Before any coordinate action, take a fresh screenshot. Locate the center of the relevant card and the center of its legal target from that screenshot; do not reuse stale coordinates after the layout changes.
- For every card drag, identify the card and confirm the move is legal before acting. Use the real `drag(from, to)` operation so the pointer stays held during movement. Never replace a drag with a click followed by a move.
- After each drag, take another screenshot and check whether the card moved and whether the game accepted it.
- During opening setup, only a Basic Pokémon can go into an empty active or bench slot. An Evolution Pokémon must be placed on a matching Pokémon that meets the evolution rules. Trainer cards cannot be placed as Pokémon.
- If a drag fails, do not repeat it blindly. Record the card name (or say if it cannot be read), the start and target coordinates, and the before/after screen change. Recheck the card type, start point, and target; make at most one informed adjustment. If the drag API does not support a held drag, state that limitation and stop card-drag attempts.
- Use screenshots to confirm energy attachment, attacks, knockouts, score changes, and turn changes. Prefer the game's automatic-play option when it makes legal progress, but verify its actions and intervene when needed.
- Do not navigate away from an active battle unless the user asks to stop or the game requires it.

## Battle and verify

- Place a legal Basic Pokémon in the active spot. Add bench Pokémon only when useful or required by a challenge.
- Before attacking, check that the active Pokémon has enough energy and that the chosen attack is available. Prefer attacks that use the required type and exploit weakness, while protecting a winning position.
- After a knockout or forced promotion, inspect the board again and select a legal replacement if the game asks.
- Continue until the result screen visibly says 勝利. Move through the result pages and read the challenge progress. Return to the beginner list, verify the updated count, and continue with the next incomplete deck or expansion.
- If a battle is lost, verify which task remains and retry with an informed deck or play adjustment; do not claim completion from an attempted battle.

## Communicate progress

- Use simple Traditional Chinese unless the user asks for another language. Give short updates after meaningful milestones, such as finding an incomplete deck, choosing a counter deck, or winning.
- In the final update, state which expansion/deck was completed and what remains. Do not say all beginner missions are finished unless every relevant expansion's beginner victory progress has been checked.
- When appropriate, end with **下一步可以做什麼：** followed by a short next action.
