# IranMaze

▶ **Play: https://shay-silversmith.github.io/IranMaze/**

A browser port of the maze game built for the ATP course (Advanced Topics in Programming).
No install, no account — open the link, set a size, press **Start**.

Developers: **Shay & Ellen**

## The game

Fly the B-2 through a randomly generated maze to reach the target.

- **Move** — arrow keys, WASD, or the on-screen pad on touch devices
- **Show Solution** — draws the path found by the algorithm you picked
- **Properties** — switch between BFS, DFS and Best First Search
- **Save** — stores the current maze in your browser so you can resume later
- **Ctrl + scroll** — zoom

## About this port

The original is a JavaFX desktop application (MVVM: Model / ViewModel / View + FXML),
which cannot run in a browser. This is a single self-contained HTML file — all artwork,
music and sound effects are embedded, so it runs from any static host with no backend.

The algorithms were ported directly from the Java source:

| Original (Java) | Notes |
| --- | --- |
| `MyMazeGenerator` | Randomised DFS (recursive backtracker), entry/exit carved on the borders |
| `SearchableMaze` | 8-directional successors; a diagonal is legal only if both of its orthogonal neighbours are free |
| `BreadthFirstSearch` | FIFO frontier — shortest path |
| `DepthFirstSearch` | LIFO frontier |
| `BestFirstSearch` | Uniform-cost: orthogonal 10, diagonal 15 |

Two desktop-only features were adapted rather than dropped: **Save** writes to browser
storage instead of a compressed `.maze` file, and **Exit** returns to the menu. The
client/server solving path from Part B is not used — the solvers run locally in the page.

Assets were recompressed from 58 MB to ~3.4 MB (WebP images, MP3 audio) so the whole
game fits in one file.

## Running it elsewhere

`index.html` has no dependencies and no build step. Open it directly, or drop it on any
static host.
