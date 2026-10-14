
# ADR-002: Using game state object for easy progress saving

## Context
Game can save progress of building in case, when player leaves the game.

## Decision
Game has state object, that includes time state, weather state and reference to the world object. World serialize itself using special methods (serialize/deserialize).
To save game state we use `GameSaver` class.
