```
## Algorithm

1. Start.

2. Read the number of locations and roads.

3. Create a weighted graph and store each road with its distance.

4. Read the source and destination locations.

5. Initialize all distances to infinity and parent values to -1.

6. Set the source distance to 0 and insert it into the priority queue.

7. Remove the location with the minimum distance from the priority queue.

8. Update the distances of its adjacent locations if a shorter route is found.

9. Repeat until the priority queue becomes empty.

10. If the destination distance is infinity, display "No path exists."

11. Otherwise, display the shortest route and total distance.

12. Stop.
```
