# tower-defense-game
A simple but very interactive game of tower defense.

## Development Plan

### 1) Define scope and core loop
- Choose the initial platform (web browser) and stack (TypeScript + HTML5 Canvas).
- Lock an MVP: one map, three tower types, three enemy types, and one boss wave.
- Specify the gameplay loop:
  1. Build phase (place/upgrade/sell towers)
  2. Wave phase (enemies pathfind and attack)
  3. Reward phase (currency, score, life update)

### 2) Design game systems
- **Grid & map system**: tile-based map with blocked/path tiles and spawn/goal points.
- **Pathfinding**: A* for enemy route calculation with dynamic recalculation when towers block paths.
- **Wave manager**: scripted wave data, spawn intervals, enemy composition scaling, and boss triggers.
- **Tower system**: targeting rules (first, last, strongest), attack cooldowns, range circles, projectile logic.
- **Enemy system**: movement speed, HP, resistances, status effects, and death rewards.
- **Economy & progression**: starting resources, tower costs, upgrade curves, and difficulty scaling.

### 3) Build a technical architecture
- Create modules:
  - `GameState` (global state)
  - `EntityManager` (towers, enemies, projectiles)
  - `Systems` (pathfinding, combat, waves, rendering)
  - `UI` (HUD, buttons, tooltips)
- Use a fixed-timestep update loop (e.g., 60 updates/sec) with interpolation for smooth rendering.
- Separate game logic from rendering so mechanics are testable.

### 4) Implement MVP in milestones
1. **Milestone A: Core map + pathing**
   - Render map
   - Spawn enemies and move them to goal
   - Lose life when enemies leak
2. **Milestone B: Tower placement + combat**
   - Place tower on valid tile
   - Target enemies and apply damage
   - Currency gain on kills
3. **Milestone C: Waves + progression**
   - Multiple waves and increasing difficulty
   - Tower upgrades and sell system
4. **Milestone D: UX polish**
   - HUD for lives/gold/wave/timer
   - Hover tooltips and range preview
   - Pause, restart, and game-over states

### 5) Content plan
- Towers:
  - Archer (cheap single-target)
  - Cannon (AOE splash)
  - Frost (slow effect)
- Enemies:
  - Runner (fast, low HP)
  - Tank (slow, high HP)
  - Flying (ignores some obstacles)
- Add one map variant and one challenge modifier after MVP ships.

### 6) Balancing and playtesting
- Track KPIs per run: wave reached, average gold spend, lives remaining.
- Create balance sheets for DPS, cost efficiency, and enemy effective HP by wave.
- Iterate with short test cycles:
  - Is early game too punishing?
  - Are upgrades always better than new towers?
  - Are any tower types mandatory or useless?

### 7) QA and reliability
- Unit test pure systems: pathfinding, damage formulas, wave scheduling.
- Add simulation tests for 100+ automated waves to detect crashes or memory leaks.
- Verify edge cases: blocked path placement, sell-during-projectile-flight, pause/resume behavior.

### 8) Release plan
- Ship v0.1 MVP with one map and complete gameplay loop.
- Gather feedback on difficulty, readability, and performance.
- Roadmap for v0.2:
  - New biome/map
  - Skill tree/meta-progression
  - Additional tower/enemy archetypes
