# Data-Structure-Mini-Project-1

# Snake and Ladder: BFS Shortest-Path Solver

A small Python mini project that models a Snake and Ladder board as a graph and uses **Breadth-First Search (BFS)** to find a route from the starting square to the finish with the fewest dice throws.

## Features

- Standard 100-square board and six-sided die
- Snakes and ladders represented as square-to-square jumps
- BFS shortest-path search with route reconstruction
- Validation for board size, die size, and jump locations
- Clear handling of rolls that would overshoot the finish (they are ignored)
- No third-party packages required

## Requirements

- Python 3.10 or newer

## Run

From this folder, run:

```bash
python snake_ladder_bfs.py
```

The program runs on its included sample board and prints the minimum number of throws and one shortest route. Edit `DEFAULT_JUMPS` in `snake_ladder_bfs.py` to use a different arrangement. A jump from a lower to a higher square is a ladder; a jump from a higher to a lower square is a snake.

## How BFS solves the game

Treat each board square as a graph vertex. From square `s`, each valid die roll creates an edge to the square reached after taking any snake or ladder there. Since every edge costs one throw, BFS visits positions in increasing number of throws. The first time it reaches the final square, that route uses the fewest throws. A parent map is used to reconstruct the route.

**Complexity:** For `V` reachable squares and at most `D` die outcomes per square, the search takes `O(V × D)` time and `O(V)` auxiliary space. Here `V` is at most the board size and `D` is the number of die sides.

## Rules used in this implementation

1. The player starts on square 1.
2. The player rolls a die with values from 1 to 6.
3. After moving, a snake or ladder at the landing square is followed immediately.
4. A roll that passes the final square is ignored.
5. The goal is to reach the final square using the fewest throws.

## Example output

The exact route depends on the sample board configuration. Running the program displays output in this form:

```text
SNAKE AND LADDER — BFS SHORTEST-PATH SOLVER
Board: 1 to 100 | Die: 1 to 6
Snakes: 8
Ladders: 8

Minimum dice throws: <number>
Route after snakes/ladders:
1 -> ... -> 30
```

## Project structure

```text
snake-ladder-bfs/
├── README.md
└── snake_ladder_bfs.py
```

## Possible future improvements

- Accept board size, die sides, and jumps from user input or a file
- Show the die value for each move
- Add a graphical board and animated gameplay
- Compare BFS with other search strategies

## License

This project is provided for educational use. Add a license file if you choose a specific open-source license before publishing.