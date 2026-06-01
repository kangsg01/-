//1일 포인터
#include <stdio.h>
int main() {
    int num = 10;// 일반 정수형 변수 선언
    int *ptr;// 정수형을 가리키는 포인터 변수 선언
    ptr = &num;// num 변수의 주소값을 포인터 ptr에 저장
    printf("num의 원래 값: %d\n", num);
    printf("num의 주소값: %p\n", &num);
    printf("ptr이 가리키는 주소값: %p\n", ptr);
    printf("ptr이 가리키는 곳의 값: %d\n\n", *ptr);
    *ptr = 20;// 포인터를 통해 num 변수의 값을 20으로 변경
    printf("변경된 num의 값: %d\n", num);
    return 0;
}

//2일 프림
#include <stdio.h>

#define V 5
#define INF 999999

int minKey(int key[], int mstSet[]) {
    int min = INF, min_index;

    for (int v = 0; v < V; v++) {
        if (mstSet[v] == 0 && key[v] < min) {
            min = key[v];
            min_index = v;
        }
    }

    return min_index;
}

void printMST(int parent[], int graph[V][V]) {
    printf("간선 \t가중치\n");

    for (int i = 1; i < V; i++) {
        printf("%d - %d \t%d\n",
               parent[i], i, graph[i][parent[i]]);
    }
}

void primMST(int graph[V][V]) {
    int parent[V];
    int key[V];
    int mstSet[V];

    for (int i = 0; i < V; i++) {
        key[i] = INF;
        mstSet[i] = 0;
    }

    key[0] = 0;
    parent[0] = -1;

    for (int count = 0; count < V - 1; count++) {
        int u = minKey(key, mstSet);
        mstSet[u] = 1;

        for (int v = 0; v < V; v++) {
            if (graph[u][v] &&
                mstSet[v] == 0 &&
                graph[u][v] < key[v]) {

                parent[v] = u;
                key[v] = graph[u][v];
            }
        }
    }

    printMST(parent, graph);
}

int main() {
    int graph[V][V] = {
        {0, 2, 0, 6, 0},
        {2, 0, 3, 8, 5},
        {0, 3, 0, 0, 7},
        {6, 8, 0, 0, 9},
        {0, 5, 7, 9, 0}
    };

    primMST(graph);

    return 0;
}

//3일 크루스칼
#include <stdio.h>
#include <stdlib.h>

typedef struct {
    int u, v, weight;
} Edge;

int parent[100];

int find(int x) {
    if (parent[x] == x)
        return x;
    return parent[x] = find(parent[x]);
}

void unite(int a, int b) {
    a = find(a);
    b = find(b);

    if (a != b)
        parent[b] = a;
}

int compare(const void *a, const void *b) {
    Edge *e1 = (Edge *)a;
    Edge *e2 = (Edge *)b;
    return e1->weight - e2->weight;
}

int main() {
    int V, E;

    scanf("%d %d", &V, &E);

    Edge edges[E];

    for (int i = 0; i < E; i++) {
        scanf("%d %d %d", &edges[i].u, &edges[i].v, &edges[i].weight);
    }

    for (int i = 1; i <= V; i++) {
        parent[i] = i;
    }

    qsort(edges, E, sizeof(Edge), compare);

    int mstWeight = 0;

    for (int i = 0; i < E; i++) {
        int u = edges[i].u;
        int v = edges[i].v;
        int w = edges[i].weight;

        if (find(u) != find(v)) {
            unite(u, v);
            mstWeight += w;

            printf("%d - %d (%d)\n", u, v, w);
        }
    }

    printf("MST Weight = %d\n", mstWeight);

    //4일 클래스
    class Account:

  interest_rate = 0.02

  def __init__(self, owner, balance):
    self.owner = owner
    self.balance = balance
  
  def deposit(self,amount):
    self.balance += amount

  def apply_interest(self):
    self.balance += self.balance * Account.interest_rate

acc = Account("홍길동", 10000)
acc.deposit(5000)
acc.apply_interest()
print(f"{acc.owner}님의 최종 잔액: {acc.balance}원")

    return 0;
}
