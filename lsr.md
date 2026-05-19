import java.util.*;

public class LinkStateRouting {
    static final int INF = 9999;

    public static void dijkstra(int[][] graph, int source, int n) {
        int[] distance = new int[n];
        boolean[] visited = new boolean[n];

        for (int i = 0; i < n; i++) {
            distance[i] = INF;
            visited[i] = false;
        }

        distance[source] = 0;

        for (int count = 0; count < n - 1; count++) {
            int min = INF;
            int u = -1;

            for (int i = 0; i < n; i++) {
                if (!visited[i] && distance[i] <= min) {
                    min = distance[i];
                    u = i;
                }
            }

            visited[u] = true;

            for (int v = 0; v < n; v++) {
                if (!visited[v] && graph[u][v] != 0 &&
                        distance[u] + graph[u][v] < distance[v]) {
                    distance[v] = distance[u] + graph[u][v];
                }
            }
        }

        System.out.println("\nShortest distances from source node " + source + ":");
        for (int i = 0; i < n; i++) {
            System.out.println("To node " + i + " = " + distance[i]);
        }
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        System.out.print("Enter number of nodes: ");
        int n = sc.nextInt();

        int[][] graph = new int[n][n];

        System.out.println("Enter cost matrix:");
        for (int i = 0; i < n; i++) {
            for (int j = 0; j < n; j++) {
                graph[i][j] = sc.nextInt();
            }
        }

        System.out.print("Enter source node: ");
        int source = sc.nextInt();

        dijkstra(graph, source, n);

        sc.close();
    }
}
