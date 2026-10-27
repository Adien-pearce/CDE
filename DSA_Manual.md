# DSA Manual Code

Here is the code and output extracted from the images, formatted for your GitHub repository.

### Experiment 1: Sorting (Bubble Sort & Selection Sort)

**Program 1A: Bubble Sort**
```c
#include <stdio.h>

void bubble_sort(int[], int);

int main()
{
    int arr[30], num, i;
    printf("\nEnter number of students: ");
    scanf("%d", &num);
    printf("\nEnter total marks of students: ");
    for (i = 0; i < num; i++) {
        scanf("%d", &arr[i]);
    }
    
    bubble_sort(arr, num);
    
    printf("\nSorted marks are: ");
    for (i = 0; i < num; i++) {
        printf("%d", arr[i]);
    }
    return 0;
}

void bubble_sort(int arr[], int num)
{
    int i, j, temp;
    for (i = 0; i < num - 1; i++) {
        for (j = 0; j < num - 1 - i; j++) {
            if (arr[j] > arr[j + 1]) {
                temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
```

**Output (1A):**
```text
Enter no of students:5
Enter total marks of students:45
42
47
15
49
Sorted marks are: 15 42 45 47 49
```

**Program 1B: Selection Sort**
```c
#include <stdio.h>
#include <conio.h>

void selection_sort(int [], int);

void main() {
    int a[50], n, i;
    clrscr();
    
    printf("\nEnter no of students: ");
    scanf("%d", &n);
    
    printf("\nEnter marks of %d students:\n", n);
    for (i = 0; i < n; i++)
        scanf("%d", &a[i]);
        
    selection_sort(a, n);
    
    getch();
}

void selection_sort(int a[], int n) {
    int i, j, k, temp;
    
    printf("\nUnsorted data: ");
    for (k = 0; k < n; k++)
        printf("%5d", a[k]);
        
    for (i = 0; i < n - 1; i++) {
        k = i;
        for (j = i + 1; j < n; j++) {
            if (a[j] < a[k])
                k = j;
        }
        if (k != i) {
            temp = a[i];
            a[i] = a[k];
            a[k] = temp;
        }
    }
    
    printf("\nSorted data: ");
    for (k = 0; k < n; k++)
        printf("%5d", a[k]);
}
```

**Output (1B):**
```text
Enter no of students:5
Enter no of marks :65
75
92
30
50
Unsorted data: 65 75 92 30 50
Sorted data: 30 50 65 75 92
```

---

### Experiment 7: Dynamic Programming (Dijkstra's Algorithm)

**Program Code:**
```c
#include <stdio.h>
#include <limits.h>

#define V 100 // Maximum number of nodes
#define INF INT_MAX

// Function to find the vertex with minimum distance value
int minDistance(int dist[], int visited[], int n) {
    int min = INF, min_index;
    
    for (int v = 0; v < n; v++)
        if (!visited[v] && dist[v] <= min)
            min = dist[v], min_index = v;
            
    return min_index;
}

// Dijkstra's algorithm to find shortest paths from src to all vertices
void dijkstra(int graph[V][V], int src, int n) {
    int dist[V]; // Shortest distance from src to i
    int visited[V]; // Visited vertices
    
    for (int i = 0; i < n; i++) {
        dist[i] = INF;
        visited[i] = 0;
    }
    
    dist[src] = 0;
    
    for (int count = 0; count < n - 1; count++) {
        int u = minDistance(dist, visited, n);
        visited[u] = 1;
        
        for (int v = 0; v < n; v++)
            if (!visited[v] && graph[u][v] && dist[u] != INF 
                && dist[u] + graph[u][v] < dist[v])
                dist[v] = dist[u] + graph[u][v];
    }
    
    // Print the shortest distances
    printf("Shortest distances from source node %d:\n", src);
    for (int i = 0; i < n; i++)
        printf("To node %d: %d\n", i, dist[i]);
}

// Main function
int main() {
    int n; // number of nodes (e.g., intersections)
    printf("Enter number of nodes (e.g., locations in the city): ");
    scanf("%d", &n);
    
    int graph[V][V];
    
    printf("Enter the adjacency matrix (use 0 if no direct road):\n");
    for (int i = 0; i < n; i++)
        for (int j = 0; j < n; j++)
            scanf("%d", &graph[i][j]);
            
    int src;
    printf("Enter source node (e.g., hospital/fire station): ");
    scanf("%d", &src);
    
    dijkstra(graph, src, n);
    
    return 0;
}
```

**Output:**
```text
Enter number of nodes (e.g., locations in the city): 5
Enter the adjacency matrix (use 0 if no direct road):
0 10 0 30 100
10 0 50 0 0
0 50 0 20 10
30 0 20 0 60
100 0 10 60 0
Enter source node (e.g., hospital/fire station): 0
Shortest distances from source node 0:
To node 0: 0
To node 1: 10
To node 2: 50
To node 3: 30
To node 4: 60
```
