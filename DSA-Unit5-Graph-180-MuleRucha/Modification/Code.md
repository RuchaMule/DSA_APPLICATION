'''
#include <iostream>
#include <climits>
using namespace std;

#define MAX 20

int graph[MAX][MAX];
int dist[MAX], visited[MAX], parent[MAX];

void dijkstra(int n, int source, int destination)
{
    int i, j, u, minDist;

    for (i = 0; i < n; i++)
    {
        dist[i] = INT_MAX;
        visited[i] = 0;
        parent[i] = -1;
    }

    dist[source] = 0;

    for (i = 0; i < n; i++)
    {
        minDist = INT_MAX;
        u = -1;

        for (j = 0; j < n; j++)
        {
            if (!visited[j] && dist[j] < minDist)
            {
                minDist = dist[j];
                u = j;
            }
        }

        if (u == -1)
            break;

        visited[u] = 1;

        for (j = 0; j < n; j++)
        {
            if (graph[u][j] != -1 &&
                !visited[j] &&
                dist[u] != INT_MAX &&
                dist[u] + graph[u][j] < dist[j])
            {
                dist[j] = dist[u] + graph[u][j];
                parent[j] = u;
            }
        }
    }

    if (dist[destination] == INT_MAX)
    {
        cout << "No path exists between source and destination.\n";
        return;
    }

    int path[MAX], count = 0;
    int v = destination;

    while (v != -1)
    {
        path[count++] = v;
        v = parent[v];
    }

    cout << "Shortest route: ";

    for (i = count - 1; i >= 0; i--)
    {
        cout << path[i];

        if (i > 0)
            cout << " -> ";
    }

    cout << "\nTotal distance: " << dist[destination] << endl;
}

int main()
{
    int n, m, i, j;
    int u, v, w, source, destination;

    cout << "Enter number of locations: ";
    cin >> n;

    if (n <= 0 || n > MAX)
    {
        cout << "Invalid number of locations!\n";
        return 0;
    }

    for (i = 0; i < n; i++)
    {
        for (j = 0; j < n; j++)
        {
            graph[i][j] = -1;
        }
    }

    cout << "Enter number of roads: ";
    cin >> m;

    cout << "Enter roads (source destination distance):\n";

    for (i = 0; i < m; i++)
    {
        cin >> u >> v >> w;

        if (u < 0 || u >= n || v < 0 ||
            v >= n || w < 0)
        {
            cout << "Invalid road details!\n";
            return 0;
        }

        graph[u][v] = w;
        graph[v][u] = w;
    }

    cout << "Enter source location: ";
    cin >> source;

    cout << "Enter destination location: ";
    cin >> destination;

    if (source < 0 || source >= n ||
        destination < 0 || destination >= n)
    {
        cout << "Invalid source or destination!\n";
        return 0;
    }

    cout << "\n--- Before Update ---\n";
    dijkstra(n, source, destination);

    cout << "\nEnter new road (source destination distance): ";
    cin >> u >> v >> w;

    if (u < 0 || u >= n || v < 0 ||
        v >= n || w < 0)
    {
        cout << "Invalid road details!\n";
        return 0;
    }

    graph[u][v] = w;
    graph[v][u] = w;

    cout << "\nUpdated graph:\n";

    for (i = 0; i < n; i++)
    {
        cout << i << " -> ";

        for (j = 0; j < n; j++)
        {
            if (graph[i][j] != -1)
            {
                cout << "(" << j << ", "
                     << graph[i][j] << ") ";
            }
        }

        cout << endl;
    }

    cout << "\n--- After Update ---\n";
    dijkstra(n, source, destination);

    cout << "\n--- Comparison ---\n";
    cout << "Shortest-path results displayed before and after update.\n";
    cout << "Adding a road may reduce or maintain the shortest distance.\n";

    return 0;
}
'''
