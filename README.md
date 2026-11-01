# Depth First Search (DFS) implementation for a warehouse graph

# Sample warehouse graph as an adjacency list
warehouse_graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}

# Function to perform DFS
def dfs(graph, start, goal, visited=None, path=None):
    if visited is None:
        visited = set()

    if path is None:
        path = []

    # Mark current node as visited and add it to the path
    visited.add(start)
    path.append(start)

    # If the goal is found, return the path
    if start == goal:
        return path

    # Explore neighboring nodes
    for neighbor in graph[start]:
        if neighbor not in visited:
            result = dfs(graph, neighbor, goal, visited, path[:])

            if result:
                return result

    return None

# Example usage
start_node = 'A'
goal_node = 'F'

path_found = dfs(warehouse_graph, start_node, goal_node)

print(f"DFS Path from {start_node} to {goal_node}: {path_found}")
