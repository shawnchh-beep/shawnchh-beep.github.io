---
name: ptcg-pocket-play
description: Play Pokémon TCG Pocket through iPhone mirroring, especially solo battles. Plan decks and turns for beginner, intermediate, and advanced solo missions, and verify moves and task completion from the screen.
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
- Within the user's requested difficulty and scope, choose the next incomplete opponent/task. When none remain in the current expansion, inspect the other relevant expansions. Do not expand the assignment to other difficulties.
- Read every challenge on the opponent deck detail screen. A win may not finish its separate challenge tasks.
- Set one primary task per battle; combine compatible tasks, and use separate battles for conflicting requirements. Verify exact type, rarity, turn-limit, damage, and no-points-lost wording. Do not equate winning with completing every task.
- Compare eligible rental and available player-made decks by task compliance, setup consistency, time to an effective attack, ability to survive or disrupt the opponent's main attacker, and knockout thresholds. Type advantage is useful when it changes the number of attacks required; it does not compensate automatically for slow or unreliable setup.
- Inspect the actual deck list, evolution lines, draw/search effects, Energy settings, and card versions. Prefer dependable lines when they can win; do not select by deck title or release date alone. Use the attribute filter to find candidates.
- Respect the user's preference for newer rentals when comparably suitable; consider an older deck when it offers a materially better task-compatible route, and briefly explain the choice.
- Check rental uses before starting. Every started rental battle consumes a use, including losses and forfeits. Do not repeatedly reset for a favorable opening. Use an available suitable player-made deck when conserving rentals matters; obtain user authorization before spending resources to acquire cards.

## Use the iPhone mirror carefully

- Use `cua_repl` for all computer and iPhone-mirroring interaction. Read the tool documentation if it is not already available.
- Before any coordinate action, take a fresh screenshot. Locate the center of the relevant card and the center of its legal target from that screenshot; do not reuse stale coordinates after the layout changes.
- For every card drag, identify the card and confirm the move is legal before acting. Use the real `drag(from, to)` operation so the pointer stays held during movement. Never replace a drag with a click followed by a move.
- After each drag, take another screenshot and check whether the card moved and whether the game accepted it.
- During opening setup, only a Basic Pokémon can go into an empty active or bench slot. An Evolution Pokémon must be placed on a matching Pokémon that meets the evolution rules. Trainer cards cannot be placed as Pokémon.
- If a drag fails, do not repeat it blindly. Record the card name (or say if it cannot be read), the start and target coordinates, and the before/after screen change. Recheck the card type, start point, and target; make at most one informed adjustment. If the drag API does not support a held drag, state that limitation and stop card-drag attempts.
- Use screenshots to confirm energy attachment, attacks, knockouts, score changes, and turn changes. Use automatic play for routine beginner battles or an intermediate matchup shown to work reliably. Prefer manual decisions for advanced battles and restrictive tasks. Do not assume automatic play preserves task requirements; inspect its actions and intervene when needed.
- Do not navigate away from an active battle unless the user asks to stop or the game requires it.

## Battle and verify

- Place a legal Basic Pokémon in the active spot. Add bench Pokémon only when useful or required by a challenge.
- Before attacking, check that the active Pokémon has enough energy and that the chosen attack is available. Prefer attacks that use the required type and exploit weakness, while protecting a winning position.
- After a knockout or forced promotion, inspect the board again and select a legal replacement if the game asks.
- Continue until the result screen visibly says 勝利. Move through the result pages and read the challenge progress. Return to the requested difficulty's list, verify updated progress, and continue with the next incomplete task, deck, or expansion.
- If a battle is lost, verify which task remains and retry with an informed deck or play adjustment; do not claim completion from an attempted battle.

## Plan each turn

- Maintain a compact state record from the current screen: turn/whose turn, both scores, active and benched Pokémon with remaining HP, attached Energy, evolution readiness and relevant effects; readable hand cards, available Energy, and whether limited actions such as a Supporter, retreat, or Ability have been used. Track task progress and remaining turn budget when relevant.
- Identify cards by version and effect, not name alone. Open card details when an unreadable effect could change the decision. Pocket rules differ from the physical TCG; use in-game help and official Pocket guidance. Do not assume the first player can never attack: an attack with no Energy requirement can be legal on that player's first turn.
- First look for a legal win this turn, including target switching, Abilities, damage modifiers and attack effects. If a guaranteed legal line meets the primary task, take it without unnecessary actions.
- Next assess whether the opponent can win on its next turn. Separate visible threats from plausible unseen cards; do not treat inferred hands or deck contents as known. Prioritize preventing an immediate loss.
- Otherwise compare a few realistic lines through the opponent's next turn and your following turn: attack, retreat/switch, evolve, heal, disrupt, or build a benched attacker. Favor a task-compatible path with a reliable winning continuation over raw damage or coin-flip upside.
- Choose action order based on dependencies. Draw or search before committing Energy, a Supporter, or retreat when new information may change the plan, but account for search targets and remaining deck contents. Re-evaluate after newly revealed cards or random outcomes.
- Before attacking, verify the chosen target, Energy costs, damage/effects, scoring outcome, and any useful or task-required actions still available. Attacking usually ends the turn; do not leave an essential action until afterward.

## Calculate knockouts, points, and Energy

- Calculate damage from the actual card text, weakness, modifiers, protective effects, and relevant status timing. Compare attacks needed to knock out each candidate target. Spend a modifier or heal when it changes a knockout, survival, or task threshold; preserve it when it does not improve the winning route.
- Track the actual points each Pokémon would concede if knocked out. Protect any target whose loss would immediately end the battle. A sacrifice is useful only if it does not cause defeat or invalidate the primary task and creates a concrete winning continuation.
- Attach Energy where it enables the best next attack, retreat, or setup. Avoid investing in a Pokémon likely to be knocked out before that Energy helps. Consider the retreat cost, Energy lost to attacks, next available Energy, and replacement attacker's readiness.
- Bench Pokémon for a defined purpose: evolution setup, Ability, replacement attacker, or necessary survival. Account for forced switching and bench damage; filling every slot is not automatically beneficial.
- After a forced promotion, inspect the new board and choose the replacement based on surviving the next threat and continuing the winning route, rather than selecting the highest HP alone.

## Adapt and learn from battles

- For intermediate tasks, prioritize consistent setup and favorable knockout exchanges. For advanced tasks, explicitly assess the opponent's setup timing and a plan to disrupt it, survive it, or win first.
- Adapt to the primary task: no-points-lost favors protection and switching; turn limits favor fast setup; damage thresholds require the qualifying attack; type/rarity restrictions must be checked against the actual list. Do not delay a winning attack merely to pursue an unrelated optional task.
- After a loss or failed task, record opponent/difficulty, chosen deck, first/second player, task target, result, and the decisive issue: setup failure, tactical decision, task mismatch, interaction error, or observed random outcome. Change the deck or plan based on that evidence, rather than repeating unchanged attempts.
- Do not claim a win-rate improvement without comparable battle records. If the same obstacle persists across three informed attempts with no viable adjustment, report the blocker and remaining task instead of consuming rentals indefinitely. Continue other independent tasks within the authorized scope when possible.

## Communicate progress

- Use simple Traditional Chinese unless the user asks for another language. Give short updates after meaningful milestones, such as finding an incomplete deck, choosing a counter deck, or winning.
- In the final update, state which expansion/deck was completed and what remains. Do not say all beginner missions are finished unless every relevant expansion's beginner victory progress has been checked.
- When appropriate, end with **下一步可以做什麼：** followed by a short next action.

