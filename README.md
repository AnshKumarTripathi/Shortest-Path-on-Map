# Shortest-Path-on-Map
🌐 How the Code Finds the Optimal Path:

Relies on OSRM API:

Uses Open Source Routing Machine (OSRM), a precomputed routing engine that employs Contraction Hierarchies (a speed-optimized pathfinding algorithm).
OSRM pre-processes road networks to enable millisecond-level route calculations.

Workflow:

Input: User-placed coordinates (latitude/longitude) are validated and normalized.

API Request: Coordinates are sent to OSRM’s /route/v1/driving/ endpoint as lng,lat pairs.

Path Calculation: OSRM:

Models the road network as a graph (nodes = intersections, edges = road segments with weights = travel time/distance).

Uses bidirectional Dijkstra’s algorithm with hierarchical optimizations to find the shortest path.

Accounts for real-world constraints (one-way streets, turn restrictions).

Response: Returns GeoJSON coordinates of the optimal path + total distance.

Key Advantages:

Not Straight-Line Distance: Calculates actual drivable paths on road networks.

Efficiency: Processes 1,000+ node routes in milliseconds via precomputed hierarchies.

Accuracy: Uses constantly updated OpenStreetMap data.

Limitations:

Requires internet (depends on OSRM’s external service).

Sequential routing (not true TSP optimization).

Why Not A?*
While A* is great for grid-based pathfinding (games/mazes), OSRM uses road-network-optimized algorithms better suited for real-world navigation with complex constraints. The heavy lifting is delegated to OSRM’s specialized engine rather than implementing pathfinding locally.
