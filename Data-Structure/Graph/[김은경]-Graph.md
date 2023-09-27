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

## 그래프 구현 방법

## 그래프 탐색

### 깊이 우선 탐색(DFS)

### 넓이 우선 탐색(BFS)




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
```
