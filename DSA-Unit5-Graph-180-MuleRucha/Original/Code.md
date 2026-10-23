## Code

```cpp
#include <iostream>
#include <limits.h>
using namespace std;

#define MAX 20

int main()
{
    int graph[MAX][MAX];
    int n, m, u, v, w;
    int source, destination;
    int dist[MAX], visited[MAX], parent[MAX];

    cout << "Enter number of locations: ";
    cin >> n;

    if (n <= 0 || n > MAX)
    {
        cout << "Invalid number of locations!";
        return 0;
    }

    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            graph[i][j] = 0;

    cout << "Enter number of roads: ";
    cin >> m;

    cout << "Enter roads (source destination distance):\n";

    for (int i = 0; i < m; i++)
    {
        cin >> u >> v >> w;

        if (u >= 0 && u < n && v >= 0 && v < n && w > 0)
        {
            graph[u][v] = w;
            graph[v][u] = w;
        }
        else
        {
            cout << "Invalid road details!";
            return 0;
        }
    }

    cout << "Enter source location: ";
    cin >> source;

    cout << "Enter destination location: ";
    cin >> destination;

    if (source < 0 || source >= n ||
        destination < 0 || destination >= n)
    {
        cout << "Invalid location!";
        return 0;
    }

    for (int i = 0; i < n; i++)
    {
        dist[i] = INT_MAX;
        visited[i] = 0;
        parent[i] = -1;
    }

    dist[source] = 0;

    for (int count = 0; count < n; count++)
    {
        int minDist = INT_MAX;
        int current = -1;

        for (int i = 0; i < n; i++)
        {
            if (!visited[i] && dist[i] < minDist)
            {
                minDist = dist[i];
                current = i;
            }
        }

        if (current == -1)
            break;

        visited[current] = 1;

        for (int j = 0; j < n; j++)
        {
            if (graph[current][j] > 0 && !visited[j])
            {
                if (dist[current] + graph[current][j] < dist[j])
                {
                    dist[j] = dist[current] + graph[current][j];
                    parent[j] = current;
                }
            }
        }
    }

    if (dist[destination] == INT_MAX)
    {
        cout << "No path exists between source and destination.";
    }
    else
    {
        int path[MAX], count = 0;
        int current = destination;

        while (current != -1)
        {
            path[count++] = current;
            current = parent[current];
        }

        cout << "\nShortest route: ";

        for (int i = count - 1; i >= 0; i--)
        {
            cout << path[i];

            if (i > 0)
                cout << " -> ";
        }

        cout << "\nTotal distance: " << dist[destination];
    }

    return 0;
}
```
