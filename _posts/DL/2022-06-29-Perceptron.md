---
published: true
layout: single
title: "신경망 학습"
categories:
  - DL
tags:
  - [Percepron, 순전파, 역전파, 손실함수, 경사 하강법, 옵티마이저]

toc: true
toc_sticky: true




---

# Percepron

1. **퍼셉트론(Percepron)**이란 무엇일까요? 초기 형태의 인공 신경망으로 다수의 입력으로 하나의 결과를 내보내는 알고리즘이다 기계신호로 인간의 뉴런을 따라한 방식 X의 입력이 W의 가중치에 영향을 받아 결과를 만들어낸다

![image-20220629152154968](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629152154968.png)

1. **XOR 문제**는 무엇이며 어떤 문제가 있을까요? 단층 퍼셉트론으로는 XOR의 값을 구분 할 수 없다

    ![image-20220629152209443](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629152209443.png)

2. 그래서 퍼셉트론을 어떤 형태로 개선하게 되었을까요? 다층 퍼셉트론으로 십가능

    ![image-20220629152216461](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629152216461.png)



딥러닝 ⇒ 값을 기준으로 로스를 줄여 가중치를 찾는것

활성화함수 ⇒ 각 노드에서연산값이 임계점을 넘을때 다음 노드로 신호를 전달하는데 그 임계점의 역할을 해주는게 활성화 함수(step sigmoid relu)

은닉층 이 깊으면 모든 함수를 표현할 수 있다

모든 층마다 활성화 함수를 적용

![image-20220629152309669](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629152309669.png)

(1) Input Layer: A 

(2) Hidden Layer: B 

(3) Output Layer: D 

(4) Neuron(Node): C 

(5) Weight: F 

(6) Bias: E 

(7) Activation Function: G 

(8) Node Map: H 

(9) Iteration: I 

(10) Epoch: J



## 신경망 학습

![img](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/68747470733a2f2f692e696d6775722e636f6d2f646c47617265542e676966.gif)

1. 데이터가 입력되면 신경망 각 층에서 **가중치 및 활성화 함수 연산**을 반복적으로 수행합니다.
2. 1의 과정을 모든 층에서 반복한 후에 **출력층에서 계산된 값을 출력**합니다.
3. **손실 함수**를 사용하여 **예측값(Prediction)과 실제값(Target)의 차이**를 계산합니다.
4. **경사하강법과 역전파**를 통해서 **각 가중치를 갱신**합니다.
5. 학습 중지 기준을 만족할 때까지 **1-4의 과정을 반복**합니다.

1-4의 과정을 **Iteration(이터레이션)**이라고 하며 매 Iteration 마다 가중치가 갱신됩니다.Iteration 은 **순전파(1&2), 손실 계산(3), 역전파(4)**로 나눠볼 수 있는다

## 순전파

입력된 신호가 연산을 거쳐 출력층에 값을 내보내는 과정

## 손실 함수

신경망은 손실 함수의 값을 최소화 하는 방향으로 가중치를 갱신한다 그래서 그 손실을 계산해주는게 손실함수이며

순전파를 통해 나온 출력값과 타겟을 손실 함수에 넣어 손실(loss , error)을 계산한다

## 역전파

순전파의 반대 방향으로 진행하면서 각 가중치들을 얼마나 업데이트 해야 할지를 구하는 과정

- 가중치는 어떻게 갱신될까?

    이 과정에서 역전파의 주요 메커니즘인 **편미분**과 **Chain rule(연쇄 법칙)**이 사용됩니다.위 식에서 볼 수 있었던 것처럼 특정 가중치 (θi) 에 대한 기울기는 아래 식과 같이 손실 함수를 해당 가중치로 **편미분**하여 구할 수 있습니다.  
    
    
    $$
    $\frac{\partial}{\partial \theta_i} J(\theta)$
    $$
    
    
    그렇다면 모든 가중치에 대한 값은 어떻게 구할 수 있을까요?여기서 바로 **Chain rule**이 적용됩니다.연쇄 법칙이란 아래 식과 같이 특정 변수에 대한 (편)미분 값을 다른 변수의 미분을 사용하여 나타낼 수 있는 방식입니다.    
    
    
    $$
    $\frac{\partial J(\theta)}{\partial \theta_i} = \frac{\partial J(\theta)}{\partial \theta_x} \cdot \frac{\partial \theta_x}{\partial \theta_i} = \frac{\partial J(\theta)}{\partial \theta_x} \cdot \frac{\partial \theta_x}{\partial \theta_y} \cdot \frac{\partial \theta_y}{\partial \theta_i}$
    $$
    
    
    연쇄 법칙을 사용하여 각 변수가 얼마나 수정되어야 할 지에 대한 정보를 전달할 수 있게 됩니다.

## 경사 하강법

경사 하강법을 사용하면 경사를 줄이는 방향 = 손실 함수의 값을 줄이는 방향

![image-20220629152639387](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629152639387.png)

![img](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/68747470733a2f2f692e696d6775722e636f6d2f6f7374415033772e676966.gif)

### 옵티마이저

경사를 내려가는 방법

![image-20220629152658906](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629152658906.png)

일반적인 경사하강법은 모든 데이터를 계산하기떄문에 확실하면 너무 오랜시간이 걸린다

### 확률적 경사하강법

그래서 등장한 것이 바로 **확률적 경사 하강법**과 **미니 배치(Mini-batch) 경사 하강법** 입니다 확률적 경사하강법은 전체 데이터중 하나의 데이터를 보고 신경망에 입력한 후 손실을 계산하고 그정도로 가중치를 업데이트합니다(iteration 마다 1개의 데이터만 사용) 가중치를빠르게 업데이트 할 수 있는 장점이있다 하지만 1개의 데이터만 보기때문에 아주 불안정하다

![image-20220629152711102](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629152711102.png)

두 방법을 적절히 융화한 것이 **미니 배치(Mini-batch) 경사 하강법**

N개의 데이터로 미니 배치를 구성하여 해당 미니 배치를 신경망에 입력한 후 이 결과를 바탕으로 가중치를 업데이트합니다.

즉, Iteration 마다 N개(=배치 사이즈)의 데이터를 사용하게 됩니다

![image-20220629152720884](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629152720884.png)

![image-20220629152731054](https://raw.githubusercontent.com/Cloudblack/Forpicture/image/img/image-20220629152731054.png)

#### of Data, Epoch, 배치 사이즈, iteration의 관계

데이터셋 전체를 몇 번이나 반복하여 학습할 지를 결정하는 Epochs(에포크)

순전파-역전파 1회, 즉 가중치를 한 번 수정하는 단위를 Iteration

of Data = Batch_size×Iteration