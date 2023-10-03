# 자료구조 - 그래프 

## 용어
[용어에 대한 그림 설명](https://hongcoding.tistory.com/78)
* 정점(Vertex): 노드라고 불리기도 하며 정점에는 데이터가 저장된다
* 간선(Edge): 노드를 연결하는 선
* 인접 정점(adjacent Vertex): 간선에 의해 직접 연결된 정점 
* 단순 경로(simple path): 경로 중에서 반복되는 정점이 없는 경우, 같은 간선을 지나가지 않는 경로 
* 차수(degree): 무방향 그래프에서 하나의 정점에 인접한 정점의 수 
* 진출 차수(in-degree): 방향 그래프에서 외부로 향하는 간선의 수
* 진입 차수(out-degree): 방향 그래프에서 외부에서 들어오는 간선의 수
* 경로 길이(path length): 경로를 구성하는데 사용된 간선의 수 
* 사이클(cycle): 단순 경로 시작 정점과 종료 정점이 동일한 경우

## 그래프 종류
![06_graph2](https://github.com/Luna828/CS-Study/assets/93186591/7e24b1b9-fecd-407e-919e-79b3ffb967ad)
* 무방향 그래프 : 두 정점을 연결하는 간선에 `방향이 없는` 그래프이며, `양방향` 이동 가능, (1, 2) (2, 1)은 동일한 표현이다
* 방향 그래프: 간선에 방향이 존재하며, `간선의 방향`으로만 이동 가능 <1, 7> 이라고 표현한다 만약 <7, 1> 이라고 쓰면 방향이 다르기에 ❌
* 가중치 그래프: 간선에 비용 OR 가중치 할당된 그래프 == 네트워크 (정점 사이의 이동거리,이동시간,이동비용)을 나타낼 때 사용
* 루트없는 트리: 간선을 통해 정점 간 잇는 방법이 한가지인 그래프 
* 이분 그래프: 그래프의 정점을 겹치지 않게 두 그룹으로 나눈 후 다른 그룹끼리만 간선이 존재하게 분할 할 수 있음
* 사이클없는 방향 그래프: 정점에서 출발해 자기 자신으로 돌아오는 경로(사이클) 없는 그래프

## 그래프 구현 방법
1. 인접 행렬
 - 2차원 배열 이용
 - 두 개의 노드가 간선으로 연결되어 있다면 인접할 수 있다
 - 인접 행렬에 그래프의 간선 정보를 저장
 - 간선의 존재 유무 -> 존재시: [i][j] = 1 / 존재❌ = [i][j] = 0

![R1280x0-6](https://github.com/Luna828/CS-Study/assets/93186591/552c94cf-a62f-4044-ad93-d30658944d66)
![R1280x0-5](https://github.com/Luna828/CS-Study/assets/93186591/8082dbdf-ebbb-4e2b-b5c3-8fd07bd31da7)

2. 인접 리스트
 - 인접 정보 저장 리스트
 - 연결 리스트의 1차원 배열
 - 배열의 크기는 노드의 개수와 같음!
 - 메모리 효율이 좋음 ( 메모리 사용량은 노드 수가 아닌 간선 수에 따라 달라짐)
 - 노드의 추가 삭제가 빠르다

![R1280x0-7](https://github.com/Luna828/CS-Study/assets/93186591/83f8f6b0-d3bf-4184-9222-4834242853aa)
![R1280x0-8](https://github.com/Luna828/CS-Study/assets/93186591/011b468f-8b0a-41e2-808b-27c3f4975c40)

 
## 그래프 탐색

### 깊이 우선 탐색(DFS) -> Depth-First Search

* 스택 또는 재귀함수 구현
* 루트 노드에서 시작해서 다음 분기로 넘어가기 전에 해당 분기를 완벽하게 탐색
* 쉬운말: 최대한 한 방향으로 갈 수 있을 때까지 가다가 없으면 다시 가까운 갈림길로 돌아와서 그 갈림길부터 다른 방향으로 탐색하는 것

![images-lucky-korma-post-30737a15-9adf-49a6-96a0-98c211cab1cc-R1280x0](https://github.com/Luna828/CS-Study/assets/93186591/9e8563f6-38a8-40b7-9d52-789b963963c8)


### 넓이 우선 탐색(BFS) -> Breadth-First Search

* 큐를 이용하여 구현
* 루트노드에서 시작해서 인접한 노드를 먼저 탐색
* 주로 노드 사이의 최단 경로를 찾고 싶을 때 사용

![images-lucky-korma-post-2112183b-bfcd-427e-8072-c9dc983180ba-R1280x0-2](https://github.com/Luna828/CS-Study/assets/93186591/140daf2e-f7e2-49f4-bc57-bd5fbc96ee64)


## 코드 구현
```swift
// 그래프를 표현하기 위한 노드 클래스 정의
class Node<T> {
    let value: T // 노드의 값
    var neighbors: [Node] // 인접한 노드들
    
    init(value: T) {
        self.value = value
        self.neighbors = []
    }
}

// 그래프 클래스 정의
class Graph<T> {
    var nodes: [Node<T>] // 그래프의 모든 노드들
    
    init() {
        self.nodes = []
    }
    
    // 새로운 노드를 그래프에 추가하는 메서드
    func addNode(value: T) -> Node<T> {
        let newNode = Node(value: value)
        nodes.append(newNode)
        return newNode
    }
    
    // 주어진 값으로부터 해당하는 노드를 찾는 메서드
    func findNode(value: T) -> Node<T>? {
        for node in nodes {
            if node.value == value {
                return node
            }
        }
        
        return nil // 해당하는 값을 가진 노드가 없을 경우 nil 반환
    }
    
    // 주어진 값을 가지는 간선(엣지)을 추가하는 메서드
	func addEdge(from sourceValue: T, to destinationValue: T) {
		guard let sourceNode = findNode(value: sourceValue),
			  let destinationNode = findNode(value: destinationValue)
		else { return } // 시작 노드와 도착 노드가 모두 존재하지 않으면 종료
		
		sourceNode.neighbors.append(destinationNode)
	}
}

// 그래프 생성
let graph = Graph<Int>()

// 노드 추가
let node1 = graph.addNode(value: 1)
let node2 = graph.addNode(value: 2)
let node3 = graph.addNode(value: 3)
let node4 = graph.addNode(value: 4)

// 간선 추가
graph.addEdge(from: 1, to: 2)
graph.addEdge(from: 1, to: 3)
graph.addEdge(from: 2, to: 4)

// 그래프 정보 출력
for node in graph.nodes {
    print("Node value:", node.value)
    
    if !node.neighbors.isEmpty {
        print("Neighbors:")
        for neighbor in node.neighbors {
            print("- Neighbor value:", neighbor.value)
        }
    }
    
    print()
}

```
```text
//출력 결과
Node value: 1
Neighbors:
- Neighbor value: 2
- Neighbor value: 3

Node value: 2
Neighbors:
- Neighbor value: 4

Node value: 3

Node value: 4

```

## 참조
```text
https://80000coding.oopy.io/125156cf-79bb-48da-82ae-1f2ee7896bb8
https://hongcoding.tistory.com/78
https://hsc-tech.tistory.com/12
https://velog.io/@lucky-korma/DFS-BFS의-설명-차이점
```
