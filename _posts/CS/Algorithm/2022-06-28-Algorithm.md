---
published: true
layout: single
title: "Algorithm"
categories: [Algorithm]
tags:
  - [Algorithm, Recursion, Divide and Conquer, BigO, linear search,binary search, 버블, 삽입, 선택, 병합, 퀵, 재귀, 분할, DFS, BFS, Greedy]
toc: true
toc_sticky: true
date created: 수요일, 6월 29일 2022
date modified: 목요일, 9월 1일 2022
---

# 알고리즘

## 알고리즘?
- 문제를 해결하기 위한 절차나 방법 (굳이 코딩이아니라 진짜 절차나 방법)
- 알고리즘을 컴퓨터가 이해할 수 있는 형태로 바꿔주는 것이 코딩/프로그래밍
- 구체적으로 순서를 표현하자
- 알고리즘을 공부해야 하는 이유?
    - 좋은 프로그램을 만들기 위해
    - 프로그램의 좋고 나쁨을 판단하기 위해서
    - 프로그램 작성 과정 전체를 효율화하기 위해서
    - 프로그래밍 기술을 향상 시키기 위해

### 알고리즘 설계 기법
- 새로운 문제를 접했을때 문제를 해결 할 수 있는 방법을 설계하는 기법

## Search Algorithm Basic(검색 알고리즘 기본)
- 원하는 데이터를 찾아내는 알고리즘

### Linear search(선형검색)
- 맨 앞이나, 맨 뒤부터 순차적으로 하나하나 찾아보는 알고리즘
- 가장 단순한 알고리즘
- 최선 O(1) , 최악 O(n) , 평균 O(n)

### Binary search(이진 검색)
- 중간지점을 기준으로 데이터를 반씩 나눠서 검색 하는 알고리즘

    1. 중간 지점을 선택, 중간 지점 값과 타겟값을 비교

    2-1. 중간값 >원하는 값 ⇒ 왼쪽 배열/리스트 확인

    2-2. 중간값 < 원하는 값 ⇒ 오른쪽 배열/리스트 확인

    1. 새로운 중간값을 선정 비교

- 필수로 정렬되어 있어야 한다

- 최선 O(1), 최악 O(n),평균 O(logN) (횟수가 반절날때)

## 정렬 알고리즘의 종류와 개념
- 데이터가 들어왔을떄 이를 사용자가 지정한 기준에 맞게 데이터를 나열해서 출력하는 알고리즘이다
- 필요성⇒빨리 찾기위함
    - 동일한 데이터 셋?
    - 겹치는 데이터?
    - 편리한 바이너리 탐색

주어진 데이터셋에 따라

Worst case : O(n2)

Best case : O(n log n)

Average Case : O(n log n)

### 버블소트
[버블소트 거품정렬 5분만에 이해하기 - Gunny](https://www.youtube.com/watch?v=RCnyz-Bfkmc)

- 제일 처음 접하는 정렬 알고리즘
- 두 숫자를 비교, 큰 숫자를 오른쪽으로 스왑하며 정렬
- 마치 거품이 올라오는 모습같아 버블소트
- 정리
    - 두 숫자를 비교 후 큰 숫자를 오른쪽으로 이동
    - Outer 루프가 한번 돌때마다 element하나의 최종위치가 확정
    - 탐색범위
        - outer : 0→ n-1
            - 마지막 element는 이미 비교되어있다
        - inner : 0→ n-i-1
            - 이미 정렬 되어있는 부분 제외
    - 최선 O(n) ⇒정렬, 최악 O(n^2)⇒역정렬 , 평균 O(n^2)

[버블 정렬(Bubble Sort)](https://gmlwjd9405.github.io/2018/05/06/algorithm-bubble-sort.html)

### 삽입정렬
- 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열 부분과 비교해서 자신의 위치를 찾아 삽입한다.
- 단순 삽입, 데이터를 올바른 위치에서 삽입하면서 자리를 바꿔준다
    - 맨 왼쪽의 2번쨰 요소 기준으로 선택
    - 기존 앞의 요소와 비교 후 교환
    - 기준 오른쪽으로 이동
    - 반복
- 최선 O(n) ⇒이미 정렬되어있는 경우 , 최악 O(n^2), 평균 O(n^2)
- [삽입 정렬(insertion sort)](https://gmlwjd9405.github.io/2018/05/06/algorithm-insertion-sort.html)

### 선택정렬
- 가장 작은 노드(최소값) 선택
- 왼쪽부터 정렬하기 위해 알맞은 위치와 교환하는 작업을 반복
- 최선 O(n^2), 최악 O(n^2), 평균 O(n^2) ⇒ 무조건 다 비교하기 때문에
- [선택 정렬(selection sort)](https://gmlwjd9405.github.io/2018/05/06/algorithm-selection-sort.html)

#### 공통 특징
- 3개의 알고리즘은 모두 제자리 정렬(in place sorting)
    - 정렬하고자 하는 배열 안에서 교환하는 방식⇒ 다른 메모리공간을 필요로 하지 않음
- 작은 데이터/데이터베이스 기준으로는 모두 사용하기 좋은 알고리즘
    - 구현하기 쉽고 단순
    - 데이터가 커지면 커질수록 느려짐⇒ 다른알고리즘 추천
- 안정 정렬과 불안정 정렬
    - 불안정 : 같은 값에서 교환이 일어난다
    - 안정 : 같은 값에서 교환이 일어나지 않는다

### 병합 정렬(Merge Sort) 알고리즘
- 분할정복에 가장 충실한 알고리즘
- 배열/리스트를 최대한 작게 나눠주고 다시 하나씩 합치면서 정렬을 하는 방법
- 병합정렬 과정

```python
1. 정렬한 데이터 집합을 반으로 나눈다.
2. 나눈어진 하위 데이터 집합의 크기가 2이상이면 이 하위 데이터 집합에 대해 1을 반복한다.
3. 원래 같은 집합에서 나뉘어져 나온 하위 데이터 집합 둘을 병합하여 하나의 데이터 집합으로 만든다.
   단, 병합할때 데이터 집합의 원소는 순서에 맞춰서 정렬한다.
4. 데이터 집합이 다시 하나가 될 때까지 3을 반복한다.
```

- [병합 정렬(merge sort)](https://gmlwjd9405.github.io/2018/05/08/algorithm-merge-sort.html)

### 퀵 정렬 알고리즘
- 정렬을 할 배열/리스트에서 기준이 되는 수(피벗,pivot) 정해주고, 이 피벗을 기준으로 왼쪽은 피벗보다 작은 수, 오른쪽은 피벗보다 큰 수로 배치를 작업하는 반복하는 정렬

- 퀵정렬 과정

    
    ```python
    1. 기준이 되는 피벗을 선택한다
        - 피벗은 가장 많이 사용되는 것은 맨 왼쪽값(리스트 0번째 인덱스, 정답은 ㅇ벗다)
    2. 피벗을 기준으로 해서 피벗보다 작은 애들은 왼쪽으로 큰 애들은 오른쪽으로 보낸다.
    
     3.  left와 right가 교차할 때까지 이 과정을 반복하다 교차하면 right와 피벗을 서로 교환한다.
    
    [피벗보다 작은애들] - [피벗] - [피벗보다 큰애들]
    
    1. 피벗보다 작은 애들과 피벗보다 큰 애들을 각각 동일하게 위의 과정(퀵 정렬)을 수행한다(재귀적으로)
    ```
    

- 최선 O(NlogN) 고르게 반반 쪼개진경우, 최악 O(N^2) 불균형하게 쪼 개진경우

    - 퀵정렬은 최악의 경우 첫번째 노드를 피벗으로 설정하고 불균형하게 분할정복을 시도하여 성능이 안좋아진다
        - 속도는 알고리즘을 처리하고 결과를 도출하는 속도(주로 소프트웨어에 영향을 주고받음)
        - 성능은 메모리에 영향을 주는 정도(주로 하드웨어에 영향을 주고받음)

피벗 종류 ⇒ 맨 왼쪽, 맨 오른쪽, 가운데, 랜덤,답은없다

​		[퀵 정렬(quick sort)](https://gmlwjd9405.github.io/2018/05/10/algorithm-quick-sort.html)

#### 	퀵 정렬 vs 병합 정렬
- 시간 복잡도
    - O(NlogN)
    - 퀵
        - 최선:O(NlogN)
        - 최악:O(N^2)⇒ 분할했을 때 불균형하게 되는 경우 ( 피벗값이 계속해서 제일 끝 값이 경우)
        - 평균:O(NlogN)
    - 병합
        - 최선 O(NlogN)
        - 최악 O(NlogN)
        - 평균 O(NlogN)

stable sort

- [힙 정렬(heap sort)](https://gmlwjd9405.github.io/2018/05/10/algorithm-heap-sort.html)

- [셸 정렬(shell sort)](https://gmlwjd9405.github.io/2018/05/08/algorithm-shell-sort.html)

    #### 안정정렬 vs 불안정 정렬

    - 안정 : 중복(동일)한 값이 있을때 상대적인 위치가 변하지 않는다 [1, 2, 3, 3, 4, 5] 3끼리 자리가 바뀌지않음
        - 버블 , 삽입,병합
    - 불안정 : 중복(동일)한 값이 있으 때 상대적인 위치가 변한다. [1, 2, 3, 3, 4, 5] 3끼리 자리가 바뀜
        - 선택,퀵

- 정렬 알고리즘의 애니메이션 보기

    - -> <https://www.toptal.com/developers/sorting-algorithms>

## Recursion : 재귀 알고리즘
스스로를 포함하는 함수로 반복문+스택으로 구성되어있다 (시작은 첫번째부터지만 return은 마지막) 무한 반복이 되기때문에 중지해줄 base case가 필요하며 반드시 스스로를 호출해야한다

#### 재귀 (재귀 = 반복문+스택(LIFO))
- 자기자신 함수를 다시 호출하는 것
- 함수가 자기 자신을 다시 호출하여 작업을 반복적으로 수행하는 것
- 함수 호출은 스택의 원리를 따르고 마지막에 호출된 함수가 먼저 종료된다.
- 재귀를 그냥 사용하면 재귀 에러발생(RecursionError 재귀에는 한계가 있다)
- 재귀의 특성을 잘 알고 사용할 것
- 재귀의 내부 코드를 되도록 간단하고 명료하게 작성하자

#### 재귀의 조건
1. base cace(기본 케이스,기저사례,종료조건)이 있어야한다
    - 재귀 에러를 방지하기 위해
2. 추가 조건과 기본조건의 차이를 확인한다
    - 기본 케이스와 만날수있게(중지할수있게)
3. 반드시 자기 자신을 호출해야한다

반복문⇒ 재귀 안되는 경우가있고 빡세다

## Divide and Conquer : 분할 정복
- 알고리즘 설계 기법, 알고리즘 디자인 패러다임
- 복잡한 문제를 작은 단위로 문제를 즉각 해결 할 수 있을때 까지 **재귀적**으로 **나누고(Divide)** 이를 **해결한(Conquer)** 다음 그 결과를 이용해서 다시 전체 문제(복잡한 문제)를 해결하며 **합치는(Combine =Merge)** 방법

#### 분할 정복 설계 단계:
1. 분할: 원래를 분할하여 **비슷한 크기/ 유형**의 작은 문제로 나눈다
2. 정복: 하위 문제를(해결 할 수 있을 정도로 작게) 각각 **재귀적으로** 해결 ⇒ Base Case설정이 필요하다
3. 합치기: 필요하면, 하위 문제들의 답을 합쳐서 원래

#### 재귀 vs 분할 정복
- 공통점 : 복잡한 큰 문제를 작은 단위로 나눠서 해결하려고 한다.
- 차이점
    - 분할정복 : 비슷한 작업을 재진행(같은 함수가 아닐수있다), 동일한 비율로 나눔
    - 재귀호출 : 같은 함수를 재호출(같은 함수 사용) ,1과 나머지로 나눔

## Dynamic Programming / Memoization : 동적 프로그래밍
- Dynamic Programming (=동적 계획법)

    - 하나의 문제를 여러 작은 문제의 답을 재사용 하여 문제를 효율적으로 푸는 것
    - 작은 문제의 답을 구해서, 큰 문제를 해결한다.(분할 정복과 유사)
        - 중복되는 작은 문제들의 답을 재사용/재활용(분할정복과의 차이점)
        - 이미 했던 계산은 반복하지 않는다⇒ 불필요한 계산 줄이기
            - 메모이제이션(Memoization)또는 타뷸레이션(Tabulation)을 통해서 필요한 계산수를 많이 줄일 수 있다.
            - 메모리 공간을 약간 더 사용해서 연산 속도를 비약적으로 증가시키자
            - 재귀+조건 ⇒ 분할정복 + 조건⇒ DP + 조건⇒또다른 방법론

- DP 구현 방법

    - 메모이제이션(하향식)
        - 하향식 방법
        - 재귀를 이용하여 값을 위에서 부터 계산
        - 메모 혹은 캐시에 값을 저장하고 재사용⇒ 캐싱
        - 다이나믹 프로그래밍에 국한된 개념은 아님
        - 메인문제를 분할하면서 해결하는 법
        - 이미 conquer했던 계산을 저장(메모이제이션)했다가 재사용해여 전체적인 속도를 향상
        - (메모이제이션을 이용한다 했을 때)⇒재귀사용⇒ 종료조건(Base case)를 만들어 줘야한다
    - 태뷸레이션(상향식)
        - 상향식 방법
        - 반목문을 이용하여 밑에서 부터 값을 계산
        - 값을 미리 계산해두고 필요하지 않은 값도 미리 계산
            - 반복문을 통해 부분 문제에 대한 해답을 하나씩 저장해나가는 방식
        - dp테이블에 값을 저장
        - 다이나믹 프로그래밍에 전형적인 형태
        - 가장 작은 문제를 문저 해결하고 최정적으로 메인문제를 해결하는 법

- DP문제 풀기위해 생각해 볼점

    DP적용 조건⇒ dp로 풀수있는 문제인가?

    - 문제를 작은 문제로 나눌 수 있어야한다 .
    - 하위문제들의 결과값을 통해서 상위 문제의 결과값을 구할 수 있어야 한다(최적 부분 구조=Optimal substructure)
    - 하위 문제들이 중복되어야 한다(중복되는 부분 문제=Overlapping Subproblems)

## BigO
- BigO의 개념
- BigO의 복잡성 차트 보기
    - [![img](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/BigO-complexity-chart.png)](https://github.com/WeareSoft/tech-interview/blob/master/contents/images/BigO-complexity-chart.png)
    - -> <http://bigocheatsheet.com/>

## DFS와 BFS의 차이
![bfs-vs-dfs.gif](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/bfs-vs-dfs.gif)

- 깊이 우선 탐색(DFS, Depth-First Search)

    - DFS의 개념: 루트 노드(혹은 다른 임의의 노드)에서 시작해서 다음 분기(branch)로 넘어가기 전에 해당 분기를 완벽하게 탐색하는 방법

        - 미로를 탐색할 때 한 방향으로 갈 수 있을 때까지 계속 가다가 더 이상 갈 수 없게 되면 다시 가장 가까운 갈림길로 돌아와서 이곳으로부터 다른 방향으로 다시 탐색을 진행하는 방법과 유사하다.
        - 즉, 넓게(wide) 탐색하기 전에 깊게(deep) 탐색하는 것이다.
        - 사용하는 경우: **모든 노드를 방문** 하고자 하는 경우에 이 방법을 선택한다.
        - 깊이 우선 탐색(DFS)이 너비 우선 탐색(BFS)보다 좀 더 간단하다.
        - 단순 검색 속도 자체는 너비 우선 탐색(BFS)에 비해서 느리다.

    - DFS의 특징

        - 자기 자신을 호출하는 **순환 알고리즘의 형태** 를 가지고 있다.

        - 전위 순회(Pre-Order Traversals)를 포함한 다른 형태의 트리 순회는 모두 DFS의 한 종류이다.

        - 이 알고리즘을 구현할 때 가장 큰 차이점은, 그래프 탐색의 경우

             

            어떤 노드를 방문했었는지 여부를 반드시 검사

             

            해야 한다는 것이다.

            - 이를 검사하지 않을 경우 무한루프에 빠질 위험이 있다.

    - DFS의 과정

        - [![img](https://github.com/WeareSoft/tech-interview/raw/master/contents/images/dfs-example.png)](https://github.com/WeareSoft/tech-interview/blob/master/contents/images/dfs-example.png)

    - DFS의 구현 방법 2가지

        - **1. 순환 호출 이용**
        - \2. 명시적인 스택 사용
            - 명시적인 스택을 사용하여 방문한 정점들을 스택에 저장하였다가 다시 꺼내어 작업한다.
        - 순환 호출을 이용한 DFS 의사코드(pseudocode)

```
void search(Node root) {
  if (root == null) return;

  // 1. root 노드 방문
  visit(root);
  root.visited = true; // 1-1. 방문한 노드를 표시

  // 2. root 노드와 인접한 정점을 모두 방문
  for each (Node n in root.adjacent) {
    if (n.visited == false) { // 4. 방문하지 않은 정점을 찾는다.
      search(n); // 3. root 노드와 인접한 정점 정점을 시작 정점으로 DFS를 시작
    }
  }
}
```

- 너비 우선 탐색(BFS, Breadth-First Search)

    - BFS의 개념: 루트 노드(혹은 다른 임의의 노드)에서 시작해서 인접한 노드를 먼저 탐색하는 방법

        - 시작 정점으로부터 가까운 정점을 먼저 방문하고 멀리 떨어져 있는 정점을 나중에 방문하는 순회 방법이다.

        - 즉, 깊게(deep) 탐색하기 전에 넓게(wide) 탐색하는 것이다.

        - 사용하는 경우:

             

            두 노드 사이의 최단 경로

             

            혹은

             

            임의의 경로를 찾고 싶을 때

             

            이 방법을 선택한다.

            - Ex) 지구상에 존재하는 모든 친구 관계를 그래프로 표현한 후 Ash와 Vanessa 사이에 존재하는 경로를 찾는 경우
            - 깊이 우선 탐색의 경우 - 모든 친구 관계를 다 살펴봐야 할지도 모른다.
            - 너비 우선 탐색의 경우 - Ash와 가까운 관계부터 탐색

        - 너비 우선 탐색(BFS)이 깊이 우선 탐색(DFS)보다 좀 더 복잡하다.

    - BFS의 특징

        - 직관적이지 않은 면이 있다.

            - BFS는 시작 노드에서 시작해서 거리에 따라 단계별로 탐색한다고 볼 수 있다.

        - BFS는 **재귀적으로 동작하지 않는다.**

        - 이 알고리즘을 구현할 때 가장 큰 차이점은, 그래프 탐색의 경우

             

            어떤 노드를 방문했었는지 여부를 반드시 검사

             

            해야 한다는 것이다.

            - 이를 검사하지 않을 경우 무한루프에 빠질 위험이 있다.

        - BFS는 방문한 노드들을 차례로 저장한 후 꺼낼 수 있는 자료 구조인

             

            큐(Queue)를 사용한다.

            - 즉, **선입선출(FIFO)** 원칙으로 탐색
            - 일반적으로 큐를 이용해서 반복적 형태로 구현하는 것이 가장 잘 동작한다.

        - 'Prim', 'Dijkstra' 알고리즘과 유사하다.

    - BFS의 과정

        - 깊이가 1인 모든 노드를 방문하고 나서 그 다음에는 깊이가 2인 모든 노드를, 그 다음에는 깊이가 3인 모든 노드를 방문하는 식으로 계속 방문하다가 더 이상 방문할 곳이 없으면 탐색을 마친다.
        - [![img](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/bfs-example.png)](https://github.com/WeareSoft/tech-interview/blob/master/contents/images/bfs-example.png)

    - BFS의 구현 방법

        - 자료 구조 **큐(Queue)를 이용**
        - 큐(Queue)를 이용한 BFS 의사코드(pseudocode)

```
void search(Node root) {
  Queue queue = new Queue();
  root.marked = true; // (방문한 노드 체크)
  queue.enqueue(root); // 1-1. 큐의 끝에 추가

  // 3. 큐가 소진될 때까지 계속한다.
  while (!queue.isEmpty()) {
    Node r = queue.dequeue(); // 큐의 앞에서 노드 추출
    visit(r); // 2-1. 큐에서 추출한 노드 방문
    // 2-2. 큐에서 꺼낸 노드와 인접한 노드들을 모두 차례로 방문한다.
    foreach (Node n in r.adjacent) {
      if (n.marked == false) {
        n.marked = true; // (방문한 노드 체크)
        queue.enqueue(n); // 2-3. 큐의 끝에 추가
      }
    }
  }
}
```

- -

## Greedy 알고리즘
- 탐욕법
- 문제 해결 과정에서 순간순간마다 최적이라고 판단한 방식으로 진행하여 답에 도달
- 문제의 성질이 동일하게 보존되고, 같은 전략을 반복적으로 사용 가능할 때 적용
    - 앞의 선택이 이후의 선택의 영향을 주지 않는 조건
    - 문제 최종 해결 방법이 부분 문제에 대한 해결 방법과 동일한 조건
    - 시간이나 공간적 제약으로 인해 다른 방법으로 최적해를 찾기 너무 어렵다면 최적해를 적당히 괜찮은 답(근사해)을 찾는 것으로 타협
- 장점
    - 다른 최적해 계산 알고리즘에 비해 적은 비용 (빠른 속도)
    - 완벽한 베스트는 구하지 못하더라도 최악의 결과는 아닐거다
- 단점
    - 당장 그 순간의 최적 값을 찾기 때문에 항상 최적 해를 찾는 것은 불가능
    - 전체에서 최적값(가장 좋은 결과)는 항상 보장되지 않는다.
- 문제 접근 방법(각자의 기준이 필요하다)
    - 가장 먼저 구현 완전 탐색(Brute Force)등의 아이디어로 문제 해결 가능한지 검토
    - 완전 탐색을 이용하면 시간 복잡도가 생길 것 같다면⇒ 그리디 방법 생각
    - 다른 풀이 방법이 떠오르지 않는다면 다이나믹 프로그래밍, 다른 그래프 알고리즘 방법을 고려
    - 다이나믹 프로그래밍⇒ 재귀(하향식) 먼저 적용⇒ 코드 개선(DP 테이블 적용)
- 대표적인 그리디 알고리즘 문제
    - 주어진 각 동전을 가장 적게 사용해 N원을 만드는 문제
        - 일반적으로 동전은 보다 작은 금액 동전의 배수이기 때문에 작은 금액 동전을 무조건 큰 금액 동전으로 교체하는 것이 이득
        - 60원 동전이 생긴다면? 규칙이 깨지기 때문에 그리디 알고리즘 더이상 사용 불가
    - 도시락 문제
        - N개의 도시락을 단 한 대의 전자렌지에서 한 번에 하나만 데우기 가능하며, 각 도시락은 조리 시간과 먹는 시간이 다르게 정해져 있을 때 모든 도시락을 먹는데 걸리는 최소 시간
        - 먹는데 시간이 오래 걸리는 도시락부터 순서대로 데우면 가능
    - 이 외 첫번째 Reference 링크에서 추천 문제 참고

> - [탐욕적 기법(Greedy Algorithm) (수정: 2019-11-23)](https://blog.naver.com/kks227/220775134486)
> - [동적 계획법(Dynamic Programming)과 탐욕법(Greedy Algorithm)](https://velog.io/@cyranocoding/동적-계획법Dynamic-Programming과-탐욕법Greedy-Algorithm-3yjyoohia5)

## MST란
- Spanning Tree란

    - 그래프 내의 모든 정점을 포함하는 트리, **Spanning Tree = 신장 트리 = 스패닝 트리**

    - Spanning Tree는 그래프의

         

        최소 연결 부분 그래프

         

        이다.

        - 최소 연결 = 간선의 수가 가장 적다.
        - n개의 정점을 가지는 그래프의 최소 간선의 수는 (n-1)개이고, (n-1)개의 간선으로 연결되어 있으면 필연적으로 트리 형태가 되고 이것이 바로 Spanning Tree가 된다.

    - 즉, 그래프에서 일부 간선을 선택해서 만든 트리

- Spanning Tree의 사용 사례

    - 통신 네트워크 구축
        - 예를 들어, 회사 내의 모든 전화기를 가장 적은 수의 케이블을 사용하여 연결하고자 하는 경우
        - n개의 위치를 연결하는 통신 네트워크를 최소의 링크(간선)를 이용하여 구축하고자 하는 경우, 최소 링크의 수는 (n-1)개가 되고, 따라서 Spanning Tree가 가능해진다.

- MST(Minimum Spanning Tree, 최소 신장 트리)란

    - Spanning Tree 중에서 사용된 간선들의 가중치 합이 최소인 트리,

         

        MST = Minimum Spanning Tree = 최소 신장 트리

        - 각 간선의 가중치가 동일하지 않을 때 단순히 가장 적은 간선을 사용한다고 해서 최소 비용이 얻어지는 것은 아니다.
        - MST는 간선에 가중치를 고려하여 최소 비용의 Spanning Tree를 선택하는 것을 말한다.
        - 즉, 네트워크(가중치를 간선에 할당한 그래프)에 있는 모든 정점들을 가장 적은 수의 간선과 비용으로 연결하는 것이다.

- MST의 특징

    1. 간선의 가중치의 합이 최소여야 한다.
    2. n개의 정점을 가지는 그래프에 대해 반드시 (n-1)개의 간선만을 사용해야 한다.
    3. 사이클이 포함되어서는 안된다.

- MST의 사용 사례

    - 통신망, 도로망, 유통망에서 길이, 구축 비용, 전송 시간 등을 최소로 구축하려는 경우
        - 도로 건설: 도시들을 모두 연결하면서 도로의 길이가 최소가 되도록 하는 문제
        - 전기 회로: 단자들을 모두 연결하면서 전선의 길이가 가장 최소가 되도록 하는 문제
        - 통신: 전화선의 길이가 최소가 되도록 전화 케이블 망을 구성하는 문제
        - 배관: 파이프를 모두 연결하면서 파이프의 총 길이가 최소가 되도록 연결하는 문제

> - <https://gmlwjd9405.github.io/2018/08/28/algorithm-mst.html>

## Kruskal MST 알고리즘
- Kruskal MST 알고리즘이란

    - 탐욕적인 방법(greedy method)

         

        을 이용하여 네트워크(가중치를 간선에 할당한 그래프)의 모든 정점을 최소 비용으로 연결하는 최적 해답을 구하는 것

        - MST(최소 비용 신장 트리) 가 *1) 최소 비용의 간선으로 구성됨 2) 사이클을 포함하지 않음* 의 조건에 근거하여 **각 단계에서 사이클을 이루지 않는 최소 비용 간선을 선택** 한다.
        - 간선 선택을 기반으로 하는 알고리즘이다.
        - 이전 단계에서 만들어진 신장 트리와는 상관없이 무조건 최소 간선만을 선택하는 방법이다.

- 과정

    1. 그래프의 간선들을 가중치의 오름차순으로 정렬한다.
    2. 정렬된 간선 리스트에서 순서대로 사이클을 형성하지 않는 간선을 선택한다.
        - 즉, 가장 낮은 가중치를 먼저 선택한다.
        - 사이클을 형성하는 간선을 제외한다.
    3. 해당 간선을 현재의 MST(최소 비용 신장 트리)의 집합에 추가한다.

> - <https://gmlwjd9405.github.io/2018/08/29/algorithm-kruskal-mst.html>

## Prim MST 알고리즘
- Prim MST 알고리즘이란

    - 시작 정점에서부터 출발하여 신장트리 집합을

         

        단계적으로 확장

         

        해나가는 방법

        - 정점 선택을 기반으로 하는 알고리즘이다.
        - 이전 단계에서 만들어진 신장 트리를 확장하는 방법이다.

- 과정

    1. 시작 단계에서는 시작 정점만이 MST(최소 비용 신장 트리) 집합에 포함된다.
    2. 앞 단계에서 만들어진 MST 집합에 인접한 정점들 중에서 최소 간선으로 연결된 정점을 선택하여 트리를 확장한다.
        - 즉, 가장 낮은 가중치를 먼저 선택한다.
    3. 위의 과정을 트리가 (N-1)개의 간선을 가질 때까지 반복한다.

> - <https://gmlwjd9405.github.io/2018/08/30/algorithm-prim-mst.html>

## Reference
> - <https://github.com/tayllan/awesome-algorithms>
> - <https://www.cs.usfca.edu/~galles/visualization/Algorithms.html>
