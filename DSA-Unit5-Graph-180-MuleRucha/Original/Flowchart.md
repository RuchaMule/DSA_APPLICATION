## Flowchart

1. START

2. Input the number of locations and roads.

3. Create a weighted graph and enter road distances.

4. Input source and destination.

5. Initialize distances and set source distance = 0.

6. Check whether the priority queue is empty.

7. If **No**:
   - Remove the minimum-distance location.
   - Relax adjacent edges and update distances and parents.
   - Repeat the queue loop.

8. If **Yes**:
   - Check whether the destination is reachable.
   - If **Yes**, display the shortest route and total distance.
   - If **No**, display "No path exists".

9. STOP

**Note:** Draw Start/Stop in ovals, input/output steps in parallelograms, processing steps in rectangles, and decision steps in diamonds.
