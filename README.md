
# Experiment No. 7 – Floyd-Warshall Algorithm

**Created By:** Krish Mhatre

## C Program

```c
#include <stdio.h>
#define INF 999

int main() {
    int d[10][10], n, i, j, k;

    printf("Enter number of vertices: ");
    scanf("%d", &n);

    if(n < 1 || n > 10) {
        printf("Invalid number of vertices");
        return 1;
    }

    printf("Enter distance matrix:\n");
    for(i = 0; i < n; i++) {
        for(j = 0; j < n; j++) {
            scanf("%d", &d[i][j]);
        }
    }

    // Floyd-Warshall Algorithm
    for(k = 0; k < n; k++) {
        for(i = 0; i < n; i++) {
            for(j = 0; j < n; j++) {
                if(d[i][k] != INF && d[k][j] != INF &&
                   d[i][k] + d[k][j] < d[i][j]) {
                    d[i][j] = d[i][k] + d[k][j];
                }
            }
        }
    }

    printf("\nShortest Distance Matrix:\n");
    for(i = 0; i < n; i++) {
        for(j = 0; j < n; j++) {
            printf("%d\t", d[i][j]);
        }
        printf("\n");
    }

    return 0;
}
```

## Output

```text
PS C:\AOA> gcc floyd.c -o floyd

PS C:\AOA> .\floyd.exe

Enter number of vertices: 4
Enter distance matrix:
0 5 999 10
999 0 3 999
999 999 0 1
999 999 999 0

Shortest Distance Matrix:
0    5    8    9
999  0    3    4
999  999  0    1
999  999  999  0
```

**Note:** 999 represents Infinity (INF), meaning no path exists between those vertices.

## Aim
To implement the Floyd-Warshall Algorithm to find the shortest paths between all pairs of vertices using C.

## Theory
Floyd-Warshall is a dynamic programming algorithm used to find the shortest paths between every pair of vertices in a weighted graph.

It checks whether a shorter path exists through an intermediate vertex and updates the distance matrix.

## Algorithm
1. Start the program.
2. Enter the number of vertices.
3. Enter the distance matrix.
4. Select each vertex as an intermediate vertex.
5. Compare the direct distance with the distance through the intermediate vertex.
6. Update the matrix if a shorter path is found.
7. Display the final shortest distance matrix.

## How to Run

**Step 1:** Save the file as `floyd.c`.

**Step 2:** Compile the program:

```bash
gcc floyd.c -o floyd
```

**Step 3:** Run in PowerShell:

```powershell
.\floyd.exe
```

## Time Complexity

| Case | Complexity |
|------|------------|
| Best Case | O(V³) |
| Average Case | O(V³) |
| Worst Case | O(V³) |

**Space Complexity:** O(V²)

Where V = Number of vertices.

## Conclusion
Successfully implemented the Floyd-Warshall Algorithm in C to find the shortest distances between all pairs of vertices.
