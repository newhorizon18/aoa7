
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
    for(i = 0; i < n; i++)
        for(j = 0; j < n; j++)
            scanf("%d", &d[i][j]);

    for(k = 0; k < n; k++) {
        for(i = 0; i < n; i++) {
            for(j = 0; j < n; j++) {
                if(d[i][k] != INF &&
                   d[k][j] != INF &&
                   d[i][k] + d[k][j] < d[i][j])
                    d[i][j] = d[i][k] + d[k][j];
            }
        }
    }

    printf("\nShortest Distance Matrix:\n");
    for(i = 0; i < n; i++) {
        for(j = 0; j < n; j++)
            printf("%d\t", d[i][j]);
        printf("\n");
    }

    return 0;
}
```

## Terminal Input (Copy and Paste)

```text
4
0 5 999 10
999 0 3 999
999 999 0 1
999 999 999 0
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

**Note:** 999 represents Infinity (no available path). This example assumes finite path costs remain below 999.

## Aim
To implement Floyd-Warshall Algorithm using C.

## Theory
Floyd-Warshall is a dynamic programming algorithm used to find the shortest paths between all pairs of vertices.

It checks whether a shorter path exists through an intermediate vertex.

## Algorithm
1. Enter the number of vertices.
2. Enter the distance matrix.
3. Select an intermediate vertex.
4. Compare direct and indirect distances.
5. Update if a shorter path is found.
6. Display the final matrix.

## How to Run

Save as `floyd.c`.

Compile:

```bash
gcc floyd.c -o floyd
```

Run:

```powershell
.\floyd.exe
```

Paste the input from the Terminal Input section.

## Time Complexity

- Best Case: O(V³)
- Average Case: O(V³)
- Worst Case: O(V³)
- Space Complexity: O(V²)

## Conclusion
Successfully implemented Floyd-Warshall Algorithm in C to find shortest paths between all pairs of vertices.
