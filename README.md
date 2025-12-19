### CoinCrawler
CoinCrawler is a deterministic grid‑navigation engine implemented in Scala 3, designed around constrained movement, collision handling, and region‑based coin aggregation. The system models a 10×10 board with walls, coins, and player state, and exposes a minimal API for movement, scoring, and path suggestion under strict structural rules.

## Architecture & Framework
Language: Scala
Paradigm: Functional / Imperative hybrid
Runtime: JVM (Liberica / OpenJDK)
Testing: JUnit
IDE: IntelliJ IDEA
The project intentionally avoids external frameworks to keep the logic transparent, testable, and self‑contained.

## Core Mechanics:
Movement
- Commands: w (up), a (left), s (down), d (right)
- Movement is atomic and validated against board boundaries and walls
- Illegal moves are ignored without side effects
  
Coin Handling
- Positive cell values represent coins
- Entering a coin cell increments the score and clears the cell
- Re‑entry yields no additional points
  
Save & Region Sweep
- save() stores the current coordinates
- Subsequent movement defines an axis‑aligned rectangle
- When the rectangle covers ≥ 9 cells, all coins inside are collected
- Saved coordinates reset after a sweep
  
Path Suggestion
suggestMove(x, y) returns a deterministic two‑segment path (horizontal→vertical or vertical→horizontal) that:
- Avoids walls
- Respects board boundaries
- Returns an empty string if no valid path exists
- Does not mutate game state

## Project Structure
src/
 └── cw/
      ├── Game.scala            // Core engine
      ├── GameBuilder.scala     // Board initialization utilities
      └── GameApp.scala         // Entry point


## Guidelines for running the Project
- Open the project in IntelliJ with Scala  support
- Scala-sdk should be added as a dependency as well.
- Download Junit4 in the library and add in the dependency to run the tests.
- Run GameApp.scala to play the game.

## Testing
The engine is validated through unit tests covering:
- Boundary conditions
- Wall collisions
- Coin collection semantics
- Region sweep correctness
- Path suggestion validity
- Board initialization

## Purpose of the framework
CoinCrawler serves as a compact demonstration of:
- Grid‑based state management
- Algorithmic reasoning
- Deterministic movement systems
- Test‑driven development in Scala
- Clean, framework‑independent design


## Authors
Sanjana Akter Jemi

