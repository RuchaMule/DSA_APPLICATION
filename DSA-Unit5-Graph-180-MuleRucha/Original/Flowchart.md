## Flowchart

1. **START**

2. Input number of locations and roads.

3. Create weighted graph and enter road distances.

4. Input source and destination.

5. Initialize distances; set source distance = 0.

6. **Priority queue empty?**
   - **Yes:** Check whether destination is reachable.
   - **No:** Remove minimum-distance location from priority queue.

7. Relax adjacent edges and update distances and parents.

8. Repeat the queue loop until the priority queue becomes empty.

9. **Destination reachable?**
   - **Yes:** Display route and total distance.
   - **No:** Display "No path exists".

10. **STOP**

### Note
- Start/Stop: Oval
- Input/Output: Parallelogram
- Processing: Rectangle
- Decision: Diamond
