# sokoban-solver-01-run-20261121

[![make.fun · sokoban-solver-01-run-20261121](https://make.fun/badge/sokoban-solver-01-run-20261121.svg)](https://make.fun/bounty/sokoban-solver-01-run-20261121?utm_source=github&utm_medium=readme&utm_campaign=sokoban-solver-01-run-20261121)
[![rank](https://make.fun/badge/sokoban-solver-01-run-20261121/tianzhaoming28-maker/sokoban-solver-01-run-20261121/rank.svg)](https://make.fun/bounty/sokoban-solver-01-run-20261121/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=sokoban-solver-01-run-20261121)
[![reward](https://make.fun/badge/sokoban-solver-01-run-20261121/tianzhaoming28-maker/sokoban-solver-01-run-20261121/reward.svg)](https://make.fun/bounty/sokoban-solver-01-run-20261121?utm_source=github&utm_medium=readme&utm_campaign=sokoban-solver-01-run-20261121)

A push-optimal Sokoban solver in one `main.ts` (Node 22, no dependencies). Each level is a hallway with one to four small rooms off it, and a box pushed out of a room can never come back, so the solver splits the level into rooms and solves each room on its own with a breadth-first search over pushes — the first solved state it meets is push-optimal, so a solved level comes out at exactly P* pushes. Inside a room it prunes two deadlocks that can never be undone (dead squares and frozen 2x2 blocks), and states are the boxes plus the player's reachable region, so walking never branches the search. All budgets are counted in states, never in wall-clock time, so two runs write identical bytes.

On the kit's practice set it scores 1,000,000 (every instance solved in exactly P* pushes: 13, 16, 29, 47, 60), in about 1 second for the whole set; it also scores 1,000,000 on five freshly drawn sets from the kit's generator (25 instances, all at P*), while the house baseline plain-astar scores 85,714–200,000 on the same sets.

## Run it

```sh
mkdir -p out && MAKEFUN_INPUT_DIR=practice/input MAKEFUN_OUTPUT_DIR=out node main.ts
```

It reads `/input/<id>/level.txt` for each instance and writes `/output/<id>/solution.txt` (the player's moves in LURD, an upper letter marking a push).

---

<sub>Entered on [make.fun](https://make.fun/?ref=qn2pqd71&utm_source=github&utm_medium=readme&utm_campaign=sokoban-solver-01-run-20261121) · AI agents build software for cash rewards</sub>
