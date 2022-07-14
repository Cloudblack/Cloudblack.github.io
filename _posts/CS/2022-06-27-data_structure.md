---
layout: single
title: "자료구조"
categories:
  - CS
tags:
  - [Data Structure]

toc: true
toc_sticky: true



---

# 자료구조

자료구조는 메모리를 효율적으로 사용하기위해 공부할 필요가있다

- 

- 

## Data Structure Essential (자료구조 본질)

- 효율적인처리

    여러개를 한번에 처리, 반복을 처리 변수처리 등등 더욱 효율적으로 만드는것

- 자료구조

    아무렇게나 있는 자료들을 도서관에서 책정리 하듯이 일정한 룰을 가지고 자료들을 정리 하는것 ⇒왜? 효율적으로 자료를 관리하기위해

    - 데이터의 특성을 파악하고 미리 정해놓은 일정한 규칙에 따라서 체계적으로 데이터를 구조화 시키고 표현
    - 자료구조를 배워야하는 이유
    - 선배 개발자들이 미리 데이터를 잘 표현할 수 있는 방법을 만들어놨다.
    - 데이터에 효율적으로 접근 할 수 있고 처리 할 수 있게 도와준다
    - 파이썬이라는 프로그래밍언어와는 별개로, 실생활에서 발생하는 **대용량의 다양한 데이터를 효율적으로 처리(저장)**하기위해 자료구조라는 개념이 개발되었다.

- array배열

    - 가장 기초적이면서 단수하고 자주 사용되는 자료 구조의 형태
    - 배열의 기능은 각각의 변수를 **하나의 변수에 여러 개의 인덱스**로 묶는 것이다. `예시 : arr[5]`
    - 파이썬에서는 **배열을 리스트와 튜플**로 구현하고 활용한다.
    - 순차적으로 데이터를 나열하면서 저장
    - 파이썬에서는 배열 ⇒ 튜플&리스트
    - 장점: 인덱스를 통해 데이터에 직접적인 접근 ⇒ 빠르게 데이터에 접근가능 단점: 미리 크기 지정⇒ 데이터 추가,제거,교체 불편

- 파이썬의 리스트

    - 파이썬의 리스트는 자료구조의 배열과 연결리스트의 특징을 모두 갖고 있다.
        - 배열의 특징 : **인덱스 사용**하여 노드에 접근가능
        - 연결리스트의 특징 : **인덱스 크기**를 자유롭게 확장가능, **서로 다른 자료형**을 노드로 갖을 수 있다.
        - 즉, 파이썬이라는 프로그래밍 언어는 기존 프로그래밍에서 발생한 어려운 점을 **부분적으로 개선**시켰다는 것을 알 수 있다.
    - 자료구조의 기본은 **배열**이라 할 수 있고, 파이썬에서는 **리스트와 튜플**로 구현할 수 있다.
    - 리스트나 튜플의 핵심은 **인덱스**를 사용하는 것이다.
    - 파이썬의 리스트는 자료구조와 알고리즘에서 가장 많이 볼 수 있는 활용법이므로 자주 보면서 익숙해지자.

- 빅O 표기법

    - 시간 복잡도

        - 입력값에 따른 시간의 증가도
        - 시간 복잡도 측면에서의 효율적인 알고리즘 → 입력값이 증가함에 따라 시간의 증가 비율을 최소화한 알고리즘 -빅 오 표기법은 시간복잡도에서 많이 사용된다

    - 공간복잡도

        -하드웨어의 성능이 증가하면서 공간 복잡도보다, 소프트웨어의 성능인 **시간 복잡도**가 더 중요하다. -메모리(저장공간) 관련된 효율성 ⇒ 분석 ,**얼마만큼 메모리 저장 공간**이 필요한지.

    표기법

    - 입력값 n의 가장 큰 차수만 표기 -상수의 항을 고려하지 않는다

## Array

- 배열은 하나의 변수에 여러개의 값을 순차적으로 저장한것이다
- 처음에 지정한 배열의 공간이 부족해지면 추가를 할수없어 더큰 배열로 옮겨야한다
- ![image-20220628222930509](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220628222930509.png)
- Reading
    - 컴퓨터에서 어디서 배열이 시작되는지 알고 순차적으로 정렬되어있기 때문에 배열의 길이에 관계없이 인덱스를 활용해 데이터에 빠르게 접근할 수 있다
- Search
    - 어디에 있는지 몰라 찾아봐야 해 열어보고 맞는지 체크를해야해 reading에 비해 느리다
    - Linear Search (선형검색)
        - 처음부터 끝까지 순차적으로 하나씩 열어보고 맞는지 체크
        - 최고 - 시작하자마자 찾은경우
        - 보통 - 중간에있는경우
        - 최악 - 마지막에있는경우
        - 찐최악 - 없는경우
- Insert (add)
    - 최고 - 마지막에 넣는경우 마지막 인덱스에 넣기만하면됨
    - 보통 - 중간에 넣는경우 넣는위치 이후의 값들을 전부 뒤로 밀어야한다
    - 최악 - 맨앞에 넣는 경우 모든 값들을 뒤로 밀어야한다
    - 최최악 - 배열이 꽉차서 늘려서 담아야하는 경우 크기에맞는 배열을 새로만들고 기존것을 옮기고 추가
- Delete
    - insert와 비슷하다
    - 최고 - 마지막 값을 지우는경우 바로 지울수있음
    - 보통 - 중간 값을 지우면 이후값을 앞으로 떙긴다
    - 최악 - 맨앞을 삭제하면 뒤의값을 전부 앞으로 땡겨야한다

## LinkedList

- 노드안에 값과 포인터/링크(다음노드의)를 포함하고있다
- 링크로 가져오는거라 메모리를 연속으로 차지하지않는다
- 단방향,양방향 연결리스트가있다

장점

- 노드를 추가하거나 삭제하기 편하다 ⇒>O(1)
    - 이전/다음 노드 정보만 바꿔줘서 chain만 끊고 새로 연결하면 됨
    - 메모리 동적으로 활용 가능

단점

- 빠른 데이터 접근이 어렵다.
    - 바로 바로 찾을 수 없다. 다음 노드 정보를 타고 타고 찾아가야한다.
    - 첫 노드(head)부터 차례대로 값을 탐색해야한다⇒O(n)

- ![img](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/2928.png)
- linked list는 두가지 정보가 필요하다 
    - 1. data field 
        2. link field 
- <img src="https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/2939.png" alt="img" style="zoom:67%;" />
- HEAD는 시작점을 가르킨다
- array와 linked list의 trade off

<img src="https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/2885.png" alt="img" style="zoom:67%;" />

## HashTable

- HashTable 개념

    - Key와 Value를 1:1로 연관지어 저장하는 자료구조 (연관배열 구조)
    - Key를 이용하여 Value 도출

- HashTable 기능

    - 연관배열 구조와 동일한 기능 지원
    - Key, Value가 주어졌을 때, 두 값을 저장
    - Key가 주어졌을 때, 해당 Key에 연관된 Value 조회
    - 기존 Key에 새로운 Value가 주어졌을 때, 기존 Value를 새로운 Value로 대체
    - Key가 주어졌을 때, 해당 Key에 연관된 Value 제거

- HashTable 구조

    [![hashtable](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/hashtable.png)](https://github.com/WeareSoft/tech-interview/blob/master/contents/images/hashtable.png)

    - Key, Hash Function, Hash, Value, 저장소(Bucket, Slot)로 구성
    - Key
        - 고유한 값
        - 저장 공간의 효율성을 위해 Hash Function에 입력하여 Hash로 변경 후 저장
            - Key는 길이가 다양하기 때문에 그대로 저장하면 다양한 길이만큼 저장소 구성이 필요
    - Hash Function
        - Key를 Hash로 바꿔주는 역할
        - 해시 충돌(서로 다른 Key가 같은 Hash가 되는 경우)이 발생할 확률을 최대한 줄이는 함수를 만드는 것이 중요
    - Hash
        - Hash Function의 결과
        - 저장소에서 Value와 매칭되어 저장
    - Value
        - 저장소에 최종적으로 저장되는 값
        - 키와 매칭되어 저장, 삭제, 검색, 접근 가능

- HashTable 동작 과정

    1. Key -> Hash Function -> Hash Function 결과 = Hash
    2. Hash를 배열의 Index로 사용
    3. 해당 Index에 Value 저장

    - HashTable 크기가 10이라면 A라는 Key의 Value를 찾을 때 hashFunction("A") % 10 연산을 통해 인덱스 값 계산하여 Value 조회

- Hash 충돌

    - 서로 다른 Key가 Hash Function에서 중복 Hash로 나오는 경우
    - 충돌이 많아질수록 탐색의 시간 복잡도가 O(1)에서 O(n)으로 증가

- Hash 충돌 해결 방법

    1. Separating Chaining
        - JDK 내부에서 사용하는 충돌 처리 방식
        - Linked List(데이터 6개 이하) 또는 Red-Black Tree(데이터 8개 이상) 사용 [![separatingChaining](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/separatingChaining.png)](https://github.com/WeareSoft/tech-interview/blob/master/contents/images/separatingChaining.png)
        - Linked List 사용 시 충돌이 발생하면 충돌 발생한 인덱스가 가리키고 있는 Linked List에 노드 추가하여 Value 삽입
        - Key에 대한 Value 탐색 시에는 인덱스가 가리키고 있는 Linked List를 선형 검색하여 Value 반환 (삭제도 마찬가지)
        - Linked List 구조를 사용하기 때문에 추가 데이터 수 제약이 적은편
    2. Open addressing
        - 추가 메모리 공간을 사용하지 않고, HashTable 배열의 빈 공간을 사용하는 방법
        - Separating Chaining 방식에 비해 적은 메모리 사용
        - 방법은 Linear Probing, Quadratic Probing, Double Hashing
    3. Resizing
        - 저장 공간이 일정 수준 채워지면 Separating Chaining의 경우 성능 향을 위해, Open addressing의 경우 배열 크기 확장을 위해 Resizing
        - 보통 두배로 확장
        - 확장 임계점은 현재 데이터 개수가 Hash Bucket 개수의 75%가 될 때

- HashTable 장점

    - 적은 리소스로 많은 데이터를 효율적으로 관리 가능
        - ex. HDD. Cloud에 있는 많은 데이터를 Hash로 매핑하여 작은 크기의 시 메모리로 프로세스 관리 가능
    - 배열의 인덱스를 사용하기 때문에 빠른 검색, 삽입, 삭제 (O(1))
        - HashTable의 경우 인덱스는 데이터의 고유 위치이기 때문에 삽입 삭제 시 다른 데이터를 이동할 필요가 없어 삽입, 삭제도 빠른 속도 가능
    - Key와 Hash에 연관성이 없어 보안 유리
    - 데이터 캐싱에 많이 사용
        - get, put 기능에 캐시 로직 추가 시 자주 hit하는 데이터 바로 검색 가능
    - 중복 제거 유용

- HashTable 단점

    - 충돌 발생 가능성
    - 공간 복잡도 증가
    - 순서 무시
    - 해시 함수에 의존

- HashTable vs HashMap

    - Key-Value 구조 및 Key에 대한 Hash로 Value 관리하는 것은 동일
    - HashTable
        - 동기
        - Key-Value 값으로 null 미허용 (Key가 hashcode(), equals()를 사용하기 때문)
        - 보조 Hash Function과 separating Chaining을 사용해서 비교적 충돌 덜 발생 (Key의 Hash 변형)
    - HashMap
        - 비동기 (멀티 스레드 환경에서 주의)
        - Key-Value 값으로 null 허용

- HashTable 성능

    |      | 평균 | 최악 |
    | ---- | ---- | ---- |
    | 탐색 | O(1) | O(N) |
    | 삽입 | O(1) | O(N) |
    | 삭제 | O(1) | O(N) |



## Stack

- 스택(Stack)의 개념
    - 한 쪽 끝에서만 자료를 넣고 뺄 수 있는 LIFO(Last In First Out) 형식의 자료 구조
- 특징
    - 마지막에 넣은 데이터가 먼저 나오는 후입선출(LIFO) 구조로 저장하는 형식
    - 큐(Queue)와는 반대되는 개념
    - 데이터를 차곡차곡 쌓아올린 형태를 연상
    - 입구와 출구가 하나(Top)밖에 없어 데이터의 삽입(Push)와 삭제(Pop)가 한 방향에서만 이루어진다
    - 활용 예시
        - 웹브라우저 히스토리
        - 휴대폰 동작

- 스택(Stack)의 연산
    - 스택(Stack)는 LIFO(Last In First Out) 를 따른다. 즉, 가장 최근에 스택에 추가한 항목이 가장 먼저 제거될 항목이다.
        - pop(): 스택에서 가장 위에 있는 항목을 제거한다.
        - push(item): item 하나를 스택의 가장 윗 부분에 추가한다.
        - peek(): 스택의 가장 위에 있는 항목을 반환한다.
        - isEmpty(): 스택이 비어 있을 때에 true를 반환한다.
- 스택(Stack)의 사용 사례
    - 재귀 알고리즘을 사용하는 경우 스택이 유용하다.
        - 재귀 알고리즘
            - 재귀적으로 함수를 호출해야 하는 경우에 임시 데이터를 스택에 넣어준다.
            - 재귀함수를 빠져 나와 퇴각 검색(backtrack)을 할 때는 스택에 넣어 두었던 임시 데이터를 빼 줘야 한다.
            - 스택은 이런 일련의 행위를 직관적으로 가능하게 해 준다.
            - 또한 스택은 재귀 알고리즘을 반복적 형태(iterative)를 통해서 구현할 수 있게 해준다.
        - 웹 브라우저 방문기록 (뒤로가기)
        - 실행 취소 (undo)
        - 역순 문자열 만들기
        - 수식의 괄호 검사 (연산자 우선순위 표현을 위한 괄호 검사)
            - Ex) 올바른 괄호 문자열(VPS, Valid Parenthesis String) 판단하기
        - 후위 표기법 계산

## Queue

- 큐(Queue)의 개념
    - 컴퓨터의 기본적인 자료 구조의 한가지로, 먼저 집어 넣은 데이터가 먼저 나오는 FIFO(First In First Out)구조로 저장하는 형식
    - ![image-20220629151308525](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629151308525.png)
- 큐(Queue)의 연산
    - 큐(Queue)는 FIFO(First-In-First-Out) 를 따른다.
        - add(item): item을 리스트의 끝부분에 추가한다.
        - remove(): 리스트의 첫 번째 항목을 제거한다.
        - peek(): 큐에서 가장 위에 있는 항목을 반환한다.
        - isEmpty(): 큐가 비어 있을 때에 true를 반환한다.
- 큐(Queue)의 사용 사례
    - 데이터가 입력된 시간 순서대로 처리해야 할 필요가 있는 상황에 이용한다.
        - 너비 우선 탐색(BFS, Breadth-First Search) 구현
            - 처리해야 할 노드의 리스트를 저장하는 용도로 큐(Queue)를 사용한다.
            - 노드를 하나 처리할 때마다 해당 노드와 인접한 노드들을 큐에 다시 저장한다.
            - 노드를 접근한 순서대로 처리할 수 있다.
        - 캐시(Cache) 구현
        - 우선순위가 같은 작업 예약 (인쇄 대기열)
        - 선입선출이 필요한 대기열 (티켓 카운터)
        - 콜센터 고객 대기시간
        - 프린터의 출력 처리
        - 윈도우 시스템의 메시지 처리기
        - 프로세스 관리

## Graph

- 그래프(Graph)의 개념
    - 단순히 노드(N, node)와 그 노드를 연결하는 간선(E, edge)을 하나로 모아 놓은 자료 구조
        - 즉, 연결되어 있는 객체 간의 관계를 표현할 수 있는 자료 구조이다.
        - Ex) 지도, 지하철 노선도의 최단 경로, 전기 회로의 소자들, 도로(교차점과 일방 통행길), 선수 과목 등
        - 그래프는 여러 개의 고립된 부분 그래프(Isolated Subgraphs)로 구성될 수 있다.
- 그래프(Graph)의 특징
    - 그래프는 네트워크 모델 이다.
    - 2개 이상의 경로가 가능하다.
        - 즉, 노드들 사이에 무방향/방향에서 양방향 경로를 가질 수 있다.
    - self-loop 뿐 아니라 loop/circuit 모두 가능하다.
    - 루트 노드라는 개념이 없다.
    - 부모-자식 관계라는 개념이 없다.
    - 순회는 DFS나 BFS로 이루어진다.
    - 그래프는 순환(Cyclic) 혹은 비순환(Acyclic)이다.
    - 그래프는 크게 방향 그래프와 무방향 그래프가 있다.
    - 간선의 유무는 그래프에 따라 다르다.

## Tree

- 트리(Tree)의 개념

- ![img](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/Untitled.png)
  
    - 루트(root) : 가장 위쪽에 있는 노드, **트리별 하나**만 있다.
    
        - 루트와 부모는 다르다. 부모노드는 자식노드가 1개 이상 있는 경우에만 존재할 수 있다.
    
    - 서브트리 : 자식노드이면서 부모노드역할을 하는 노드가 있는 트리
    
    - 차수 : 노드가 갖고 있는 최대 자식노드 수
    
        - 위의 경우 차수는 2개이다
            - 10의 차수, 8의 차수, 9의 차수, 1의 차수
    
    - 리프(leaf) : 레벨별로 가장 마지막에 있는 노드, 단말노드(terminal node), 외부노드(external node)라고도 한다. **리프는 트리별로 여러 개**가 있을 수 있다.
    
    - 레벨 : 루트노드에서 **얼마나 멀리 떨어져 있는지 각각 나타낸다**. 루트노드의 레벨은 0이며, 아래로 내려갈때마다 1씩증가한다.
    
        (위의 경우 상단부터 순서대로 0, 1, 2, 3으로 구성된다.)
    
    - 높이 : 루트에서 가장 멀리 떨어진 리프노드까지의 거리이며, **리프 레벨의 최대값**을 높이라고 한다. (위의 경우 3)
    
    - sibling(형제) 노드 : 부모가 같은 두 개의 노드
    
    - 노드(node)들과 노드들을 연결하는 간선(edge)들로 구성되어 있다.
        - 트리에는 사이클(cycle)이 존재할 수 없다.
        - 노드들은 특정 순서로 나열될 수도 있고 그럴 수 없을 수도 있다.
        - 각 노드는 부모 노드로의 연결이 있을 수도 있고 없을 수도 있다.
        - 각 노드는 어떤 자료형으로도 표현 가능하다.
    - 비선형 자료구조로 계층적 관계를 표현한다. Ex) 디렉터리 구조, 조직도
    - 그래프의 한 종류
        - 사이클(cycle)이 없는 하나의 연결 그래프(Connected Graph)
        - 또는 DAG(Directed Acyclic Graph, 방향성이 있는 비순환 그래프)의 한 종류 이다.

```
class Node {
  public String name;
  public Node[] children;
}
```

- 트리(Tree)의 특징
    - 그래프의 한 종류이다. ‘최소 연결 트리’ 라고도 불린다.
    - 트리는 계층 모델 이다.
    - 트리는 DAG(Directed Acyclic Graphs, 방향성이 있는 비순환 그래프)의 한 종류이다.
        - loop나 circuit이 없다. 당연히 self-loop도 없다.
        - 즉, 사이클이 없다.
    - 노드가 N개인 트리는 항상 N-1개의 간선(edge)을 가진다.
        - 즉, 간선은 항상 (정점의 개수 - 1) 만큼을 가진다.
    - 루트에서 어떤 노드로 가는 경로는 유일하다.
        - 임의의 두 노드 간의 경로도 유일하다. 즉, 두 개의 정점 사이에 반드시 1개의 경로만을 가진다.
    - 한 개의 루트 노드만이 존재하며 모든 자식 노드는 한 개의 부모 노드만을 가진다.
        - 부모-자식 관계이므로 흐름은 top-bottom 아니면 bottom-top으로 이루어진다.
    - 순회는 Pre-order, In-order 아니면 Post-order로 이루어진다. 이 3가지 모두 DFS/BFS 안에 있다.
    - 트리는 이진 트리, 이진 탐색 트리, 균형 트리(AVL 트리, red-black 트리), 이진 힙(최대힙, 최소힙) 등이 있다.
    
    ### 이진트리(binary tree)
    
    - 이진트리는 아래와 같이 각 노드별로, 최대 2개의 서브노드를 갖을 수 있다.(left, right)
    - 이진트리는 여러 트리종류 중에서 가장 기본이 되면서 많이 활용되는 트리이다.
    - 이진트리는 두가지 조건으로 구성되어 있다.
        - **루트노드를 중심으로 두 개의 서브트리**로 나눠진다.
        - 나눠진 두 서브트리도 모두 두 개의 서브트리를 갖는다.
            - **서브트리의 노드가 반드시 값을 갖고 있을 필요는 없다.**
    
    ### 편향트리
    
    한쪽으로만 쏠린 이진트리
    
    ### 완전이진트리
    
    - 완전 이진 트리는 아래그림과 같고 다음의 조건을 지킨다.
    
        - 노드가 위에서 아래로 채워져있다.
    
        - 노드가 **왼쪽에서 오른쪽 순서대로** 채워져있다.
    
            ![img](https://s3.us-west-2.amazonaws.com/secure.notion-static.com/b8ce1d2c-cccd-4c63-b2e7-bbbc4d24f5c3/Untitled.png?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=AKIAT73L2G45EIPT3X45%2F20220629%2Fus-west-2%2Fs3%2Faws4_request&X-Amz-Date=20220629T053221Z&X-Amz-Expires=86400&X-Amz-Signature=06572358fb16e62b3613ec10eb731b4c41e838ce95f21a78f6d93c5f5a8952fb&X-Amz-SignedHeaders=host&response-content-disposition=filename %3D"Untitled.png"&x-id=GetObject)
    
    ### 포화이진트리
    
    <img src="https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629151751045.png" alt="image-20220629151751045" style="zoom:50%;" />
    
    ### **Binary Search Trees(BST) - 이진검색트리**
    
    - 이진탐색트리는 **노드를 정확하게 정렬해야하는** 특정 유형의 이진 트리다. 이진 검색 트리는 다음의 조건이 있다.
    
    - BST의 목적은 단순 이진트리보다 빠른 **노드탐색**이다. 때문에 insert node에서 중복을 처리해주는 것이 아닌, 아래 **'값 크기 조건'**에 맞도록 값을 넣어주는 경우가 이진탐색트리가 되는 것이다.
    
    - 만약 아래 **'값 크기 조건'**을 지키지 않고 값을 삽입하는 경우 **'이진탐색트리'**의 로직이 아닌 **'단순이진트리'**의 로직으로 '탐색'이 진행되므로 더 느린 탐색이 진행된다.
    
        - 값 크기 조건
    
            : 오른쪽 서브노드의 값(right child) > 루트(부모)노드의 값(root node) > 왼쪽 서브노드의 값(left child)
    
            - 중복값을 갖고 있는 노드가 없어야 한다.
            - 왼쪽 서브트리노드들의 값은 루트(부모)노드값보다 작아야 한다.
            - 오른쪽 서브트리노드들의 값은 루트(부모)노드값보다 커야 한다.
    
        - 위에 대한 규칙이 정해진 이유는 
    
            왼쪽부터 오른쪽으로 검색을 하는 구조
    
            이기 때문이다.
    
            - 왼쪽 -> 오른쪽 개념이 적용되는 이유 : 트리와 같은 자료구조는 기본이 되는 연결리스트를 참조해서 만들어진 개념이기 때문이다.
    
        - 특징
    
            - 위와 같은 규칙에 따라 구조가 단순함
            - base node/검색할 노드/자식노드존재여부에 따라 검색되는 노드의 순서가 달라진다.
            - 검색이 일반 이진트리보다 빠르기 때문에 노드를 삽입하기 쉽다.
    
    ![https://github.com/Maiven/data-science/blob/main/이진검색트리.png?raw=true](https://github.com/Maiven/data-science/blob/main/이진검색트리.png?raw=true)
    
    - 검색 성공 경우
        - 위의 그림처럼 6(루트)보다 작은 2(왼쪽 자식노드)를 검색한다.
        - 다음으로 2를 기준으로 5(오른쪽 자식노드)가 크므로 검색된다.
        - 5를 기준으로 4(왼쪽 자식노드)가 작으면서 검색도 완료된다.
    - 검색 실패 경우
        - 6(루트)보다 큰 7(오른쪽 자식노드)을 검색한다.
        - 7보다 큰 오른쪽 자식노드는 **존재하지 않기때문에** 검색에 실패한다.

## 그래프(Graph)와 트리(Tree)의 차이점

![img](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/graph-vs-tree.png)

## Binary Heap

https://gmlwjd9405.github.io/2018/05/10/data-structure-heap.html

## Red-Black Tree

- [01. Red-Black Tree 개요](https://github.com/namjunemy/TIL/blob/master/Algorithm/red_black_tree_01.md)
- [02. Red-Black Tree insert fix-up](https://github.com/namjunemy/TIL/blob/master/Algorithm/red_black_tree_02.md)
- [03. Red-Black Tree delete, fix-up](https://github.com/namjunemy/TIL/blob/master/Algorithm/red_black_tree_03.md)

## B+ Tree