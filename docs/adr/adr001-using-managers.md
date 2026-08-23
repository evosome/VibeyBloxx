# ADR-001: Using Managers to control game components and data

## Context
I am developing a game where both technical details and game mechanics may change frequently. I also need to support the codebase up to version 0.2. For this situation, it would be great to write flexible and easily replaceable code.

## Decision
I will use Managers to control game data and specific game components. Managers will contain the core business logic for their specific areas. This approach makes it painless to remove an entire Manager script or replace it with a new one, since the logic is self-contained.

To ensure Managers remain easy to remove, I follow these rules:
1. A Manager controls only the data classes that correspond to its specific domain (e.g., the WeatherManager controls only Weather instances and may refer to the World to apply weather parameters, but does not touch other systems).
2. Ideally, Managers should not directly know about or reference each other to maintain loose coupling and independence.