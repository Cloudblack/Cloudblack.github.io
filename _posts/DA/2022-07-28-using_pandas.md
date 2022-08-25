---
published: true
layout: single
title: "PANDAS로 데이터를 처리해보고 시각화해보자"
categories:
  - TIL
  - DA
tags:
  - [TIL,PANDAS,시각화]

toc: true
toc_sticky: true

---


<head>
  <style>
    table.dataframe {
      white-space: normal;
      width: 100%;
      height: 240px;
      display: block;
      overflow: auto;
      font-family: Arial, sans-serif;
      font-size: 0.9rem;
      line-height: 20px;
      text-align: center;
      border: 0px !important;
    }

    table.dataframe th {
      text-align: center;
      font-weight: bold;
      padding: 8px;
    }

    table.dataframe td {
      text-align: center;
      padding: 8px;
    }

    table.dataframe tr:hover {
      background: #b8d1f3; 
    }

    .output_prompt {
      overflow: auto;
      font-size: 0.9rem;
      line-height: 1.45;
      border-radius: 0.3rem;
      -webkit-overflow-scrolling: touch;
      padding: 0.8rem;
      margin-top: 0;
      margin-bottom: 15px;
      font: 1rem Consolas, "Liberation Mono", Menlo, Courier, monospace;
      color: $code-text-color;
      border: solid 1px $border-color;
      border-radius: 0.3rem;
      word-break: normal;
      white-space: pre;
    }

  .dataframe tbody tr th:only-of-type {
      vertical-align: middle;
  }

  .dataframe tbody tr th {
      vertical-align: top;
  }

  .dataframe thead th {
      text-align: center !important;
      padding: 8px;
  }

  .page__content p {
      margin: 0 0 0px !important;
  }

  .page__content p > strong {
    font-size: 0.8rem !important;
  }

  </style>
</head>


# Pandas를 활용한 데이터 처리



```python
data = {
    '이름' : ['채치수', '정대만', '송태섭', '서태웅', '강백호', '변덕규', '황태산', '윤대협'],
    '학교' : ['북산고', '북산고', '북산고', '북산고', '북산고', '능남고', '능남고', '능남고'],
    '키' : [197, 184, 168, 187, 188, 202, 188, 190],
    '국어' : [90, 40, 80, 40, 15, 80, 55, 100],
    '영어' : [85, 35, 75, 60, 20, 100, 65, 85],
    '수학' : [100, 50, 70, 70, 10, 95, 45, 90],
    '과학' : [95, 55, 80, 75, 35, 85, 40, 95],
    '사회' : [85, 25, 75, 80, 10, 80, 35, 95],
    'SW특기' : ['Python', 'Java', 'Javascript', '', '', 'C', 'PYTHON', 'C#']
}
```


```python
import pandas as pd
```


```python
df = pd.DataFrame(data)
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td></td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td></td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


## 데이터 접근



```python
df['키']
```

<pre>
0    197
1    184
2    168
3    187
4    188
5    202
6    188
7    190
Name: 키, dtype: int64
</pre>

```python
df[['키','이름']]
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>키</th>
      <th>이름</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>197</td>
      <td>채치수</td>
    </tr>
    <tr>
      <th>1</th>
      <td>184</td>
      <td>정대만</td>
    </tr>
    <tr>
      <th>2</th>
      <td>168</td>
      <td>송태섭</td>
    </tr>
    <tr>
      <th>3</th>
      <td>187</td>
      <td>서태웅</td>
    </tr>
    <tr>
      <th>4</th>
      <td>188</td>
      <td>강백호</td>
    </tr>
    <tr>
      <th>5</th>
      <td>202</td>
      <td>변덕규</td>
    </tr>
    <tr>
      <th>6</th>
      <td>188</td>
      <td>황태산</td>
    </tr>
    <tr>
      <th>7</th>
      <td>190</td>
      <td>윤대협</td>
    </tr>
  </tbody>
</table>
</div>


### 컬림지정 생성



```python
df = pd.DataFrame(data, columns=['이름','키','학교'])
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>키</th>
      <th>학교</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>197</td>
      <td>북산고</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>184</td>
      <td>북산고</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>168</td>
      <td>북산고</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>187</td>
      <td>북산고</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>188</td>
      <td>북산고</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>202</td>
      <td>능남고</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>188</td>
      <td>능남고</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>190</td>
      <td>능남고</td>
    </tr>
  </tbody>
</table>
</div>


### 인덱스



```python
df = pd.DataFrame(data, index=['1번','2번','3번','4번','5번','6번','7번','8번'])
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td></td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td></td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


#### 인덱스확인



```python
df.index
```

<pre>
Index(['1번', '2번', '3번', '4번', '5번', '6번', '7번', '8번'], dtype='object')
</pre>
#### 인덱스 이름 지정



```python
df.index.name='안녕'
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>안녕</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1번</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>2번</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>3번</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>4번</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td></td>
    </tr>
    <tr>
      <th>5번</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td></td>
    </tr>
    <tr>
      <th>6번</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>7번</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>8번</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


#### 인덱스 초기화



```python
#drop 기존 인덱스 삭제, inplace 변경 유지
df.reset_index(drop=True,inplace=True)
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td></td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td></td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


#### 컬럼으로 인덱스  설정



```python
#drop 기존 인덱스 삭제, inplace 변경 유지
df.set_index('이름')
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td></td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td></td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


#### 인덱스 정렬



```python
#ascending=false 내림차순
df.sort_index()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td></td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td></td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


## 저장하기



```python
#CSV 파일로 저장
df.to_csv('score.csv',encoding='UTF-8',index=False)
```


```python
# TXT  파일로저장  sep = 구분자 \t 는 탭
df.to_csv('score.txt',sep='\t')
```

## 열기



```python
#skiprows= 지정된 row를 건너뜀, nrows = 지정된 갯수만큼 row 만 가져옴
df = pd.read_csv('score.csv')
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df = pd.read_csv('score.txt',sep='\t',index_col='이름')
df=df.drop('Unnamed: 0',axis=1)
```

## dataframe 확인



```python
#계산 가능한 데이터에대한 정ㅂ로ㅡㄹ 알려줌
df.describe()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>8.000000</td>
      <td>8.000000</td>
      <td>8.000000</td>
      <td>8.000000</td>
      <td>8.000000</td>
      <td>8.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>188.000000</td>
      <td>62.500000</td>
      <td>65.625000</td>
      <td>66.250000</td>
      <td>70.000000</td>
      <td>60.625000</td>
    </tr>
    <tr>
      <th>std</th>
      <td>9.985704</td>
      <td>29.519969</td>
      <td>26.917533</td>
      <td>30.325614</td>
      <td>23.754699</td>
      <td>32.120032</td>
    </tr>
    <tr>
      <th>min</th>
      <td>168.000000</td>
      <td>15.000000</td>
      <td>20.000000</td>
      <td>10.000000</td>
      <td>35.000000</td>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>186.250000</td>
      <td>40.000000</td>
      <td>53.750000</td>
      <td>48.750000</td>
      <td>51.250000</td>
      <td>32.500000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>188.000000</td>
      <td>67.500000</td>
      <td>70.000000</td>
      <td>70.000000</td>
      <td>77.500000</td>
      <td>77.500000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>191.750000</td>
      <td>82.500000</td>
      <td>85.000000</td>
      <td>91.250000</td>
      <td>87.500000</td>
      <td>81.250000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>202.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>100.000000</td>
      <td>95.000000</td>
      <td>95.000000</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.info()
```

<pre>
<class 'pandas.core.frame.DataFrame'>
Index: 8 entries, 채치수 to 윤대협
Data columns (total 8 columns):
 #   Column  Non-Null Count  Dtype 
---  ------  --------------  ----- 
 0   학교      8 non-null      object
 1   키       8 non-null      int64 
 2   국어      8 non-null      int64 
 3   영어      8 non-null      int64 
 4   수학      8 non-null      int64 
 5   과학      8 non-null      int64 
 6   사회      8 non-null      int64 
 7   SW특기    6 non-null      object
dtypes: int64(6), object(2)
memory usage: 576.0+ bytes
</pre>

```python
df.values
```

<pre>
array([['북산고', 197, 90, 85, 100, 95, 85, 'Python'],
       ['북산고', 184, 40, 35, 50, 55, 25, 'Java'],
       ['북산고', 168, 80, 75, 70, 80, 75, 'Javascript'],
       ['북산고', 187, 40, 60, 70, 75, 80, nan],
       ['북산고', 188, 15, 20, 10, 35, 10, nan],
       ['능남고', 202, 80, 100, 95, 85, 80, 'C'],
       ['능남고', 188, 55, 65, 45, 40, 35, 'PYTHON'],
       ['능남고', 190, 100, 85, 90, 95, 95, 'C#']], dtype=object)
</pre>

```python
df.index
```

<pre>
Index(['채치수', '정대만', '송태섭', '서태웅', '강백호', '변덕규', '황태산', '윤대협'], dtype='object', name='이름')
</pre>

```python
df.columns
```

<pre>
Index(['학교', '키', '국어', '영어', '수학', '과학', '사회', 'SW특기'], dtype='object')
</pre>

```python
df.shape #row ,col
```

<pre>
(8, 8)
</pre>
## Series 확인



```python
df['키'].describe()
```

<pre>
count      8.000000
mean     188.000000
std        9.985704
min      168.000000
25%      186.250000
50%      188.000000
75%      191.750000
max      202.000000
Name: 키, dtype: float64
</pre>

```python
df['키'].min()
```

<pre>
168
</pre>

```python
df['키'].max()
```

<pre>
202
</pre>

```python
df['키'].nlargest(3) #큰거 순서대로 3개
```

<pre>
이름
변덕규    202
채치수    197
윤대협    190
Name: 키, dtype: int64
</pre>

```python
df['SW특기'].count()
```

<pre>
6
</pre>

```python
df['SW특기'].unique() #유니크한값 보여줌
```

<pre>
array(['Python', 'Java', 'Javascript', nan, 'C', 'PYTHON', 'C#'],
      dtype=object)
</pre>

```python
df['SW특기'].nunique() #유니크한 값의 갯수
```

<pre>
6
</pre>
## 데이터 선택


### 기본


#### iloc



```python
df.columns
```

<pre>
Index(['학교', '키', '국어', '영어', '수학', '과학', '사회', 'SW특기'], dtype='object')
</pre>

```python
df.iloc[:,0] # 행 열이며 iloc은 숫자로 가져옴
```

<pre>
이름
채치수    북산고
정대만    북산고
송태섭    북산고
서태웅    북산고
강백호    북산고
변덕규    능남고
황태산    능남고
윤대협    능남고
Name: 학교, dtype: object
</pre>
#### loc



```python
df.loc['채치수':'윤대협','학교'] #loc은 문자열로 가져옴
```

<pre>
이름
채치수    북산고
정대만    북산고
송태섭    북산고
서태웅    북산고
강백호    북산고
변덕규    능남고
황태산    능남고
윤대협    능남고
Name: 학교, dtype: object
</pre>

```python
df.loc[['채치수','윤대협'],'학교']
```

<pre>
이름
채치수    북산고
윤대협    능남고
Name: 학교, dtype: object
</pre>
### 조건



```python
df[df['키'] >=185]
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>채치수</th>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>서태웅</th>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>강백호</th>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>변덕규</th>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>황태산</th>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>윤대협</th>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
filt = df['키'] >=185
df[~filt] #물결표시를 주면 반대 결과를 취할수있음 그런데 변수를 안취하면 안먹히네
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>정대만</th>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>송태섭</th>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.loc[df['키']>=185,'수학'] #loc에도 조건을 넣을 수 있음
```

<pre>
이름
채치수    100
서태웅     70
강백호     10
변덕규     95
황태산     45
윤대협     90
Name: 수학, dtype: int64
</pre>
#### 다양한 ㅈ고ㅓㄴ



```python
df[ (df['키'] >=185) & (df['학교'] == '북산고')] # &  =  AND
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>채치수</th>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>서태웅</th>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>강백호</th>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.loc[ (df['키'] >=185) & (df['학교'] == '북산고')]
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>채치수</th>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>서태웅</th>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>강백호</th>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.loc[ (df['키'] <170) | (df['키'] > 200)] # | = OR
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>송태섭</th>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>변덕규</th>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
  </tbody>
</table>
</div>


## str 함수



```python
filt = df['학교'].str.startswith('능') #특정 글자로 시작하는
df[filt]
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>변덕규</th>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>황태산</th>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>윤대협</th>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
filt = df['학교'].str.contains('남') #특정 글자가 들어가는
df[filt]
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>변덕규</th>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>황태산</th>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>윤대협</th>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
filt = df['학교'].str.contains('남') #특정 글자가 들어가는
df[~filt]#반대
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>채치수</th>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>정대만</th>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>송태섭</th>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>서태웅</th>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>강백호</th>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



```python
langs = ["Python","Java"]
filt = df['SW특기'].isin(langs) #특정 값이 들어있는지
df[filt] #소대문자가 다르게 인식되는 문제
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>채치수</th>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>정대만</th>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
  </tbody>
</table>
</div>



```python
langs = ["python","java"]
filt = df['SW특기'].str.lower().isin(langs) #시리즈를 문자열로 바꾸고 소문자로 바꾼 후 비교
df[filt] 
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>채치수</th>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>정대만</th>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>황태산</th>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
  </tbody>
</table>
</div>



```python
langs = ["python","java"]
filt = df['SW특기'].str.contains('Java',na=False) #na를 어떻게 처리할 것인가?
df[filt] 
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>정대만</th>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>송태섭</th>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
  </tbody>
</table>
</div>


## 결측치


### 결측치를 데이터로 채우기



```python
df.fillna('없음')# 특정값으로 결측치를 채움
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>채치수</th>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>정대만</th>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>송태섭</th>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>서태웅</th>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>없음</td>
    </tr>
    <tr>
      <th>강백호</th>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>없음</td>
    </tr>
    <tr>
      <th>변덕규</th>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>황태산</th>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>윤대협</th>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


### 결측치로 채우기



```python
import numpy as np
df['학교'] = np.nan
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>채치수</th>
      <td>NaN</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>정대만</th>
      <td>NaN</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>송태섭</th>
      <td>NaN</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>서태웅</th>
      <td>NaN</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>강백호</th>
      <td>NaN</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>변덕규</th>
      <td>NaN</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>황태산</th>
      <td>NaN</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>윤대협</th>
      <td>NaN</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['학교'].fillna('모ㅗ름',inplace=True)
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
    <tr>
      <th>이름</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>채치수</th>
      <td>모ㅗ름</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>정대만</th>
      <td>모ㅗ름</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>송태섭</th>
      <td>모ㅗ름</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>서태웅</th>
      <td>모ㅗ름</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>강백호</th>
      <td>모ㅗ름</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>변덕규</th>
      <td>모ㅗ름</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>황태산</th>
      <td>모ㅗ름</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>윤대협</th>
      <td>모ㅗ름</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


### 결측치 버리기



```python
df=pd.read_csv('score.csv') #다시가져옴
df.dropna()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>


- axis : index or columns 결측치가있을때 열을지울지 행을 지울지

- how : any or all 하나만 결측치가 있어도 지울지 전부 결측치일때 지울지



```python
df.dropna(axis='index',how='any')
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.dropna(axis='columns',how='any')
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
    </tr>
  </tbody>
</table>
</div>


## 데이터 정렬



```python
df.sort_values('키',ascending=False)
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.sort_values(['수학','영어'],ascending=[True,False])
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
  </tbody>
</table>
</div>


## 데이터 수정


### 컬럼 수정



```python
df['학교'].replace({'북산고':'상북고'},inplace=True)
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>상북고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>상북고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>상북고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>상북고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['학교']= df['학교']+'등학교'
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['국영'] = df['국어'] + df['영어']
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>100</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>35</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>120</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['결과'] = 'Fail'
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
      <th>결과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>100</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>35</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>120</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
      <td>Fail</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.loc[df['국영'] > 150,'결과'] = 'Pass'
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
      <th>결과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>100</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>35</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>120</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>


### 컬럼 삭제 ,  로우 삭제



```python
df.drop(columns=['결과','국영'])
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.drop(index=7)
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
      <th>결과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>100</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>35</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>120</td>
      <td>Fail</td>
    </tr>
  </tbody>
</table>
</div>



```python
filt = df['수학'] < 80
df.drop(df[filt].index) #df.drop(index = df[filt].index)
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
      <th>결과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>


### Row 추가



```python
df.loc[8] = ['이정환','해남고등학교',184,90,90,90,90,90,'Kotlin',450,'Pass']
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
      <th>결과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>100</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>상북고등학교</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>35</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>120</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>8</th>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>


### Cell 수정



```python
df.loc[4,['학교','SW특기']] = ['중졸','없음']
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
      <th>결과</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>100</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>중졸</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>없음</td>
      <td>35</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>120</td>
      <td>Fail</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
      <td>Pass</td>
    </tr>
    <tr>
      <th>8</th>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
      <td>Pass</td>
    </tr>
  </tbody>
</table>
</div>


### 컬럼 순서 변경



```python
cols = list(df.columns)
cols
```

<pre>
['이름', '학교', '키', '국어', '영어', '수학', '과학', '사회', 'SW특기', '국영', '결과']
</pre>

```python
df = df[[cols[-1]] + cols[:-1]]
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>결과</th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pass</td>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Fail</td>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pass</td>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Fail</td>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>100</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Fail</td>
      <td>강백호</td>
      <td>중졸</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>없음</td>
      <td>35</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Pass</td>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Fail</td>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>120</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Pass</td>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Pass</td>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
    </tr>
  </tbody>
</table>
</div>


### 컬럼 이름 변경



```python
#df.columns = ['컬럼이름들']
```

## 함수 적용



```python
def add_cm(height):
    return str(height) + 'cm'

df['키'] = df['키'].apply(add_cm)
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>결과</th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pass</td>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197cm</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Fail</td>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184cm</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pass</td>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168cm</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Fail</td>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187cm</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>100</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Fail</td>
      <td>강백호</td>
      <td>중졸</td>
      <td>188cm</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>없음</td>
      <td>35</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Pass</td>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202cm</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Fail</td>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188cm</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>120</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Pass</td>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190cm</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Pass</td>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184cm</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
    </tr>
  </tbody>
</table>
</div>



```python
def capitalize(lang):
    if pd.notnull(lang): #NaN이 아니라면
        return lang.capitalize() #첫글자는 대문자로 나머지는 소문자로
    
df['SW특기'] = df['SW특기'].apply(capitalize)
df
# df['SW특기'].str.capitalize() 이거랑 똑같음..
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>결과</th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pass</td>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197cm</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Fail</td>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184cm</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pass</td>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168cm</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Fail</td>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187cm</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>None</td>
      <td>100</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Fail</td>
      <td>강백호</td>
      <td>중졸</td>
      <td>188cm</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>없음</td>
      <td>35</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Pass</td>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202cm</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Fail</td>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188cm</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>Python</td>
      <td>120</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Pass</td>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190cm</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Pass</td>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184cm</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
    </tr>
  </tbody>
</table>
</div>


## 그룹화



```python
df.groupby('학교').get_group('상북고등학교')
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>결과</th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pass</td>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197cm</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Fail</td>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184cm</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pass</td>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168cm</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Fail</td>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187cm</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>None</td>
      <td>100</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.groupby('학교').mean()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>국영</th>
    </tr>
    <tr>
      <th>학교</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>능남고등학교</th>
      <td>78.333333</td>
      <td>83.333333</td>
      <td>76.666667</td>
      <td>73.333333</td>
      <td>70.00</td>
      <td>161.666667</td>
    </tr>
    <tr>
      <th>상북고등학교</th>
      <td>62.500000</td>
      <td>63.750000</td>
      <td>72.500000</td>
      <td>76.250000</td>
      <td>66.25</td>
      <td>126.250000</td>
    </tr>
    <tr>
      <th>중졸</th>
      <td>15.000000</td>
      <td>20.000000</td>
      <td>10.000000</td>
      <td>35.000000</td>
      <td>10.00</td>
      <td>35.000000</td>
    </tr>
    <tr>
      <th>해남고등학교</th>
      <td>90.000000</td>
      <td>90.000000</td>
      <td>90.000000</td>
      <td>90.000000</td>
      <td>90.00</td>
      <td>450.000000</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.groupby('학교').size()
```

<pre>
학교
능남고등학교    3
상북고등학교    4
중졸        1
해남고등학교    1
dtype: int64
</pre>

```python
df.groupby('학교').size()['능남고등학교'] #그룹화 후 원하는 그룹만 볼수있음
```

<pre>
3
</pre>

```python
def unnumeric(cm):
    return int(cm[:3])
df['키']=df['키'].apply(unnumeric)
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>결과</th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>국영</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Pass</td>
      <td>채치수</td>
      <td>상북고등학교</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>175</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Fail</td>
      <td>정대만</td>
      <td>상북고등학교</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>75</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Pass</td>
      <td>송태섭</td>
      <td>상북고등학교</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>155</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Fail</td>
      <td>서태웅</td>
      <td>상북고등학교</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>None</td>
      <td>100</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Fail</td>
      <td>강백호</td>
      <td>중졸</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>없음</td>
      <td>35</td>
    </tr>
    <tr>
      <th>5</th>
      <td>Pass</td>
      <td>변덕규</td>
      <td>능남고등학교</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>180</td>
    </tr>
    <tr>
      <th>6</th>
      <td>Fail</td>
      <td>황태산</td>
      <td>능남고등학교</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>Python</td>
      <td>120</td>
    </tr>
    <tr>
      <th>7</th>
      <td>Pass</td>
      <td>윤대협</td>
      <td>능남고등학교</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>185</td>
    </tr>
    <tr>
      <th>8</th>
      <td>Pass</td>
      <td>이정환</td>
      <td>해남고등학교</td>
      <td>184</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>90</td>
      <td>Kotlin</td>
      <td>450</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.groupby('학교')['키'].mean()
```

<pre>
학교
능남고등학교    193.333333
상북고등학교    184.000000
중졸        188.000000
해남고등학교    184.000000
Name: 키, dtype: float64
</pre>

```python
df.groupby('학교')[['국어','영어','수학']].mean()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
    </tr>
    <tr>
      <th>학교</th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>능남고등학교</th>
      <td>78.333333</td>
      <td>83.333333</td>
      <td>76.666667</td>
    </tr>
    <tr>
      <th>상북고등학교</th>
      <td>62.500000</td>
      <td>63.750000</td>
      <td>72.500000</td>
    </tr>
    <tr>
      <th>중졸</th>
      <td>15.000000</td>
      <td>20.000000</td>
      <td>10.000000</td>
    </tr>
    <tr>
      <th>해남고등학교</th>
      <td>90.000000</td>
      <td>90.000000</td>
      <td>90.000000</td>
    </tr>
  </tbody>
</table>
</div>



```python
df['학년'] = [3,3,2,1,1,3,3,2,3]
df.groupby(['학교','학년']).mean()
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>국영</th>
    </tr>
    <tr>
      <th>학교</th>
      <th>학년</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th rowspan="2" valign="top">능남고등학교</th>
      <th>2</th>
      <td>190.0</td>
      <td>100.0</td>
      <td>85.0</td>
      <td>90.0</td>
      <td>95.0</td>
      <td>95.0</td>
      <td>185.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>195.0</td>
      <td>67.5</td>
      <td>82.5</td>
      <td>70.0</td>
      <td>62.5</td>
      <td>57.5</td>
      <td>150.0</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">상북고등학교</th>
      <th>1</th>
      <td>187.0</td>
      <td>40.0</td>
      <td>60.0</td>
      <td>70.0</td>
      <td>75.0</td>
      <td>80.0</td>
      <td>100.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>168.0</td>
      <td>80.0</td>
      <td>75.0</td>
      <td>70.0</td>
      <td>80.0</td>
      <td>75.0</td>
      <td>155.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>190.5</td>
      <td>65.0</td>
      <td>60.0</td>
      <td>75.0</td>
      <td>75.0</td>
      <td>55.0</td>
      <td>125.0</td>
    </tr>
    <tr>
      <th>중졸</th>
      <th>1</th>
      <td>188.0</td>
      <td>15.0</td>
      <td>20.0</td>
      <td>10.0</td>
      <td>35.0</td>
      <td>10.0</td>
      <td>35.0</td>
    </tr>
    <tr>
      <th>해남고등학교</th>
      <th>3</th>
      <td>184.0</td>
      <td>90.0</td>
      <td>90.0</td>
      <td>90.0</td>
      <td>90.0</td>
      <td>90.0</td>
      <td>450.0</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.groupby('학년').mean().sort_values('키')
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>국영</th>
    </tr>
    <tr>
      <th>학년</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>2</th>
      <td>179.0</td>
      <td>90.0</td>
      <td>80.0</td>
      <td>80.0</td>
      <td>87.5</td>
      <td>85.0</td>
      <td>170.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>187.5</td>
      <td>27.5</td>
      <td>40.0</td>
      <td>40.0</td>
      <td>55.0</td>
      <td>45.0</td>
      <td>67.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>191.0</td>
      <td>71.0</td>
      <td>75.0</td>
      <td>76.0</td>
      <td>73.0</td>
      <td>63.0</td>
      <td>200.0</td>
    </tr>
  </tbody>
</table>
</div>



```python
df.groupby('학교')['학년'].value_counts().loc['상북고등학교'] # 학교로 그룹화 한 뒤에 학년별 학생 수 
```

<pre>
학년
3    2
1    1
2    1
Name: 학년, dtype: int64
</pre>

```python
df.groupby('학교')['학년'].value_counts(normalize=True).loc['상북고등학교'] #학생들의 수 데이터를 퍼센트로 비교하여 가져옴
```

<pre>
학년
3    0.50
1    0.25
2    0.25
Name: 학년, dtype: float64
</pre>
# 데이터 처리 후 시각화 작업



```python
#!pip install matplotlib
```


```python
import matplotlib.pyplot as plt
```

## 그래프 기본



```python
x = [1,2,3]
y = [2,4,8]
plt.plot(x,y)
plt.show()# 그래프만 볼 수 있음
```

<pre>
[<matplotlib.lines.Line2D at 0x1b71fd86d08>]
</pre>
<img src="data:image/png;base64,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"/>

### 타이틀 설정



```python
plt.plot(x,y)
plt.title('하하')
```

<pre>
Text(0.5, 1.0, '하하')
</pre>
<pre>
d:\conda\envs\prsql\lib\site-packages\IPython\core\pylabtools.py:151: UserWarning: Glyph 54616 (\N{HANGUL SYLLABLE HA}) missing from current font.
  fig.canvas.print_figure(bytes_io, **kw)
</pre>
<img src="data:image/png;base64,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"/>

### 한글폰트,마이너스 설정



```python
import matplotlib
matplotlib.rcParams['font.family'] = 'Malgun Gothic' #윈도우 기준 mac은 'Applegothic'
matplotlib.rcParams['font.size'] = 20
matplotlib.rcParams['axes.unicode_minus'] = False # 한글폰트 사용시, 마이너스
```


```python
plt.plot([-1,0,1],[-1,0,1])
plt.title('하하')
```

<pre>
Text(0.5, 1.0, '하하')
</pre>
<img src="data:image/png;base64,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"/>

### 축



```python
plt.plot(x,y)
plt.title('꺾은선그래프',fontdict={'family':'HYGungSo-Bold','size':30})# 개별 폰트설정
```

<pre>
Text(0.5, 1.0, '꺾은선그래프')
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y)
plt.xlabel('x축',color = 'red',loc = 'right') #left right center
plt.ylabel('y축',color = '#00aa00', loc ='top')# top center bottom
```

<pre>
Text(0, 1, 'y축')
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y)
plt.xticks([1,2,3])
plt.yticks([3,6,9,12])
plt.show()
```

<img src="data:image/png;base64,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"/>

### 범례(legend)


![100](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220728200904.png)



범례 위치



```python
plt.plot(x,y,label = '무슨데이터')
plt.legend(loc = 'upper right')
```

<pre>
<matplotlib.legend.Legend at 0x1b7239e9308>
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y,label = '무슨데이터')
plt.legend(loc = (0.5,0.5)) #x,y축 0~1
```

<pre>
<matplotlib.legend.Legend at 0x1b723b15648>
</pre>
<img src="data:image/png;base64,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"/>

### 스타일


[matplotlib marker](https://matplotlib.org/stable/api/markers_api.html)  

[matplotlib color](https://matplotlib.org/stable/gallery/color/named_colors.html)  

[matplotlib linestyle](https://matplotlib.org/2.1.2/api/_as_gen/matplotlib.pyplot.plot.html)  

[matplotlib linestyle2](https://matplotlib.org/stable/gallery/lines_bars_and_markers/linestyles.html) 





```python
plt.plot(x,y, linewidth =5)
```

<pre>
[<matplotlib.lines.Line2D at 0x1b7235eab88>]
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y,marker ='o')
```

<pre>
[<matplotlib.lines.Line2D at 0x1b72332ba08>]
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y,marker ='o',linestyle ='None')
```

<pre>
[<matplotlib.lines.Line2D at 0x1b723b7fe88>]
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y,marker ='v',markersize = 10)
```

<pre>
[<matplotlib.lines.Line2D at 0x1b724bc4e08>]
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y,marker ='x',markersize = 10,markeredgecolor='red')
```

<pre>
[<matplotlib.lines.Line2D at 0x1b724c9b888>]
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y,marker ='o',markersize = 10,markeredgecolor='red', markerfacecolor ='yellow')
```

<pre>
[<matplotlib.lines.Line2D at 0x1b724e6af88>]
</pre>
<img src="data:image/png;base64,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"/>

### 선 스타일



```python
plt.plot(x,y,linestyle = '--')
```

<pre>
[<matplotlib.lines.Line2D at 0x1b724ed69c8>]
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y,linestyle = '-.')
```

<pre>
[<matplotlib.lines.Line2D at 0x1b724f48fc8>]
</pre>
<img src="data:image/png;base64,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"/>

### 색



```python
plt.plot(x,y,color = 'crimson')
```

<pre>
[<matplotlib.lines.Line2D at 0x1b725038648>]
</pre>
<img src="data:image/png;base64,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"/>

### 포맷



```python
plt.plot(x,y,'ro--')# color,marker,linestyle
```

<pre>
[<matplotlib.lines.Line2D at 0x1b72509e188>]
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y,'bv:')# color,marker,linestyle
```

<pre>
[<matplotlib.lines.Line2D at 0x1b725106e48>]
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(x,y,'gv')# color,marker,linestyle
```

<pre>
[<matplotlib.lines.Line2D at 0x1b72524f748>]
</pre>
<img src="data:image/png;base64,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"/>

### 축약어


[축약어](https://matplotlib.org/stable/api/_as_gen/matplotlib.pyplot.plot.html)  

markeredgecolor or mec



markeredgewidth or mew



markerfacecolor or mfc



markerfacecoloralt or mfcalt



markersize or ms




```python
plt.plot(x,y,marker = 'o', mfc = 'red', ms=10 , mec ='blue', ls= ':')
```

<pre>
[<matplotlib.lines.Line2D at 0x1b724ce81c8>]
</pre>
<img src="data:image/png;base64,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"/>

### 투명도



```python
plt.plot(x,y,'rv-',alpha = 0.3)
```

<pre>
[<matplotlib.lines.Line2D at 0x1b7252c8b08>]
</pre>
<img src="data:image/png;base64,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"/>

### 크기



```python
plt.figure(figsize = (10,5))
plt.plot(x,y)
```

<pre>
[<matplotlib.lines.Line2D at 0x1b725330a08>]
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.figure(figsize = (10,5),dpi = 100) #dpi  해상도
plt.plot(x,y)
```

<pre>
[<matplotlib.lines.Line2D at 0x1b725c0a948>]
</pre>
<img src="data:image/png;base64,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"/>

### 배경색



```python
plt.figure(facecolor = '#a1c3ff')
plt.plot(x,y)
```

<pre>
[<matplotlib.lines.Line2D at 0x1b72553e888>]
</pre>
<img src="data:image/png;base64,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"/>

### 파일저장



```python
plt.plot(x,y)
plt.savefig('graph.png',dpi=100) # dpi안주면 이전 dpi를 따라감
```

<img src="data:image/png;base64,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"/>

### 텍스트



```python
plt.plot(x,y,marker ='o')
for idx,txt in enumerate(y):
    plt.text(x[idx],y[idx]+0.3,txt,ha='center',color='blue') #x좌표, y좌표, 표시할text , 정렬, 색
```

<img src="data:image/png;base64,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"/>

### 여러데이터



```python
days = [1,2,3] #1일 2일 3일
az = [2,4,8] # 만명 단위 아스트라제네카 접종인구
pfizer = [5,1,3] #화이자
moderna = [1,2,5] #모더나
```


```python
plt.plot(days,az,label ='az')
plt.plot(days,pfizer,'o--',label='pfizer')
plt.plot(days,moderna,'g:',label='moderna')
plt.legend(loc=5)
```

<pre>
<matplotlib.legend.Legend at 0x1b7263e2f88>
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.plot(days,az,label ='az')
plt.plot(days,pfizer,'o--',label='pfizer')
plt.plot(days,moderna,'g:',label='moderna')
plt.legend(loc=5,ncol=2) #몇 열로 정렬할지 정할 수 있다
```

<pre>
<matplotlib.legend.Legend at 0x1b7275c6108>
</pre>
<img src="data:image/png;base64,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"/>

## 막대그래프



```python
labels = ['강백호','서태웅','정대만']
values = [190,187,184]
plt.bar(labels,values,color=['r','g','b'],alpha=0.5)
```

<pre>
<BarContainer object of 3 artists>
</pre>
<img src="data:image/png;base64,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"/>

#### 축 글자 돌리기



```python
plt.bar(labels,values,width=0.5)
plt.xticks(rotation=45)# 옆을 돌리기
```

<pre>
([0, 1, 2], [Text(0, 0, ''), Text(0, 0, ''), Text(0, 0, '')])
</pre>
<img src="data:image/png;base64,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"/>

#### 축 텍스트 변경



```python
ticks =['ㅂㅂ','ㅈㅈ','ㄷㄷ']
plt.bar(labels,values,width=0.5)
plt.xticks(labels,ticks) #x축을 labels => ticks로 변경 ticks만 쓰면 아예 따로나옴
```

<pre>
([<matplotlib.axis.XTick at 0x1b724e2c148>,
  <matplotlib.axis.XTick at 0x1b727a51188>,
  <matplotlib.axis.XTick at 0x1b727a45908>],
 [Text(0.0, 0, 'ㅂㅂ'), Text(1.0, 0, 'ㅈㅈ'), Text(2.0, 0, 'ㄷㄷ')])
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.barh(labels,values,height=0.5)## 옆을 돌린 막대그래프
plt.xlim(175,19)
```

<pre>
(175.0, 195.0)
</pre>
<img src="data:image/png;base64,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"/>

[hatchstyle](https://matplotlib.org/stable/gallery/shapes_and_collections/hatch_style_reference.html)



```python
bar=plt.barh(labels,values)
bar[0].set_hatch('/')
bar[1].set_hatch('*')
bar[2].set_hatch('+')
```

<img src="data:image/png;base64,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"/>


```python
bar=plt.bar(labels,values)
plt.ylim(175,195)
for idx, rect in enumerate(bar):
    print(rect)
    plt.text(idx, rect.get_height()+0.5,values[idx],ha='center',color ='blue')
```

<pre>
Rectangle(xy=(-0.4, 0), width=0.8, height=190, angle=0)
Rectangle(xy=(0.6, 0), width=0.8, height=187, angle=0)
Rectangle(xy=(1.6, 0), width=0.8, height=184, angle=0)
</pre>
<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAYUAAAELCAYAAAA2mZrgAAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjUuMiwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8qNh9FAAAACXBIWXMAAAsTAAALEwEAmpwYAAAh0klEQVR4nO3deZxU1Z338c8XSRSNGwE0OiEkuOLGCC7JRDGJZBwXEhQzGX0COCpoHCfi8lJHJ2Iek2hwGw2DC/OIxnGSwSVxG6PEgBqXBByDihBFMSYKSKKoiETg9/xxbt+uLm51V3dXdTfd3/fr1a+izz331mkK6tv3bKWIwMzMDKBXZzfAzMy6DoeCmZnlHApmZpZzKJiZWc6hYGZmOYeCmZnlHApmZpZrdShIGitpeYVjm0v6rqTFktZIelXSpZL6FNSdLSkqfA1qw89iZmbt1LvaipKGAd8HRgKrCo5vCswC9gOmA/OBYcA5wD6SDo8NV8qtyI6XW1Ftu8zMrHaqCgVJc4CDgaXA08CuBdXOBj4LjIqIe0rO/S1wDTAauLPsnD9GxIzWN9vMzOqh2u6jAcB3SGHwbIU6xwNPlgZCZhrwR+AbBef8ucrnNzOzDlBt99GQhq4fSZXqDAb+s7wwItZKeho4oOCct6p8fjMz6wBV3SkUjAUUWQ1sV+HYOuATkj5SVv6OpL6StqqmHWZmVl9VDzRX4VHgS5I+GRGvNRRK2g4YkX27BfB2yTnjsy8kLQNuBSZHxHuVnkTSBGACwBZbbDFst912q91PYGbWA8ybN29FRPQvOqbWbp0taQYwJiI+Vla+P/Ar4GXSjKLnSWMQlwJbAZ8C+kTEB1n9I4EtgfeAHYDDgVHAb4CDImJNS20ZPnx4zJ07t1XtNzPr6STNi4jhRcdqdqcQEb+WNBq4AfhZVryWNPOoF3BKQyBk9e8tu8T1ks4lhcgJwHW1apuZmVWnpiuaszf6gcD+wCHAjhFxFjAIWFjFJS4HPgC+VMt2mZlZdWo5pgCk2UakLiAAJPUCPgfcXsW567KxBQ88m5l1go7Y++ho0jqHH7dUUdI2wCeBV+vcJjMzK1CzUFDBAgZJOwHXAg9GxKMl5X0llQ9Ub5LV7UUVAWJmZrVXy+6j/SVNAX5O2rtoT2AcaWuM8tXMewN3SPoJsADoS7qj2Af4t4h4uIbtMjOzKtUyFF4H1gBnAZuTuoCuBS6NiHfL6r4EPAaMIQXCKtKeSl+LiJk1bJOZmbVCq0MhIsaTLTgrK3+NtINqNdf4A/CV1j63mZnVlz9kx8zMcg4FMzPLORTMzCznUDAzs5xDwczMcg4FMzPLORTMzCznUDAzs5xDwczMcg4FMzPLORTMzCznUDAzs5xDwczMcg4FMzPLORTMzCznUDAzs5xDwczMcg4FMzPLORTMzCznUDAzs5xDwczMcg4FMzPLORTMzCznUDAzs5xDwczMcg6FTnTLLTBgQPGx99+HCy6AwYNh003hU5+C886D1auL699zD3z2s7DFFtCvH3zjG7B0af3abmbdk0OhE8ybB1/+Mowbl978y61ZA4ceCj/4Qap39dUwciRMmQJHHw0RTevPmAGjRsHHPpbqnHwy3HUXHHQQrFzZET+RmXUXvTu7AT3NiBHwyCOw/faw776waNGGdS6/HJ54Au6+G446qrF8n33gn/85veEffXQq+/OfU9nRR8Ptt4OUyg8+GA4/HK66CiZPrvuPZWbdhO8UOtjy5fDtb6cw2Guv4jr/+Z9w4IFNAwHg1FNhxx3hRz9qWvfdd+G7320MBIC/+zsYPjwdNzOrlkOhgy1YABdfDFttVbnO4sWw++4blvfune4unnqqsWzWLBg0CHbbbcP6I0fCSy+lIDIzq4ZDoYOV/jZfSZ8+sGxZ8bFNNoE33oAPP0zfv/ACDBlSXHfXXdPj4sWtb6eZ9UwOhS7ooIPgl7+E115rWr5sGcyZk/68alV6fOONND5RpGFm01tv1aedZtb9OBS6oH/913QncOihabB58WK4//7UHdTQ7bTZZulx9eo0ZbVIQ/lf/lL/NptZ9+BQ6IL23z/NMHr3XfjKV2CnndLjyJEwenQKhIZQ6N0b1q4tvk5DGPTp0zHtNrONn6ekdlFHHgm//z387/+mtQy77566g0aPbjqovM02aVpqkT/9KT1WWiBnZlbOodCF9e4N++3X+P369fD44zBmTGPZzjvD735XfP6iRdCrF+yyS33baWbdh7uPNiJ33pmml379641lBx0Ezz8Pr7++Yf2HHmrc+sLMrBoOhS6ofBsLSOsNTj89bXtx0EGN5WPHpseLL25a/4EH4Mkn4ZRT6tdOM+t+3H3UBf3613DOOfC3f5s2t3vuObj55jT1tHQ1M6TxhUmT4Ior4M03U2i8/DJMnZq2uTjuuM75Gcxs49TqOwVJYyUVrpGVtLmk70paLGmNpFclXSqpcP6LpKMkPSFplaQVkn4kqcKs+55jhx3SdNIrroBvfQsefDDdJcybVzxoPGVKqvvss6n+7benULnrrjSmYGZWLUVRX0VRRWkY8H1gJLAqIj5WdnxT4JfAfsB0YD4wDDgBeBA4PEqeTNJ44CZgFnAX8EngdOANYHhEtLi/5/Dhw2Pu3LlVtd/MzBJJ8yJieNGxqrqPJM0BDgaWAk8DuxZUOxv4LDAqIu4pOfe3wDXAaODOrKxvVnYnMKYhLCQ9AtwPTAImV9M2MzOrnWo7FwYA3yGFwbMV6hwPPFkaCJlpwB+Bb5TV3RK4oPTuISL+B5ibHTczsw5WbSgMiYiLIuKdZuoMBl4oL4yItaS7iwNKig8FlkTEwoLrPATsJMlLrszMOlhVoRDVDTysBrarcGwd8AlJH8m+3x1YUKFuw8fODK6mbWZmVju1nJL6KPAlSZ+MiHx/T0nbASOyb7cA3gY+kdUv0jCzaduig5ImABMABg4c2K4GDzrvvnadb5UtufSIzm6CmbVBLScs/l/gI8AsSaMkDZZ0OKk7qKHb6YPssQ+wpsJ1Gso/WnQwIm6IiOERMbx///41arqZmUENQyEifk2aYbQl8DPgpezxIdKU0w8ioiEU1lL5LqUhDFbXqm1mZladmq5ojoh7JQ0E/hrYHHghIpZLugsoHVR+G+hb4TIfzx79IZJmZh2s5ttcZLONftPwvaRewOeA20uqvQhU2rtzV2A9UGHvTzMzq5eO2AThaNI6hx+XlD0K7CFph4L6I4EnImJVB7TNzMxK1CwUpA0/kl7STsC1wIMRUTrb6Jbs8aKy+ocBBwLX1apdZmZWvVp2H+0vaQrwc2AFsCcwjrQ1RulqZiJioaSrgLMk9SftjfQZ4DTSNhe31bBdZmZWpVqGwuuk6aRnkQaZXyXdJVwaEe8W1D8nO+dU4AjSVhhTgO9FxPoatsvMzKrU6lCIiPHA+ILy10jjAdVeJ4Arsy8zM+sCvNu+mZnlHApmZpZzKJiZWc6hYFalW24p/jhUgLVr00eiDhkCffrATjvBGWfAW281rSe1/PXqq3X/UcwqqvmKZrPuZt48OP98eOgh2GKL4jrjxsFtt8Gxx8Jpp8GLL8L118N996Xzt9oq1bvppsrPc/750L8/tHPzX7N2cSiYNWPECHjkEdh+e9h3X1i0aMM68+enQDjjDLjqqsbyQw6B0aNh+nQ488xUNn588fM8/DAsXQo//GG6WzDrLO4+MmvG8uXw7W+nMNhrr+I6L2SfNzhqVNPyI4+EXr3SXUNLLroI9t4bjj66fe01ay/fKZg1Y8GCln9z32OP9Dh/PnzhC43lzz8P69enN/vmzJkDjz0Gd97puwTrfA4Fs2ZU8ya9554wcSJceCFsvjl88YvpzuKMM2DYMDjhhObPnzIlDUx/9au1aLFZ+zgUzGpg6lRYsgQmTGgs23HHdAew2WaVz1u4EO6/PwWD7xKsK/CYglk7rVuXZh3NmQPnngszZ6Y3+fXr00D1ihWVz502LYVGS3cTZh3Fdwpm7XTttfDTn8Ls2XDwwY3lY8emrqVTT01BUe6DD+BHP4KvfQ36VvocQrMO5jsFs3a68cY0/bQ0ECAtdDvtNLjjDnjzzQ3Pu/fetLjt7/++Q5ppVhWHglk7LV4MgwYVHxs0CCLg5Zc3PDZzJmy5ZRqYNusqHApm7dSvX+W1CAsXNtYp9eGHaYD5sMNg003r2z6z1nAomLXTMcekWUYPPNC0/JVX0kDyXnvB4MFNjz35JLz3nu8SrOvxQLNZO02eDLNmwVFHpW0shg5N01NvvDHNTJo+fcNzHnssPQ4d2mHNNKuKQ8GsnbbdFh5/HC65BG6/HW6+GbbeOnUNTZ4Mu+224TnPPJO2wGhptbNZR1P6VMyN0/Dhw2Pu3LltPn/QeffVsDVWasmlR3R2E8ysAknzImJ40TGPKZiZWc6hYGZmOYeCmZnlPNBsGw2PAdWPx4Csge8UzMws51AwM7OcQ8HMzHIOBTMzyzkUzMws51AwM7OcQ8HMzHIOBTMzyzkUzMws51AwM7OcQ8HMzHIOBTMzyzkUzKzbuuUWGDCg+NjatXDFFTBkCPTpAzvtBGecAW+91fJ1b7oJJPinf6ppc7sEh4KZdTvz5sGXvwzjxsH77xfXGTcOzj4b9twTLr8cjjwSrr8e9t8f3nmn8rXXrk0fvdpdeetsM+tWRoyARx6B7beHffeFRYs2rDN/Ptx2W7ozuOqqxvJDDoHRo2H6dDjzzOLr33ADrFxZj5Z3Da2+U5A0VtLyCsd6SzpL0gJJqyW9JOlqSdsW1J0tKSp8DWrDz2JmxvLl8O1vpzDYa6/iOi+8kB5HjWpafuSR0KsXvPhi8XnLlsEFF8D3vle79nY1Vd8pSBoGfB8YCayqUO1m4DhgJjAV2BmYCBwhaVhElN+UrQDOKbjOimrbZWZWasGC1N/fnD32SI/z58MXvtBY/vzzsH497L138XmTJsHOO8NJJ8HEibVpb1dTVShImgMcDCwFngZ2LaizNykQro6ISSXls4G7gJOAK8tO+2NEzGhLw83MirQUCJDGESZOhAsvhM03hy9+Md1ZnHEGDBsGJ5yw4TkzZ8J//zc88US6m+iuqr1TGAB8B7gCuIaCUAB2zx7vLiu/F1hPumso9+cqn9/MrKamToUlS2DChMayHXeExx6DzTZrWve111KInH8+7Ldfhzazw1Wbd0Mi4qKC7p9Sz2eP5Tdee2TPM7/gnComf5mZ1da6dXDssTBnDpx7broLmDIldR2NGAErSjqw166F44+HXXaBiy7qvDZ3lKruFCIiqqjznKTrgUskvQ88TLqjuBqYB9xUcNo7kvoCa1sIHDOzmrn2WvjpT2H2bDj44MbysWNT19Kpp6aggNSl9NvfpmmuvXvAfM1a/4inAYOAG0rK/gh8PiI+KKg/PvtC0jLgVmByRLxX6QkkTQAmAAwcOLAWbTazHubGG9P009JAgLTQ7bTT4OKL4c034d57UzfTZZel4y+91LT+ypWpbLvtYMstO6TpdVez4RJJm5BmHY0ALgOOJc0s6gXMkdSv7JTLSQPTo4BTgKeAs4CHJW1a6Xki4oaIGB4Rw/v371+r5ptZD7J4MQwaVHxs0CCIgJdfhptvTmXnnptmHZV+Adx6a/rzHXd0RKs7Ri3vFE4HvgocEhGPNBRKugV4DphGCgoAIuLesvOvl3QucClwAnBdDdtmZpbr16/yWoSFCxvrNNwxFDn2WDjsMDjxxO41+FzLUDgZmF0aCAARsVzSVOAiSf0josJfMZDuHiYDX8KhYGZ1cswxcM018MAD6Y29wSuvwLRpadHb4MHpqzmDB8OYMfVta0erZSgMJnUBFVkCCPgMUDEUImJdNrawVQ3bZWbWxOTJMGsWHHUUjB8PQ4em6ak33phmJk2f3rnt60y1XIKxguK1CAC7ldSpSNI2wCeBV2vXLDOzprbdFh5/PM0smjUrrVSeMSPdNfzmN2lTvJ6qlncKdwD/LOmwiHigoVDSp4FTgWcjYnFW1hf4S+kso2yg+lpSUP24hu0ysx5qxoz0VWTrrdPahClT2nbtlifqb5xqGQqTgUOBeyTNAJ4hTU89GdiEtM1Fg72BOyT9BFgA9AWOBvYB/i0iHq5hu8zMrEo1C4WIeEvS54ALgTHAOGAl8ABp7cHCkuovAY9l9fqSNth7GvhaRMysVZvMzKx1Wh0KETGebMFZwbGVpLUJRTufltb7A/CV1j63mZnVVzfe68/MzFqrB+zkYWadZdB593V2E7qtJZceUZfr+k7BzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOzXKtDQdJYScsrHOst6SxJCyStlvSSpKslbVuh/lGSnpC0StIKST+StH1r22RmZrVRdShIGibpQeBmYPMK1W4GLgeeA84G7gUmAr+WtFXZ9cYDdwPvAecANwKjgUclbd26H8PMzGqhdzWVJM0BDgaWAk8DuxbU2Rs4Drg6IiaVlM8G7gJOAq7MyvoC1wB3AmMiIrLyR4D7gUnA5Db+TGZm1kbV3ikMAL5DCoNnK9TZPXu8u6z8XmA9sHNJ2fHAlsAFDYEAEBH/A8zNjpuZWQerNhSGRMRFEfFOM3Wezx73LivfI3ue+SVlhwJLImJhwXUeAnaSNKDKtpmZWY1U1X1U+tt8M3Wek3Q9cImk94GHSXcWVwPzgJtKqu8OLKhwqUXZ42CgcEDbzMzqo6pQaIXTgEHADSVlfwQ+HxEflJR9Ani0wjUagqDSjKUJwASAgQMHtqetZmZWpmbrFCRtAswERgCXAceSZhX1AuZI6ldSvQ+wpsKlGso/WnQwIm6IiOERMbx///41abuZmSW1vFM4HfgqcEhEPNJQKOkW0hTVaaSgAFjbzHM3hMHqGrbNzMyqUMsVzScDs0sDASAilgNTgWMkNfxq/zbQt8J1Pp49ejzBzKyD1TIUBgNLKhxbAgj4TPb9i8AuFeruSprC+rsats3MzKpQy1BYQdO1CKV2K6kDaZB5D0k7FNQdCTwREatq2DYzM6tCLUPhDuDzkg4rLZT0aeBU4NmIWJwV35I9XlRW9zDgQOC6GrbLzMyqVMuB5smkRWn3SJoBPEOannoysAlpmwsAImKhpKuAs7JxhgdJXUunkba5uK2G7TIzsyrVLBQi4i1JnwMuBMYA44CVwAPA5ILVy+cAr5PuIo4grWeYAnwvItbXql1mZla9VodCRIwHxlc4tpL0Zn9OFdcJ0gZ5V7a2DWZmVh/+kB0zM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOznEPBzMxyDgUzM8s5FMzMLOdQMDOzXKtDQdJYScvLygZJipa+ys5ZUk09MzPrOL2rrShpGPB9YCSwquzwCuCEZp7jWuAXBccWApdV2wYzM6uvqkJB0hzgYGAp8DSwa+nxiHgPmFHh3H8ENgMmFxxeFBGF55mZWcertvtoAPAdUhg8W+3FJfUGLgTuiYi5BVX+XO21zMys/qrtPhoSEQEgqTXXPx74NDCmwvG3WnMxMzOrr6ruFBoCoQ3OAn4REU9XOP6epI9L2qKN1zczsxpSa9/vJc0AxkTEx1qo97fAA1ndOwqOLwE+VVL0KnAj8IOI+LCZ604AJmTf7gosak37N2L9SAP6tvHwa7Zx6Umv16cion/RgXqGws+AYcCgiFhbcPzrQACrgU8CXyMNZt8dEV9pVaN6AElzI2J4Z7fDqufXbOPi1yupekpqa0jaATgCuKQoEAAi4sdlRVMlTQNOkXRYRDxQj7aZmVll9VrRfBywCfCTVp53Sfb4pdo2x8zMqlGvUDgWeDEiXmjleUuBdcBWtW/SRu+Gzm6AtZpfs42LXy/qEAqSPgHsD/y0DafvQbrDeLWWbeoKJG0uafu2nh8RTf7BZrO2xrfnmlZf5a+ZdW1+vZJ63Ckcmj0+XKmCpO0lfbSsrA9wNelO4fY6tKuzfRN4o+iApL0kfa6gfEdJh2WLAJH0TDbQD2n9x03Abq1phKSvS/paq1puZj1GPULh89njM83UOQx4WdKVkr4p6RLgOeAQ4JyI+F0d2lVTkv6phQ0AF7ficmcB/15QPhL4H6DZmV6tdBLwjzW8Xrcm6bps+nRbz58v6Zzsz9tn/zbGt3DOtpLOkzRH0jJJf5G0RtJSSbMlnSNp67a2aWMiabCk3Vr4+nTZOW1+zbI7+j9I+ofs+wOz1+yQGvwsZ28MG37WY/bRUGBZRCxtps480mZ440njByuBp4AJEVG0cV5XdCswq8Kxh2nFdiC1JmkzYFCFw5sD6yRVusN4JSLW1KVhXYykC4CPRcT5bTj3UODrFQ6vjIizsj/vAFT9Bi5pb+BBYA0wDbgYeBMQaR79gcDpwLckfTkiFrS27RuZX9B0PVOR54E9W7pQC6/Z4oj4PukX5R2BFhfUSroMOKa5OhGxU0vX6WpaHQoRMZ70Zl7p+AFVXONZGruZNkoR8Tbwdnm5pCHAJ4D7O7hJpfYEftNCnUqTAP6a5u/yupP9gG3aeO6ewInAzwqObdLWBgHXAe8CwyLinYLjD0v6d9LGlNOAEe14ri4vIgaVfi/pl8B7EXFUGy7X3Gv2pzZcbzugD3BVwbGDgFFtuGanq8s6hR7uX4D3gJmtPG9PSeWrKTctqNdX0lBgl0oXyjYf3GCTKknbANtm3/45Ila2so1WJiK+WuNL7gtcVyEQGp7zbUn3A+Nq/Nwbg78CPmjPBWr8mr0ZEZeXF0pai0PBJI0ibQJ4XkQUbvZX0qe4KCJKu3BeA84pq34IcFpZ2VHZV7VtGpJd9+9Iv9mUHnsDuBeYEhEvVnvNbmQT2vdbfT28BPyNpN6VFn5K+gjwN1ndHkPSzsBO2Z/3iIjnsz+/x4bdPd1uBmNHcSjUiKQDgNtIfaBXNlO14cOIyn9LXxkRTWZdSSoaYP5v4FvAPqS9pZpr06is/iOk/aJ+Q9rbpaF/+gDgDOAZSUdHxM+bu1431I/GO6euYhJwN/CIpKuAuaQxBYD+pOneZ5LuFI/olBZ2nn8FfkvaXfnfJI3MNuvcl6aTZiaTxl66JEl/lf3xw4hY1qmNKeBQqIHszfc20uDyMc1t6FeDDxVaHRFLS/5hVWrTJqTFOA9GRNFt7OvAXdkeVQ8B00l7UPUIknqR1sVsIWmrhu4aSU/RtNvur0jdgZWuM7Sg+JW2ds1FxEOS/ho4m/TLRfnr/BppRtr/6Ul3d9mMrX8g3T0vI01MuUnSieWzFSW93dHta6XXssdFtHJKeUdwKLSDpL7A94CJpC09ToiI1W283B6Symds9WlH8/qTuot+2VyliFgvaTbwRUlb96BxhhHAlsB6Ut/vrVn5XTT9fzGK9CFTlfxvQdmxNF1rMyKbdl3VFvERsZA0dRilbeW3IW0e+XZEvF/NNboTSccD/wFMiohfZWVHkcKxn6RTI+K15q7RBl+VNIg0E6nW9sse2/peUVcOhTaQ9BngFFIYrAdOjojp7bjkNJrvCir/TOxqLAf+AHxd0rSIKBycy950xpCm5PWUQID0+j1B2lplElkoRMSlpZWyO7LDmrlO0fbD5YPEnwY+kn1tQNJA0lThlmylyh9ytaoOb4ydStIA0sye40jjdNc0HIuIxyX9DSnEF0jaKyKW1PDpdyd1L7a0RqhPhbvFimFS4VMouwyHQtsE8BXSby/fj4g3W6gPMD+rv+HFIp4i3Q635F9o/LS6l4FvUGFqaXYHMI40/e5ZSTfQtH96AOk3lomkfvUe0z+djf+MIf1G/3vgKUnfjIiiBYTNiohq9t+fEREXKm1JUrSq/RbaP7X0F2zk07wL9AY+AxxbPt4GEBHPZes6DqhxIED6fz1d0oGkXx4q2YXiu8WNlkOhDSLiFdIH/ABpFSRpAHkUqZ+6H2lWy7ukN+9HgRsi4qTmrpuNA+zcTJWXs3oN/ZBzs+eo1M6Hs9lH3yKtLfkeja/5WtICwpnA1RFRuAVHdyNpK9L4z88j4s6s7ErgSklPRESH/wePiEOaO551762NiO72pt+siHgd+GwLdVYDs8uKH6NgDVEdnE0a1O5WHArtJGlXUtfPFqQ3m6mkgbAPSF0Le5GmqZ4uaVJEXNvM5bal8qKySr7Ahv8pclmXwtnA2dng6i9IgfDldnzM6kZJaQ+pm0hdAhNLDl1Imq3yM0lHZIsrO53SfmADSWMf67J/a69W6grsCbLtPU4CDid18fQlzTx6hzRF92Hg+oi4teJFaiS7S+x2n9TmUGi//0faxG9Iha6EWcBVkn5Imkb3YEQUfoRodn7FTuNSkobT8qrl8uuvl7QOWNcDA2Fr4A7SStMvlva/R8QaSaOBXwGPSzo+Iu6u8rrTSa9ZL+CjpMkBWwMzI+K6NrRTpFW3E9lwquVCUjjMA6bVYCbbRkXSPqTB5V6kmXU/IHXHrQc+Ttpi50RgkqSxEVG4gFRSQ5++SO+Bm5MG86dl12xtu8YCZ0bE0Nae2xU5FNpvX1LXUEu/MdxCWog2lDp+rnQVg5Yt7X0E3XDQkvRmcQBwRMMMllIRsULS50lbvlez99OLpBlGW5LuvD4kdeUtI61Bae0dX4PrsrZOJa0hWUjqChHpjWt34O+B/5A0LCJOb+PzbIxuAt4njSEUbUsxR9JU4E5ghqSHsu1oGjxJ6u5ZT3rN/kKaAbSK9Hf8XBvbNYC0bqglr1Pd2GGncii03zzgCEnfqfAPtcFY0gB1vfusqx20bO5Nq9sNWkbElZL+q7mxk4h4U9Lnq7mLioj7gPtq2cZsvONk0hjPmQVVVpDGpx6VtB74pqRze8I01azrcyhwbXP/zyJiraT/Iq3635WSN+GIeJIUDM09Ty13JC5v222kLuYuzaHQfieSxhSez2b4/Ip0S7uWNEawF2mW0P7A6fXeFrylQcuerJrB9E7uVltD+s11u5YqAttndSsulOxOsq7PZ4DDJU1uZhuZTUg7oa6ijnfk3ZlDoZ0iYpGkPUmfUXAkKSRKZx8tJm0zcWK2KMmsUDa2cRbwQ0k7AP8FLKBxGnJf0uy244DPAac0t3q+GxpP4y9g1wOPk9aZrCf93Qwl/f/bhbTi++2ObFwLXbKl/lTlNPZO4VCogYhYBVybfXWUd0l3JT1pwVm3FxHXSfoVqRtpImnh25bZ4XeAV0hTLr8ZEW3tA98oRcR8SbvTOPvoFJrOPnqRtGX9qIj4fSc0sdpxpMuA8+rZkPZQD5uEYtYqkiYDB0XEl2pwrX6kN/TzI+Ku9l7P6i+b8fQTYGxE/Lqz29MRHApmZparx2c0m5nZRsqhYGZmOYeCmZnlHApmZpZzKJiZWc6hYGZmOYeCmZnlHApmZpb7/6ZnlnP2i1t2AAAAAElFTkSuQmCC"/>


```python
plt.bar(labels,values)
plt.ylim(175,195)
for idx, rect in enumerate(bar):
    plt.text(idx, values[idx]+0.5,values[idx],ha='center',color ='blue')
```

<img src="data:image/png;base64,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"/>

### DF 활용



```python
df =pd.read_csv('score.csv')
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
    </tr>
  </tbody>
</table>
</div>



```python
plt.plot(df.index,df['키'])
plt.xticks(df.index)
plt.show()
```

<img src="data:image/png;base64,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"/>

#### 그리드



```python
plt.plot(df.index,df['영어'])
plt.plot(df.index,df['수학'])
plt.grid(axis='y',color='purple',alpha=0.5,linestyle='--',linewidth=2) 
```

<img src="data:image/png;base64,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"/>

## 누적막대 그래프



```python
plt.bar(df['이름'],df['국어'])
plt.bar(df['이름'],df['영어'],bottom=df['국어'])
plt.bar(df['이름'],df['수학'],bottom=df['국어']+df['영어'])
plt.xticks(rotation=45)
```

<pre>
([0, 1, 2, 3, 4, 5, 6, 7],
 [Text(0, 0, ''),
  Text(0, 0, ''),
  Text(0, 0, ''),
  Text(0, 0, ''),
  Text(0, 0, ''),
  Text(0, 0, ''),
  Text(0, 0, ''),
  Text(0, 0, '')])
</pre>
<img src="data:image/png;base64,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"/>

## 다중 막대 그래프



```python
index = np.arange(df.shape[0])
index
```

<pre>
array([0, 1, 2, 3, 4, 5, 6, 7])
</pre>

```python
plt.figure(figsize=(15,5),dpi=50)
w = 0.25
plt.bar(index-w,df['국어'],width=w,label='국어')
plt.bar(index,df['영어'],width=w,label='이름')
plt.bar(index+w,df['수학'],width=w,label='수학')
plt.xticks(index,df['이름'],rotation=45)
plt.title('성적')
plt.legend(ncol=3)

plt.show()
```

<img src="data:image/png;base64,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"/>

## 원그래프



```python
values = [30,25,20,13,10,2]
labels = ['Pthon','Java','Javascriopt','C#','C/C++','ETC']
plt.pie(values, labels=labels, autopct='%.1f%%')
plt.show()
```

<img src="data:image/png;base64,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"/>


```python

plt.pie(values, labels=labels, autopct='%.1f%%', startangle=90) #스타트위치
plt.show()
```

<img src="data:image/png;base64,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"/>


```python

plt.pie(values, labels=labels, autopct='%.1f%%', startangle=90,counterclock=False) #방향
plt.show()
```

<img src="data:image/png;base64,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"/>


```python
#explode = [0.2,0.1,0,0,0,0]
explode = [0.05] *6
plt.pie(values,labels = labels, explode=explode)
plt.show()
```

<img src="data:image/png;base64,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"/>


```python
#explode = [0.2,0.1,0,0,0,0]
plt.title('언어별 선호도')
explode = [0.05] *6
plt.pie(values,labels = labels, explode=explode)
plt.legend(loc = (1.2,0.3), title ='언어')
plt.show()
```

<img src="data:image/png;base64,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"/>


```python
colors = ['#ffadad', '#ffd6a5', '#fdffb6', '#caffbf', '#9bf6ff', '#a0c4ff']
plt.pie(values,labels = labels, explode=explode, autopct='%.1f%%',colors=colors)
plt.show()
```

<img src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAUIAAADnCAYAAABrC191AAAAOXRFWHRTb2Z0d2FyZQBNYXRwbG90bGliIHZlcnNpb24zLjUuMiwgaHR0cHM6Ly9tYXRwbG90bGliLm9yZy8qNh9FAAAACXBIWXMAAAsTAAALEwEAmpwYAABR0klEQVR4nO2dd3iTVRuH79OWEWaBsvem4GBVRFZRQMoQLEMoCKhFUEREUBQREMUFInwylCFDiYIQFcGylDIFi4AgBJCNlL1H6cr5/jjpTAJJOtJx7uvK1eY9433SJr+c8ZznEVJKNBqNJjfj5WkDNBqNxtNoIdRoNLkeLYQajSbXo4VQo9HkerQQajSaXI8WQo1Gk+vRQqjRaHI9Wgg1Gk2uRwuhRqPJ9Wgh1Gg0uR4thBqNJtejhVCj0eR6tBBqNJpcjxZCjUaT69FCqNFocj1aCDUaTa5HC6FGo8n1aCHUaDS5Hi2EGo0m16OFUKPR5Hq0EGo0mlyPFkKNRpPr0UKo0WhyPT6eNkCTizGZDEBJwC/ZozgggTv3edwGrhMcrBNza9KM0AneNRmGyVQYaAg0Ah4CyqLELkH8DGm8QxRwHDgCHLU+zMBegoMvpbHvbIUQIhDYAPSQUi7zrDXZDz0i1KQPJlNRlOglCF8joCYgMvCuBqCu9ZHannPAXuvjD2A9wcE3MtAWtxFCVEEJenJuALuB6amFTQiRF4iTUloyx8KcjxZCjXuYTMWADtbHI0B1Mlb0XKWM9dHO+jwOk+kPYLX1sTsLTquXoGzLA1QCngF+EEJMkFKOAxBC9AWmAzWAXDXqzUi0EGqcx2QqC4QAnYFmZK/3jw/QwvqYCJzHZFqDEp61BAdf9qRxVnZKKRckPBFCTADWA+8IIRZJKY+iBLCoh+zLsWSnN7LG89QEJnvaiHSiNNDP+rBgMkUAi4GFWWUKLaWMFUJ8AqwC2qDWQDUZgHaf0SRhNvphNg7GbKzioMYW4HwmWpRZeAFNgP8BkZhMX2EyPexhmxI4Yf1ZQgghgXHW5xeFEFIIsSB1AyFEoBBiqxDijhDivBBimhAin516RYUQE4UQB4UQd4UQV4UQq4UQLezUDRdC/COEKCCEmCqEOCuEiBJCbBFCNEzH1+sRtBDmdszGgpiN/TEbVwNngVlAb7t1g4MtwI+ZaJ0nKAi8COzBZNqGydQXk8lGRDKRStaf/wHPAT9bnw+1Pp+bqn4gsAzYDLyDEtJXgU+TVxJC+KE2kV4HfgeGAZ+h1no3CCF62LHFy3r/usAnwJeo9eF1QoiSbr6+LIF2n8mtmI2VUB+mUMA3Velf+Ic0ttvOZGoDrMtQ27IeF4GvgS8JDj6R3p0n2zV+Q0o5OVXZKpS4VZVSXhBCjEeNCktKKS8lqxeIcp+5CzSSUh6wXs8LHEAtBRSTUsZZrxuBnkBzKeX2ZP0URAlkJaCSlPKG9Xo40AqYK6UcmKz+QGA28LqU8vN0+YN4AD0izG2YjY9hNi4FjgEjsRVBgEb3mB6HA1cyxLasS0lgFHAUk2kZJlPNDLpPYSFEGSFENSHEk0KIX1G78sOllBec7OPrBBEEkFLGoHajCwFVIXE02BNYmFwErfVvo4S2KNA1Vd8SeDvVtW+t1xs4aV+WRAthbsBszIPZGILZuAPYCvQAvO/TKtj+1eA4kqZnuQ0voBuwH5NpGiZT8XTufyxqeeIoaje7NhAspZztQh+77Fw7bf1Z2PqzMer/72hkv8X6M/U66X/JR6EAUsoo1IjZ1wUbsxxaCHMyZqMXZmMoavS3GLWe4yzd7lGW208u5EGtux3BZHodkylvOvU7FwgC2gL+UsrqUkpX12Sv27l21/oz4fNewvrzP3sdSCkvAnEkCWcCjnbTo8jmWpKtjdfcA7OxDepkwhygghs9NMVsLOegbD32P3C5jWKoDYYDmEz3+uJwlkNSytVSyvVSyoPp0J8jbll/lrVXaJ06+wBXM9CGLIUWwpyG2eiP2bgKNe15KA09CRxPj2OAlWnoO6dRHViGybQZk8mVUbc7JOxupuUUT8L0+QkH5Y9Zf+5Iwz2yFVoIcwpmY0nMxpmos7Ud0qnXe41ylqfTPXISzYHtmEzzrAEnMoKEjSp3RvkASClPo9YgXxBCBCQvE0IYgPeAk+SiLzsthNkds1FgNr4C/Au8RPqeFmqB2ejIP2w1KhSWJiUCeB7Yi8lk45icDiRsZMwQQrwshAhxs5/BKOf4jUKIGUKIF4UQo1HLKdWB3tYd51yBFsLsjFrDWw18QcacP/XG1oVCERwcBYRlwD1zClWAcEymT9JxMwUp5W6UE3QlYBJQzc1+TqJ2j+ejzo5PR20ARaD8EP9IF4OzCdqhOrtiNvZAefantwtHatbiH/Kk3RKT6Rng+wy+f05gN9CD4GB9VjiLooUwu2E2FkV9e/fNpDvGAqXxD7HdQTSZCqF8yPJnki3ZmRvA8wQH67XVLIieGmcnzMZWqM2QzBJBUD5zT9ktCQ6+BazNRFuyM0VQO8vTMJnyeNoYTUq0EGYXzMaxqMPxle5XNQPQu8fpx6vAxgw4laJJA3pqnNUxG/MB84A+HrQiGiiJf8hNmxKTyRe4gBo5apznANCO4OAznjZEo0eEWRuz0Q91isOTIgiQD+hotyQ4+BpqpKpxjbrA1gwM4KBxAS2EWRWzsTawHeWkmxXofo+y3H722F0qA1swmbJ15JacgBbCrIjZ2BoVE666p01JRhBmYwEHZT8B8ZloS06iFMrfsKWnDcnNaCHMapiN/YA1qAP9WYkCQHu7JSqH8KZMtSZnUQRYjcnUydOG5Fa0EGYlzMbngAVk3Y0HvXuccRiAHzGZnvW0IbkRLYRZBbOxFyoeXVbKDZyaTpiNjo6L/UhSZBSNe/gACzGZ+nvakNyGFsKsgNnYFfiGrP//KEJSwvSUBAdHotY1NWlDAHMwmQI9bUhuIqt/8HI+ZmMQKqdEdskxrSNXZzx5gOWYTLU8bUhuQQuhJzEbHwdMQLpFJ8kEnsJsdCTapky1JGdTHFiFyVTivjU1aUYLoacwGx8DVpD9AhYUB1rbLQkOPgnszFRrcjY1gJ/SM4yXxj5aCD2B2VgZlQmuoKdNcRO9e5x5NEflVNZkIFoIMxuzMT9KLPw8bUoaeBqz0dF7Rwth+tMHk2mcp43IyWghzHxmAY08bUQaKQXYD0MfHPwvKlSYJn0Zj8nk6TPnORYthJmJ2fgyMMDTZqQTenqc+czFZKrtaSNyIloIMwuzsSkw1dNmpCPBmI2OnL+1EGYM+YH5mEz6c5vOZIs/qBCiihBCCiFGetoWtzAby6B87LLq0Tl3KA80sVsSHLwfOJTeN4yNi2NGWBiPvvUWfgMGUPTZZ3lk1Ci+CQ/HXlzN+b//Tv0RIzD07k3ZF17glTlzuBkV5dS9Dpw+TZePP6Z4//4U7tOHJ8aPZ8fhwzb1jJs3U2foUAy9e/Pg8OGYtm+3qWOxWAh4802GzJnj+ou2pSkqeZMmHckWQpitUZsKS4FynjYlA8jU6fGZK1cY+/33NK5enfE9e/JOt274eHvT74svGL14cYq645cs4fkZM6hVtixT+vene9OmfLVuHU++/z5x8fcOlPPPqVM0eestDp45w+jgYMb26MGx8+dpNXYsu44dS6y3+cAB+kydSqPq1Zncrx+1ypal++TJRBw5kqK/WWvWcPryZSaGuJt504b3MZnqpFdnmmwSoVoIUQU4DrwhpZzsYXNcw2x8Dfjc02ZkEMfxD7GfTtJkagj8lZ43uxsTQ1x8PIUMhsRrFouFx0aPZu/Jk9z49lt8vL05+N9/1Bs+nGEdOjDluecS6365Zg0vzZ7N/CFDGPD44w7v02z0aCKvXmXP5MkULag8nCKvXOGB4cN5qHJlwidMAKDbp5/i4+3NkhEjEtu2HDOGuhUr8uWgQQCcv3aN2kOHMmPgQPq0TNdIWzuAZgQH6/Bn6YAeEWYkyl/wA0+bkYFUxWxsaLckOHgX6ssr3cifN28KEQTw8vKiWZ06RMfFEW+xADBn/Xry+vgwtmfPFHUHtmlDGV9fFm/e7PAe+06eZNuhQ4zq2jVRBAHKFS/OC48/zsb9+zlz+TIAhyIjaVWvXor2TWvX5tTFi4nPRyxcSMNq1dJbBEEtS4y4by2NU2RLIRSKjkKIX4UQp4QQt4UQe4QQ/ZLV6WJdVxzooI/tQoh91t/zCyEGCyG2CSEuCiGuCiE2CCHsr4E5z1dkX6dpZ/Ho7rGUkj+PHKFJzZrky6OWYNfv3cujNWviWzDln97b25vWDzzAtkOH7K4pJrQFCGpgGzS67cMPA7D14EEAihUqlEL0AE5cuECFEupU3IZ9+/hh2zZmDrT7FkwPJmAy+WdU57mJbCmEqMjNv6DCPk0D3kYlGFoohEj4YIYBV7ETYl4IURX1jbrQeqkv8BlqgX888AlQG9gghKjgloVm47OA/cToOYtMFcKY2FjOXb3K4chIwnbtosvHH3Py4kVmDx4MqKnyochI6lasaLd97fLluRMdzblr1+yWm//7j4L581O5VCnbtuXUMu/R8+cB6NCwITPXrOH7LVs4du4cs9euxbRjB72bNycmNpaX58xh5FNPUaeCe28hJ8gHLMBk8s6oG+QWskvEk9TcAJpLKbclXBBCzAVOAq8Ay6WUMUKIH4DnhBDFpJTJE5T3QoWW/9b6fC9QS0p5Jll/vwF/Ai8A77lkndlYkpy7Lpia2piN9fAP2W+nbAdwBrXDnC5sO3SI1uOSDlk09/dn3dix1C6vbnH19m2iY2Mp4+trt32pIkVUvVu3KFvMNgj42atXKV20qP221utXb90CYHinTuw8coTen6t/tbeXF+/26EHrBx/kw+XLiY6NZUz3e6V6SRceAYYD2WvtPIuRLYVQSnkBlUIy+bU7Qog/gORrVouBF4EuqMjPCfQC1kgpz1nb/mnnHhFCiJuAO1nGpgK5KWpId8BWCIODJSaTCRiaXjd6qHJlwsaM4W5MDEfOneO7LVt4eMQIvho0iP6tWxMVEwOQOE1OTcL1mLg4u+VRMTFOt82fNy/L33yT4+fPc/LiReqUL0+ZYsU4ceECE5cvZ+mIEcRbLLw4axamHTuIt1jo3Lgx00NDKVLAUfoXtxiDyfQ1wcFX0rPT3ES2FEIAIYQPanrbHKhlfdQnZYTnzcAp1Ad1gbWdP/AQqTYxhBCFgEAgwNpXTVSeDl+XDDMb2wPp5ieRTeiG41HzctJRCIsXLkz7ZOt3I556ir7TpvHil1/SrE4dCuVXwXwcucgkiJghr/2ALj7e3i63rVq6NFVLl058/uq8eTxZvz4dGzXi2WnT+PvECb4dNgwpJcPnz+fVefNYMDTd/iQARYG3gDfTs9PcRHZZI0wQNwuAEKIOsAeVMKgvUBjYBpiTN5JqRfw7oK0Qooj1cm/U2uGKxM6F6IKaVi9DRWCOBVYB112y0mz0Bqa41CZn8CBmo6OR82bgfEbdWAjBe888Q0xcHCsiIihqHWldsU5fU3P5pspRX7JIEbvlvgUL3rdtKQdTZ4Cf//yT3//5h2nPP8+pixcxbtnC96+/TvsGDQhq2JCvBg/m202buHHnjtOv0UmGYjJl2GJkTie7CGHCYs5N68+FqNFaLSnlg1LKnlLKUcARO20XowKfdrY+7wV8L6WMBhBClEKFyd8KlJZSNpVS9pNSjkNtwLhCPyC37uLZ3zQJDrag0n1mGOWLFwcg8upVDPnyUaFECQ5HRtqteygyktK+vhQvXNhuec2yZbl88yZXbt60KTtk7dPfwebHnehoXp03j3E9elDRz4/9p0/jW6BAio2bxtWrE2+xcOx8un835Edt9GncILsIYYLT7mEhRGHUAvFiKeXRVPXqpm4opdwH7AO6CyEaoaa8C5JVaYIaUU6TUiaOAIUQxYCyTltoNuYjd78RPeZGc/CM2uOqUrIkAC38/dlsNnPXul6YQHx8PL/v20ebhx5y2FcLf/U9tvbvv23K1v39N/ny5KF5HfuHOiYsXUqRAgUY3ll950bFxCT6NiaQsIaZxztDNnoHYDJlpVzY2YbsIoR9gSuo5EDxqClyiq9lIURP4GEH7RejXFmCAXOqzZFY68/UX/MTXbTxJaCSi21yEo2tDuT22ID6/6WJ1bt3E5tqkyMmNpZR335LgXz56Na0KQADWrfm2u3bfL5yZYq6c9av58yVKwxu1y5F+8vJRn+tH3iASn5+fGQypRDSyCtXmL1uHX1btrRx6gZ1NvnzlSuZ9eKL+FhFrna5cly/c4fNBw4k1vt11y4K5s9PjbLOf8e6gDfKlUzjIln2iJ0QYjhqatoSeAZ4WUo5y1q2AugEzAN2Aw1QU9+9wGNSykKp+qoEnEDtNH8upfwkWVlh1NpiIeAL4BLQAZVntirwt5Ty3om3VbDV40CZtLzmHMAI/EPsr5GaTPNJYwiyrh9/zN8nT9KrWTOqlCpF5JUrfLdlC8cvXGDh0KGEtEgKkdh90iRMO3YwoHVrHqlRg70nTzJ73ToGtmnDLOvxN4CgDz5g4/79mKdNS/Qd/CUigi6ffEL9KlXoHxhIVEwMs9asASDi00/trhEGjh1LtdKl+XrIkBTX24wfz96TJ3m9c2eiYmL47JdfeKNLF8alOvWSjsQC1QkOPp1RN8iJZGUhXITa7Y0EJkspv0xWVhzl9NwRlWJyGzAMGAV0Ty2E1jYbUTvMFaWUkanK6qEcqh9FjTh/RB1f+hv4xwkhfAUlormdbfiHNLNbYjJ1QjnBu83mAweYvGIFu44d4/z16/gWKECrevV46+mnaVQ95YwwJjaWCT/8wKKNG7lw/TrVSpdmUNu2vNqxI0IkORa8MGMG6/buZWcqgQvbtYvxS5ey9+RJihgMBDVowMd9+1LGju/hovBwhs+fz6EvvsAv1SbMuatXGfzVV6z9+28K5c/PC088wQe9e+OdMVPjBGYQHPxKRt4gp5FlhTDboBKeH8V2ap0bkUAF/ENsdypUAqKLqC8uTcZyF6hCcHCG7dbnNLLLGmFW5lm0CCYggKftlgQHxwAr7ZZp0pv8KA8GjZNoIUw7gz1tQBZDh/DPGmghdAEthGnBbHwYaOxpM7IYLa1nre2xGkh3T2KNXR7AZLINoaOxixbCtBHqaQOyIN5AV7slwcF3UFGBNJmDHhU6iRZCd1EuM06lV9zx9xG6vjIFv8cGke/h/tTpOJJJ81ZiSeVsG9j/A0TdPnYfJ85cdNB7EmfOX6HvmzMp2WwwBRo+R9Pe4wjbtMem3tqte2nY7R3y1x9A7Q4jmfX9erv9Bb/6OR0HT3LmJabmXtPjZe50qHGLEEymbBtPIDPRfyT36UbS0T+HbNt9mFb9P6BR3SqMeqEzPj7e/BK+izc/+w7zsUi+nvhiivp+xQozaWRvm378fO0fCUvg7MWrBPR8FyEEw559ksIFDcxbHk7HlyazYsbrdApUQXmOnjpP55c/o03TB3g+uBW7zScY8v4CShYrTPcnk+LQrtq4m9Vb9rJ/xSeObnkvHsds9MU/5JqdslUo/9B87nSscYlSQHv0JtV90ULoPk5Niy9cvsEXo/sxuFebxGvD+wfRa8QXzP9xI8P7t+fBWkkHUsqXKsaAp1u5bMzIT43cuRvD3h8/olI5PwBeCA6kfvBoXvvoW4Ja1Mfb24uZ362jgX9lVn35RmLb2Lh45i4PTxTCqLsxDJ24kHde7ELVCrYBSp0gD/AUsMimJDj4JibTWpLOfmsyln5oIbwvemrsDmZjDcAptercumEKEUxgSO+2APyxJ2WciOK+Nr7g9+Xq9dssWb2dwc88kSiCAIUK5md4//YcPX2e7X//C8ChE2dp2TjlWdmm9WtyKvJS4vOJX/1E3jw+vPH8vf3I78O9IpLq3ePM4ylMJl9PG5HV0ULoHv1JGffQId7e9v/ExYqqfBoiVS/Firie4iQ84gDx8RaCWtgetW772IMAbN19OLH/U2cvp6hz4sxFKpRREVwOHY9k0termPnuc+TNm6YJQzvMRkfz+RUknfHWZCz5UEdUNfdAC6F7dExrB7sOnACgVpWUh++LFDRw5dotbtxy3svEfFQd5Khb3TYifvWKpfHx8eboKRXQu0PL+ixb+yezvl/P0VPnWRq2nVnfryek42MADHl/Ad3bPcLjj9az6ctF8uHo7xQcfBUViEGTOWTYweacgl4jdBWzsTQqErbb3L5zl0/m/kK1iqVo0ah2irIFP21iwU+bAChdoih9Ozdj/JBuFCqY32F/Zy9ew8tLULK47ek1b28vihctyNUbtwHo3fExtuw6xMsT5ifWCe0eSP+uLTGu3MrO/cc5uNKtnWJ7dAO+d1CWEARXk/E0xWTKaz3do7GDFkLXeRInp8X2uHX7Lj2GT+PwyXOs/upNvLySBuUjn+vAoJ6PU6hAfiIvXOXXTXv4bMGvbPrrIJu/GUu+vPZzaURFxzgsA5VrIyY2KXzVjHef451BXTl84ixVy5ekcvmSXL95hxGfGpk4rAd+xQrz1pTvWfTzZm7duUvrR+oyc+xzlC9d3NWXG4TZaMA/JMpO2U/ALJTfoSZjMaAc/7fdr2JuRU+NXae9uw0PHY+kSa+xbPrrED9MeZUnmj6QorxTYEN6d3yMzq0bMuiZJ/h5xgg+fr0XEfuOMd+00WG/Pt5exMXZz7MBEBMbhyF/yjwb5UoVI/CRulQurw6BjJn2A+VLF+OlXm14b6YJ48ptTB8zgJ+nv87FqzfpO2qmOy+5II7+XsHBF1Fh/DWZQ4v7V8m9aCF0BbPRC2jrTtPla/+kcY93kVKy/bvxdG3j3Mm8kc91JH++PPy23V62TIVvkYLExsVz6/ZdmzIpJVdv3KaUnWlzArsOHOerpb/x5bjniY2L5/OFYXw57nmC2wbQukk9jJOGEP6nmf3//ueUzanQu8dZg5aeNiAro4XQNRoDfvetlYr5po30fP1/dG7dgJ0/fJDCb/B+eHt7UbpEUW7ctje7VNSsrOLBHj551qbs+H8XiYmNw79aObttLRYLL703n4E9WtP4gWocO32B21HRtGictHZZpXxJ/IoV5t+T55y2OxmdrKHK7GFChe7SZDzNMJn0590B+g/jGi5Pi/cdPsWg8fMY0LUliz8dQgGDawcqrt24zelzl6lczrH+Jmy4rN26z6Zs3TZ1rU2qaXgCs5f+zsnIS0wcpjYWo6LVenpcXMrjf3ejY8mTx63lvCI4GkUHB0cC293pVOMyRVFpbDV20ELoGi7vck5dtJqCBfIxfcyAFJGRU3Pl2i2bqW18vIWhExdisUh6BTVNvG6xWLhwOSnTaK0qZWlavyb/+3YNl68l5d+4dfsuk+ev4olH61Gjsm0WgQuXrzN66lI+e7MPvlb/xeoVS+Pt7cXKjbsS623aaebO3WgerFnRpg8n0WePswZ6ndABetfYWdT6YENXm/21/zglihZmSdgfdsv9ihWmU2BD9h4+Rbdh03gm6FHqVi/Pleu3MK2L4O9Dpxj2bPsUfn1D3l/AnGUb2PzNWJrWV+mE/ze6H837TqDJM+MY1PNxfHy8mbtsA5eu3WTlrJF27/3G5O+o71+ZPp2TousXLVyA555uyUvvzeffk+cpkD8vUxaG0e+pFilOrbhIF8xGH/xD4uyUmVBpEjQZT0t0Sgm7aCF0nhooNwSXuH4rihNnLvLcO7PtljeqV5VOgQ2pUak0zRvWYtnaP7ly/RYFDfloWLcKS6e8So/2TVK0KVvSF9/CBShSMMmcxg9UY+PCMbw9dQnvzTSRN48PrZvU5acvXqdmFdvR4KadZpaEbWeP6UObss9HPUtsXDxTF4Xh5eVFz/ZNmPrWs66+9OQUB1oD62xKgoNPYDL9BTRKyw00TqFHhA7QOUucxWzshp7GpYWv8A+xH83bZHobsFVkTUZQSWe4s0WvETqPXmhOG12tywv20G40mYej3NO5Gi2EzvOgpw3I5pRGpVO1JTj4MPBPplqTe9FCaActhM6jR4RpR+8eex7nnVhzEVoIncFsLAhU87QZOYBgzEZHPkR6epw5aCG0gxZC53iANARa0CRSAWhityQ4+B/gcKZakzvRU2M7aCF0jqqeNiAHofMeexY9IrSDFkLncJSnV+M6Wgg9ixZCO2ghdA4thOlHVcxG+4nHg4P/Ao5nrjm5jsKYTPfNvpjb0ELoHG6fLdPY5V6jQlOmWZF70aPCVGghdA4thOmLjlHoWezHZMvFaCF0Di2E6UttzEZH2aG2A2cy05hciGux4HIBWgidQwth+mN/ehwcLIEfM9eUXIejQLm5Fi2EzqGFMP3Ru8eew3Gmr1yKDsPlHL6eNiAH8hBmYw38Q47YKdsEXABKZbJNdtlx+DAfmUxsOXiQm1FRVC1ViheeeIIRTz2VIguhPc5cvsyob79lzZ493L57l4erVGFsjx4ENUwZ2nLtnj289e23HPjvPyqXLMlrHTvyUnvbgOjBn35KdGwsq955Jy0vSQthKrQQOoeOVZYxdAc+trkaHGzBZBpFGvNHpwffb9lSts/Uqd2rlCp1odujjx7x8fKybNi/v9qb33xTIWz37gO/v/eebYxFKwf++6/AY2+/HQLQ9ZFH9hY2GGJ+3LGjXseJE/2mPv/8ilc7djwO8MehQ0U7TJz47IOVKp0e3K7diX2nTpUcMmdOvRtRUatGPf104hfFF7/+WmXlzp0dt0yc+A1wIw0v62Aa2uZIdDxCZzAbr6Nyb2jSl534hwR42oh7IYToCpSRUn6Z6vr3wDPAQ1JK22Qxqs5ioKO1zinrtULAHmuV2lLKeCHEZ0AzKeWjydouAkpJKdtbnxuA/cA8KeXEdHyJGvQaobPEetqAHMY5VHL3UZ42xAl+SS2CVmZYfza1U4YQohhKKL9MEEEAKeUt4HOgOpAgfLVRywHJ+YOU/n7vADHAJFdfQHoghKgihJD3eAy4T3nCY0GqfgsLIUYJIbYJIS4JIaKFEOeEEJuFEGkKi+4KemrsHFoI085plLP0MmAb/iGW+9TPEkgp4x0UXU2o4qA8EPAGwuyUJUynmwFbrX2ldnKuAvwHIISoDbwBBEkpY5yxOwNZAqy2c3098Fyy534o0U5dP3GqL4Rojno/FAFWWH+PAioCrYBg4Jt0tN0hWgidQwuhexxF7QAvByLwD3F5HWbhVgwoUahq/VkF5RDs0dlM90EfVl321WhenrDkmYVbaZ26/PGnX677+48zmbzsxKsLtzIoedm88Bgx8HGDfKhph4ELt1L/mSGTKi+dOarpU/3HVGvU6ulzh/7eXDxPPkOTp/q9s3PhVoyVatZ/vFCREmffnLY+dOFWQtPxZYzq3wxXw/bvlFIucFCWeF0IUQUlhHbrCyGaoMRzD9Az+ag5WZ0SLtrmNloInUMLofOYUcK3DP+Qv9PS0dwovGhIdKgBs7VfABZuJS8qnFQVUgpkwu+lycCwadFRt9m25ltKlqtG48DuT9irI7y8EF5e+JWpHJy6zNsnD4WKliBP3vw1gBpBvUdyMfI4vyyaGPDLIrX817JzKJ36jX70j7XGRy+ePc7rk8Mg/UNoeWStUQiRF/geNeJtK6W8aa+elPJyZtmkhdA5tBDemz0kjPz8Q8z3qesKEpgyN4pOwAnr4zgNE3//B1gfakg5PV24lfwkiWMVbMXS7SAad+/cYsa7PTh/+jAjPlvt0H0mNjqKPHkcH+DwyZOPuLikWW6/ETPo3P8dzp06TMlyVfErU5k7t67z/YwRdBs4kcJF/Vg66y22rV7E3ahb+DdsTb8RMylWsry7LwXA0bQ/o3kW9b/o4kgEMxsthM5hLx9vbudPksTvqLudWAirAUR5EWRzrM4qcMPnRnEXeMtBF3fnRnEKFbXmBCmFcleowXY9a+FWCuB4NFkFsDslO3vqEF+MDubSuRO8/P4P1G1sdzAIgJe3D/Hxjt82cXEx5M2bMjtsMb9yFPNLOga8fM4YivmV5/GnX+LHeePYvs5I39enU7BwMZbPfoevJvTlrS82OLyHE0SnpXEaeBq4DKz00P1t0ELoHFc8bUAWwAJsQy1om/APcTslpIWwuqiTJd1RuWC6kux8cQThnYCjAQSaAUINvD03imvY8zmE/EAt68OGuVHcAU6SJJQnaJj4+45QA6tSt1m4lcKkEsfff5zZ7PsZbzQuXqoi73613ati9Xvn8ipQyJf4uFju3rlF/gKFUpRJKblz8ypFijn2Fz9xaBfhP3/FmC+3ER8Xy9qln/PyhKU83LQDAIPGGXmjR1XOHNtP+WqOjm3fF3d8EQsLIVInyr4rpbzmQh8NUWuHWWbDTAuhc+TWPLDxQDhq5Pcj/iHn3O3IQlgDlPh1A+rcp3oFYH4E4U8GELgLINTAJ3OjuI5yW3Flo6QA4G992DA3ipsooTxBglg2TPx9c6iBFUKI54BhwJJzpw6FVqz+YF4cT7urAIVLV6wJwLnTh6lSO+UpkouRx4mLjaFsFbsmYbFYWDT5JVp1HkjVOo2JPGEmOuo2tR5Oys9esmwVCvv6ce6/f9MihO5MS8daH8n5GfVl5iwlgEtu3DvD0ELoHDY7WjmYGOA31MjvZ/xD3FqwthAmgEdIEj9Xk1/5ARsiCO8UQOBmgFADX86N4gawkPR77xZG5aR5wF7huB17bnr5+BR6oF3Q6SFLf7rg5eU1MDZpvfL3UIPtqGrhVorfunapFWBatfiTX4dMWHKcZGuW+yPWFQSo17iNXYPCV8zm0vmTjJiyBoCY6CgALHEpp9qx0Xfx9nH7tNyd/s1wxxVnLrZnwc+72Ec06gsqy6CF0DlyuhDeRfl6LQd+wT/kujudWAjzQuUu7obyAauQRruKAGsiCA8OIHA1QKgBo1UMf0BNizOU32Z+UTh/oUIM+mZJJS8vr2Gpy+dGcRU4YYmPP37x+NHzpWvUOkBDTrRrOOrfZXPe2RHx+9IGA35f2i9hB1QIUcjLy3tvwcLFL5WuUGMyqUaV16+cr7L8q9H5+wz/goKFfQEoVb46Xt7e7Nm2kmbtlY/xoT2biI6+Q8Vqbqfbdne555CU0p4foSucAuqmsY90RQuhc+REIbwF/IoSv1X4h9x2pxMLYT4o5+FuqEXw0ulloBUDsCKC8D4BBP4AEGpg5dwoOqCccAvds3UaObn7LwoWL0HEsiV2ywuV8Cv2cIdOxYzDX2mwef4c3ly/mepN1GGT0eHb+aRNcwqXLHWm7dDhh2Kioi4XLF6izt0bNwq3fPHFIbENCQ81EJW8PyHKLMyTN3/1x9r1GYlVIAsUKlqlQbOnOi6cNLjcuVOHLPkMhbzXLJlCs/b9KFHG7WDTnpyabgBeEULUk1Lu96AdiWghdI6cIoTXUeKxHFiDf8hddzqxEJYXaIsSv6dwsMuajuQBvosgvHAAgV8DhBrYMDeKJ1AnN4pn1I2jblzn8skTLBj0nN3yyg0a8XCHThQtU5YCvr7kL5x0JL1Ko8a8sWYjpnFv59s8f85D3nnzUqdla4Lf/5jSNWr+CjA3ivNYp9pbv5kfJ7y9n3nms6mDYxtyBdgdalA7uwM2/VgImP7LoonBQgjpV6ZKeLeBH/wElCflGmVFnIsu859bf5D0YRYwBJgMBHnQjkR00AVnMBuLAtc8bYabXEItZi8HfsM/xK0jWhbCDEB7lPh1Aoqmm4XQ1YugnxOeRBA+GPVhSY0ERgQQ+HnChblRPACsBcqmoz1ZBYk6l53kGpTcnxJOhRpS+rgu3IoXShwduQZVRB39m9m/GUOcNcR6UuQ48IaUcnJa6wshPkadNf8aeEVKmWpkLARQQ0r5r7M2pgU9InQG/5DrmI03yD4RaM6hojwvAzbiH+KW46yFsEKo6CndUd/cBdPNQvcQwJQIwn0DCBwHEGrgn7lRtEAd16riSeMyAIES+LLAY3bKLXOjiMS+a9AJYFuoIaUP7MKt+KDWbt31jW0shBhg5/qfUsoDLvQzGrVhMhRoL4T4ATiEWvetjHq/mXFtN9pttBA6zzGyQHy8e3AKFdRgOWkIamAhzBc13e0GtCMTNiTcYGwE4UWB4QEEylADR+dG0RwVzMC+T0rOxAslahWAFnbK4+dG8R/2XYO2unnPZ6yP1AwHnBZCqw/hq0KIpcDLqM210sBtIBLluTDPTRtdRguh80SQ9YQwIajBMvxDItztxEKYH+qbtzvwONkjgvEwoEgE4QMDCIwPNXBmbhQtUbvfjTxsW1bBGzW6qoyK5pJALGoTymmklCdw4fy2s/WllFuALa7YkhFoIXSe7cBATxuB+tZNONrmdlADC2FlUd/C3YCWqA9NduM5lBiGBBAYE2rg0twoHkcd3bI3QtIoToYaPHbOOEuiA7M6z3YP3nsP8C7gj39IPfxDxrojghbCKlkIG24hbCvqSNt0oDXZUwQT6Ab8EkF4AQCrg/OT2I8DaJdtixfxemXHx922LprPe03q83JxAyOrlsU4/BXu3nTuUEak+QDTe3RhWPnivFKqMJ91eIJjf+6wqbdjiZF369fh5eIGxgc8yK6fbPPcWywWPmgewOLXnN7jcIS9PDG5Gi2EzmNGuZ9kBhIV1OBNoAb+IQ3wD/kA/xCXc01YCKthIewtC2ERqKNkU1AL7xkWpsoDtAPWWtcNsfrmdQGW3qvRyV1/8Xnndswf2J+YO3fs1lnxwXgWDH6e0jVr0fPjKTR8ujub5n3F1KeeJD7u3vsNZ/b/w4etmnDu8EE6vDGazm+P5eLxY0x6shUnd+9KrHd462bmPteHSg0a0ePDyZSuUYsv+3Tn+M6Uqx0bZ8/i6n+neXp8mqNnpWeEoByBdp9xBbNxLcp/LiOwoBawl5P2oAb1SDra9lD6mJehOOs+cz92A08GEHgRrPEM4SuwDWY6qV0rDm/ZRNHSZShathzn/z3E9Iu3UtQ5e+gg4xrV44khw3jmkymJ18PnfMniYS8x4Kv5NHt2gENjPn68GdfORjJ2+x4KFFXeRtciIxkX8AAVHniIN9aEAzCrdze8fHwY9E2S0/anbVtStk5dnv1CZQm4cf48Y+rXJuTzGTzaq48bf5oUhIQa+C6tneQk9IjQNdJ7ehyH2h17CSiPf0hL/EOmuSOCFsIaWAibaCHsICpO33tkDxFMTxoAmyMIrwAQasASamAgahScghsXL9Dp7bG8//chyj9g/5ja5vlz8Mmbl85vp4wx0PL5gRQtXYYdSxY7NOS/f/ZxdPs22r8+KlEEAXzLlaN5/xc4vHkjV8+ogDvn/j1EreatUrSv1qQpV04n+fEvfXsEleo3TA8RBLXxp0mG3ixxjfQQwhiUz9ty0h7UoAlJI7+q6WBbTqA2sCWC8LYBBP4LEGpghDWM14SEShN2HUD57DrGvGE91R55lAK+vimue3l7U7tVa/as/Bkppd1+zBvWA/Dgk7YHJ+o+3pa1UydzZPtWArr1pIBvMa78l/Lw0uWTJyhWXh3VPrhxA3+ZfmDsjjQF/E7gaqhBrxGmRguha2xHrd+5ur4WBawh/YIadEed601rUIOcSmXUyLBdAIF7AUINvG8N4zWVxIMLjrFYLJw7fIjm/V+wW166Zm1i7tzh+rlz+Ja1PdRy9qCZfAULUqKSbXT9MrVqA3DxmIpn++CTHQib/BEVH6pP1caPYP59Pbt/NvHaL2uJi4lh8Wsv027YSMrWvl/0MqfYmR6d5DS0ELqCf8gVzMZdOOendgtYhRK/X9MY1KA1atTXlfQPapBTKQ2ERxDeIYDA7QChBv5nFcN53Gen/M7Vq8RFR1O0dOoYpIoiJdUu851rV+0K4fVzZylSyv6/qnCytgBthw7n5K6dzOnfG1Ajzo5vvUudVq1Z9emHxEVH0/GtMfd/xc6hhdAOWghd52ccC+E14BfSN6hBFzIwqEAOpxiwPoLwLgEE/gYQamChNRjrd0BeRw1jotTRV5989vOOJFyPi7F/dDv2bpTTbfPkz89L3y3n4onjXDl1kjK16lC0TBkunTzBr59OZNA3S7HEx7NoyIvsXmHCEh/PQx06EzJlOoYiLp/61OuDdtBC6DorSLbWhApq8BNJQQ3cSvRkDWoQRFJQg+xyrjmrUxBYFUF4rwACfwIINWCaG0Vn1HlsuwFCvX3UR8ORi0yCiOU12D+g4eXt47BtvIO2JatUpWSVpKXe70e8Sr02T/JQUEfmvfAsp/f9zQvzvkVKydJRw/lu5Ks8P3uB3Xs4IB7Y6EqD3IIWQlfxD/kbs/EPlKvGctIW1KAwKqhBN7JGUIOcSj7ghwjCnw8g8BuAUANr50bRFhWT0SaSjsG603vnqv34pbevqD2uwn72E+IV8PV12PbWZWvbko6duPf88jMHN/7OhN1mLp8+xY4lRsZH7KOcv4pnmrdAAaZ0eILek//nyqhwR6hB59+xhxZCd/APsRcJxCmsQQ26kBTUwHHOR0164gMsjCC8SACBMwBCDWybG0VgfEzsH6QKLpHXYKBY+Qqc//ew3c7O/XuIIqVKU7C4/VWLUtVrErFsCbevXLGpc+7fQwCUrW0/PkT0nTt8N/JVOo8eR/EKFdm3JowCvr6JIghQpWFjLPHxXDx+jEoP13fqDwC2iao0Cu1HmAlYCCtpIWyghbDVwAVgAdAZLYKZjQCmRxA+OuFCqIE9B35fFybtnCyo2awF/27bTOzdlEu9lvh4Dob/jv/j9nOOJLQF2P/bWpsy8+/r8MmXjxqPNbfbduVHEzAUKUKbocMBiI2KwhKfctKRsIbpncel+Bi/ulI5N6GFMIOwEFbOQtgQC2EbgLPAbNQZ2OwQ2SWnMzGC8E8Snty6dPFGTFRUFJAiCOhjfQdw59o11n3xeYrGm76ew7XIM7QKHZx4LS4mJnHKC1C7VWuKV6xE2OSPUgjptchINn09m0d79SV/IdssA5HmA6z/4nP6TJuVuE5ZulZtoq5f5/DWzYn19q35lXwFC1Kqeg1nX/OZUAN7nK2c29BT43TEQlhlkhycm5KzzvPmNN6MINwXdapHJRtWEWvWAA8D1GvTjoZdu/HT+He4cORfqjR+hDP/7GXT17NpFTqYmslGdDN6dOHwlo1M2G2mRKXK+OTJQ8iU6czo2YWPWz9G0779iY2KInzOLPIVLMTT731o16jFr71Mk2f6pOi7fN16+Ld+gi9DutF26OvEREWx7n+f0e61N8jjYGfaDk4HociNaCFMIxbCapIkfo09bI7GNV4EiggvESMtklAD5+dGEYiaQjYFGLjAyC8fTmC7cRE7lhopWbUaPT7+jCdefjVFR0XLlqNQCT/y5E/aCX64Y2eGmlbxy8TxmN59i/xFivBAuyC6TfiYIqVsN0q2LV7Emf37GLx4mU3ZC/O+5dtXB7PyownkK1SIx18aSifXfAtXuFI5t6GDLriJhbCGqLU+t/MpahJJr6AL7rIS6BFA4F2AuVEURLlEOV4EzF5cAMqnDtuvSUKvEbrPKXJXWPicTCcgLILwwgChBm5br/3kSaPSkcVaBO+NFkI38SLoEvC7p+3QpBuBwG8RhJcAsKbR7AF840mj0on5njYgq6OFMG1872kDNOlKALAxgvByANZRVH9UJO/syq5QA/s8bURWRwth2lhK5kWt1mQO9VCRa6oChBqQoQaGAmkOC+0h9GjQCbQQpgEvgm4DizxthybdqYaKaZh4lCPUwBhU6oTsRDRgdKaiEKKwEGKUEGKbEOKSECJaCHFOCLFZCPHsfdruF0IstHP9ISHEl0KIw0KI20KIW0KIE0KIJUKIWm6+pgxBC2HamelpAzQZQjlgUwThiS5RoQYmAYNQaRWyA0ZnzhYLIZqjnMnHoTYBPwReA75GaUTwPdo2A+oCc5JdE0KID1Hn8duhIjK9Ye1/FSprYl3b3jyHFsI04kXQQWBDRt9nx46DPN11AqX8emHI9xR167zI5EnLsFhsP5O//LKDZk1fp3DBpynl14t+z07i3DnnztqfOXOJZ/tOonTJXhQq8DTNmr5OWJht5Ka1a3fRuOFQCuTvgn/tgcyaZf8Ya7fgD+jUcZxrLzbrUAK1gdIy4UKogdlAH1Ru4KyMBCbfr5IQogkqYvoJoI6UspeUcoqUcpaUcrSUshl2cr4kYyBw0JqfOIEpwNuo5YTaUsoRUsqZUsrPpJRDgIpkwmfGFbQQpg8ZOirctu0ALZu/wflzV3lzVHc++vg5ypUrzqg3v2Zg6LQUdRcsWEfXp96jYKH8fDrpBUIHPslPP/5BqxZvcv36vWPDnj17hSYBrxG+YS+vDuvChx/15/btu3TuOJ6VK5NSUB49epYuncdTpmxxJk0OpVnzegwdMpNly1Lm6V616k/WrP6LL6a/lH5/jMynCLA6gvAOCRdCDXyPihAe5TGr7k9YqIED96oghMiL2vD7D2grpTxlr56U0m46CSFEEdTOevLRYDvUaHKSlHKslNLmC0NKGSelzFJr69qhOh2wRpE+iZpOpTs//bSNc+euMnhwxxTXe/f6mKVLNrFn7wwefLAqV67cpFqVAbRp24Aflr2TmEsjLCyCTh3GMXZcCOPG93V4n759PuXXVRHs2TuDSpXUyYdbt6JoWP8VAMyHZuPt7c3IEXPYtvUA27YnncHt328yFy5cJ2z1+wBERUXzYL2XeP6Fdox+p9f9XqKnHaqdIRZ4NoDAxFRzc6NohZr2FfaYVY5pEWpgy70qCCFeAOYCXaSULp88EUK8hEp9UF5Kecl6bTNQA6gipYx22WrVRxXgOFBVSnkio9uBHhGmC14ExQGf37eim3Tu3MRGBAFeHtIJgD/+UOmOjYs3cPNmFB9M7J8ioVBQUACNG9fEuDjc4T2uXr3J0iWbGDS4Q6IIAhQqZOC14V05evQs27er+xw69B8tWj6Qov2jTf05fepC4vMPJ35P3rw+jHyjm+svOGuSBzBGED4w4UKogY3A44BbCbgykI33E0ErT6NsX+nmfUKBn5KJYEmgGfCduyLoKbQQph8zgfMZ0bG3t/30GsWKqeglCaK3fv0eqlQpTZ06FW3qtmnbgCNHIrlw4ZrdvsLD9xEfb6F9kO1x6TZtGwCwbeuBxPueOnUxRZ2TJ85TvoIfoIRy8qTlTJ/5Mnnz5qhgO17A7AjCRyZcCDWwE2gFRHrMKlved7JeQ2CnlNLlzR8hRENr+znJLjdABRr509X+PI0WwnTCi6A7wEeZec9du1QWtFq1ygNw0HwK/7qV7NatVVslvDt69Kzd8oNmlUq5rp321auXxcfHm6NHzwEQ1CGA5cu2MGvWKo4ePcvSpZv4ctYqeocEAjB0yEy6dW/O44/Xd/u1ZXEmRRD+QcKTUAP7UZFrjnvOpER+DzXwm5N1S6BSTbhDKHAMUtyrhPWnS30KIfIKIcokPICEsN8lk18XQninRzt76Ogz6ctXKDeB8hl9o9u37zLpkx+oVq0MLVrUA+Ds2as0b/GA3fqlSqnQ81ev3rJbfvbsFby8vChZ0iZqPd7e3hQvXpirV28C0Lt3IFu37OeVl2ck1nkh9En692+D0biBnTv/5cDBr9x6XUKIfvkM+T7dfGd1iutxsXH8OPsXwr5Zx+kjZ4iLjady7Yr0HPo0QX3b3jdHMcCxAyeY+fYc9mzeR1xsHHUfqcPLH4byQJOUnhyrjeuZN2ER506ep0KN8rz43gBaB7dMUcdisbxTvkbZgZHHzy2TUg4JNXBsbhTNgbUop2xPEI/aqHCWaBzkbLkXQogCQAjwaaqAtgnTYVf7fAz7u8ipR5ZVUbvbaW1ngx4RpiNeBN1F+WBlKLduRdGj+0QOHz7Dl7NfxctL/RujoqLJl8/+VDThekyMfa+Pe7VNaB8Tk3Ruf/qMIZw+8w2/bfiYYyfmM3vOMG7cuMMbI+bywcR++PkV5e235lOhXF98i3Sja5cJnDnjeKAghGgkhFgLLIyLjbPJLnfhzCW+GrsA/8a1GTh+AM+90wdvH2/G9/uImaPnOuw3gaP/HOf5Ji9z4uBpBozuwwtj+3Hm2FkGt3qNg7uSwvHv3ryXsX0mUqdRLV6dPJhKtSrwVvfxHIg4mKK/5bN+5u6d6FK/Ri4rFkG4N0CogUjUNNlTKTPnuXic7hTu+fP1BAqhoi+l7g83+tyLytmT8BhgvT4g1fXUS0/utrNBjwjTn7nAKMD+HDWNHDr0H92DP+DEifMs+eFtnniifmKZj483cXH280gliJjB4CDF5D3aJrRP3bZcuRKUK1ci8fm7YxZRvnwJBr/UkfHjvuU7Yzj/m/4SxYoV4t13FtGv72R+2/CxTd/lyoRMRI2izgG7sDOiKlGmOCtOfk+BQknx/vqOfIbQx17h+2nLGfT+8/j4OJ4BfTToM4r6FWXBnzMpVFStrbbv04beDzzP1Ndn8mX4VAC+n7qMNj0DeX+xivXXY8jTvNhyGD/P+5W6ASrB+uXzV5j1zjzenDEMv7IlegP5IwjvHUBgdKiBy3OjeBy1m9zKoUHpzw3A1eTHG4BXhBD1pJT7XWgXCqySUqZeF92NSmkbDNj+ox0gpbwCJE4BrLu/ABvvtfvrbjt76BFhOuNFUAzKmTTdWb58C480HoaUkm3bp9C1a8ocUr6+hbhy5abdtpcvq+ulSvnaLff1LURsbBy3btm6xkkpuXr1ZuL02h67dh1h9ldhzPzyFWJj45n6+U/M/PIVgoOb0br1w3xrfJPw8L3s33/Spm1UVExRVIrU2mB/RJMvf94UIgjg5eXFQ80eIDY61ianR3KO7DvG3m376Teqd6IIApQs58dTL3Rg18a/uXBGbf6cPHSahq0eTtH+waZ1OZ9sR3zaiFnUbliL9n3aJlx6GlgZQXhBgFADN4H2ZG6ypA9CDVy8f7UUzMJJx+sEhBD+qJ3hOanLpJTxqOWhACHEfX2mshJaCDMAL4KMpHOIrvnz19Kr58d06vwIf+6cxoMPVrWpU7NmOf49fMZu+8OH/sPLyytxYyU1NWoqF8jDdtofP36OmJg46vjb7kYDWCwWhrw0ndCBT9K4cS2OHTvL7dt3E9cuAapUKY2fXxH+/de2/4uXl7wipRwnpbxh9wYOkFKy/8+D1GviT958DnO18+f6vwB4LOgRm7JH2jYC4O+t/wBQuFhhziUTPYCzJ85RyrojvnPDbn77YSOjZr6Wuqs2wDpr+H9CDdxFCWRmRCg6Cky7b61USCkPAJ8C7YUQ84QQNkmarcflaia7FAqcwXHo/4mo43rzhBBP26sghCgqhCjtqr0ZiRbCjONlICY9Otq37zgvDZpO/wFt+HbxmxQokN9uveYt6rF//ykiI23d2tav203TpnUoWNB+2wTRWrd2l03ZunW7AWjTpoHdtrNnh3Hy5EU+mNgfgKgo9bJTT7Xv3o0lTx7b1Zh7TWmTExsTy6VzVzh5+DTbwnYwsssYzp08z+jZI+7Z7oT5JIaC+SlbuYxNWeXaStzPHFWzvGYdmrB85s+s/f53zhyL5MfZv7DBtJl2vZ8gNiaWT1+eSp+RPalSx+7KR1MgPILw0gChBmJRx/FmO/UC3UMCg0INbr/XRgNfAM8DR4QQU4UQLwkhhgshpgIHgUmQeBKlH/C1dfRna4yUN4G2qM0JkzVowztCiBeFEO8KIb5BCWlTN+3NELQQZhBeBB3C+gZKK9Om/kzBgvn5YvpL99wdfbbfEwBMeC9lwJHVq3eyfftBXhyceEoMi8WSwqewVq0KNG3qzxf/W8Hly0kDs1u3opgy2cQTT9SnRg3bgzMXLlxjzOiFTPosFF9fNe2sXr0s3t5erFyZtHm3adM+7tyJ5sEHq7j02pOzd9t+OpTtRo/a/Xitw1vcuHqT6esmUf0B29Fxci6dvULx0vbzDxcrVQyAGwk74sN78EjbRozp/T5PV+/Dpy9P5fkxz9K4dQO+nbyEmOhYnh9zz2AsD6PCeFUCCDVgCTUwiHR6L9hhpgvuMjZIKS1SyldR7j8bUet7U4F3UaPc30jyS+yKcpH5+j59nkT5FL6CClDxOkpsB6F2cMcDm+7R/oSUUri6zuduO9CbJRnNRJSbwb0/qfdh119HKFGiMEuW2H/v+PkVoVOnJtSpU5HXhndlymcmLl68Ttt2DTh+7BwzZ6wkqEMAIVY/P4BXhsxk7pzVbNw8iaZNVcaBqf8bRMvmb9C0yXBeHBSEj4838+au4dKlG6xYOd7uvd98Yx7161ejT5/WideKFi3IgOfaMuSlGRz5N5ICBfLx+ZQfebbf4ylOrbhKjYeqMS3sE6LvxvDfkTOs/e43+jwcyltfvU6n/u0dtouOiiavgx3xhOtx1s2kfPnz8snyCZw5fpZzJ89TuU4l/MoUJ/LEOeZPXMyHS8diibfw4YuT2WDajCXeQvPOTXlj+jAKFSmY0G1NVBivNgEEHgYINfDm3CiuAx/YWuE2R0in0GDWoAn3O40yEFjnjNBIKWOAGdZHlkcLYQbiRVCUhbBXSOOi+fXrtzlx4jwvPGf/FF+jRjXo1KkJAJ9OeoFy5Yrz5axf+XXVn5Qv78fIN7rx9uhnEt1sAMqWLY6vbyGKFEly+WrcuBYbNn7CO28vYMJ7RvLm9SGw9UOYfnqXmjVt1xY3bdrH0iWb2LXHNoDzlM9fJDY2nmlTf8LLy4sePVvw+dQX0/JnoGjxIjRtn7TO12dET8b2nchHL07h4WYPUrGG/fVP73vsiMcmCGCqHfHyVctSvmrZxOefvfoFjz4ZQPOOTRn37If8+/dRJnz7DlJKPh8+g89e/YJxC95K3kVF1MjwyQAC9wCEGphoFcP/kfZUrxagf6iBO2nsxymEEFWBJ1CuMzkOHXQhE7AQ9jXwnKftyMIkBl0QQizw9vHu9UfseqcS9p4+coZuNfsy7LOX6PO6/c/oO70m8Of6v1h36WebsgtnLtKpQk9em/IyIcN72G2/8ectjO0zkaXmhUgp6Vo1BOO+eVSrWwWAXRv3MOSJEay7siL5qDCBa0DHAAK3JVyYG8WzqMjRzi2O2mdSqCHzAsUKIQJQPnkf2Ysok93Ra4SZw1DgkKeNyImULK92cy/Z2SBKoGLNCly/fIPrV2w3pU8eUkcLq/pXttv27p27fPbqdELH9ad0xVIc23+CQr6FEkUQwL9xbeLjLUQes3t80RdYG0F4oq9NqIFvgO4kncRwlX2oNbxMQ0oZIaWckBNFELQQZgrWkP69cP+Nr3HAyYPqMEPZKrY7wgnUb6FST+9Ya3vg4891f5E3Xx4ebm4/PfXcCYsoWKQAva2jxeioaBufxWjrLrl3HocDvIIoP8PESM+hBn5CpQy9d5BIW64CT1uz7GnSCS2EmYQXQXuAt+5XT2OfP1b/SVxsytS8sTGxTB81m/wF8vN4t5Yprl+7nBT3s3HrBpSpVJoFHy0m+m6Sl8nFyEv8OHsl7fu2tXHWBnU2+bvPlzFq1vBEF59KtSty6/ptdm/em1hv66/bMRTM73CN0kpeYGkE4f0TLoQaWI9yNbnq3F8BC9A71MBRJ+trnESvEWYyFsJWArbBBXM3910jHNl1DP/+fZR2vR6nbJXSXIq8zJrvfify+FnGLXyL9iFtEusOCxrFro1/s9S8INF3cPMv2xjZZQy16tegY/92REfFsHyWikW6IGIWxa1uNMkZHPga5auV5d2vR6W4PqTNCI7sPUbI6z2Ijopm8WdL6ftGLwaO62/Thx0k8FoAgf9LuDA3iodQwRru52T8dqjB+aNrGufRI8LM5zmSDqdrnKTPiJ7UfKgaYd+uY/LQL1g+awU1H67O19tnpBBBAL9yJfD1K5piJ7hF58f4fNVH+OTxZsZbc/ju82U0al2fr3fMtCuCqxat4ci+4wz9dLBN2XvfvsODj9Vj7oRFLJ+1gp5Dg3l+jOPI36kQwLQIwhPX+EIN7EX58d3rffGDFsGMQ48IPYCFsAdRPltFPG1LFiE7hOrPCD4LIDAxyOvcKCqiEimlTnW5D2gaanB5PVHjJHpE6AG8CNoHPIOKH6fJvYyIIHxOBOFeAKEGTqNGhnuS1fkP6KhFMGPRQughvAhaDbzqaTs0HicU+C6C8DwAoQYuAK2BbcAVoJ1VIDUZiBZCD+JF0EzUuU5N7qYn8HME4QaAUAPXULvJgaEGzJ40LLeghdDzjAB+8rQRGo8ThMqfXAQg1MAdF6NNa9KAFkIP40WQBbVe6G5KRU3OoSWw1NNG5Ea0EGYBrFGtu6HFMLdzjQyKbq65N1oIswhaDHM9N4AnAwjc7WlDciNaCLMQWgxzLbeADgEEZrvE6DkFLYRZjGRiaPK0LZpMIRJoGUDgVk8bkpvRQpgFsYphd1zILqbJluwDHtXTYc+jhTCL4kWQ9CLoDVSeh7j71ddkO9YCzQMI1M7SWQAthFkcL4Jmo6LVuJTqUpOlmYeKWq3/p1kELYR2EEKUEUKcFUKM87QtAF4ErQUeQ6VI1GRfJDAmgMDQAAL1KD8L4bQQCiGqCCGkEGLk/WtnewoCfqgEPJmKvSTbAF4E7QcaoXeUsyu3gT4BBE70tCEaW/SI0A5SyqNAOcA2GF0GIoT4H+Bw99CLoCvAU8BIIEfmjsih/Ak0CCDwO08borGPFkIHSCkvSikze/ryECqku0OsmyifoabKhzPFKo27xKOSozcLIPBfTxujcYwWwmQIIbyEEGnNN5speBG0E2gAfOVpWzR2OQa0CCBwrF4PzPq4LYRC0VEI8asQ4pQQ4rYQYo8Qol+yOl2s64oDHfSxXQixz/p7fiHEYCHENiHERSHEVSHEBiFEEzvt2gohfhNCXBZC3BJC7BRCPJqqjrcQ4kXrPW4mq9fSWp645imE6CqEOIb6Bq8shPCzlo23c+/WQohV1ntHCyEOCyHeF0IUTFUv0NpHdyFEgBBinRDihhDimhBiuRCierK644UQEmgF1LO2k0KIAff6H3gRdMeLoMGoxNs6XWjWYT7wcACBf3jaEI1zpGVEWB34BbUTNg11WDwaWCiE6GatE4bK0NU9dWMhRFWgCbDQeqkv8BnqAz0e+ASoDWwQQlRI1u5ZlA9WFCq360eow+q1k9XxBpajRkuXgdHABFSgywapTKkD/A8VGn4McMfRCxZCvAL8BpQBPgaGATusr/13IUR+O80CrPYeRK3tzQWeBLYKIcpZ6/yEymVyCDhj/f05VDj/++JF0O+oafUY1N9F4xnOA90CCHw+gMBbnjZG4zw+aWh7A2gupdyWcEEIMRc4CbwCLJdSxgghfgCeE0IUk1ImT1vYCzUC+9b6fC9QS0p5Jll/v6EWml8A3rNeHmat21kmJVyZKITIk6zv14EuwDAp5f+SXf9UCFEg1evoAzwmpUz07hdC+KV+sUKIesDnKPEPllImhNn/UgixDiXoo5LZmcBwoLWUcmuyvlYCG1DiHCql3APssY4A/aSUC1Lf/35YT6NMtBBmBL5AZ8rLTO4CU4CPAwi86WljNK7j9ohQSnkhuQhar90B/gBqJru8GMiDEqbk9ALWSCnPWdv+mVwErdcigJup+hNAvtS2SymT76K+BmxOJYLJbUzOH8lF8B68aP05PJkIJvAN8DdgL5/jd8lF0GpDOGpk+bQT93UJL4KOexHUydq3ni5nLBL1RV4rgMB3tAhmX9K0WSKE8BFCNBNCjBJCzBNCbEblW/BNVm0zKk1h92Tt/FFTuQWp+iskhOgkhHhPCPGdEGInUCBVf4tQ0+AtQogn7dhUHeX68qOTL2OXk/WaAEellMdSF1hHpluBqkKIwqmKt6Wun+y+xYUQJZy8v0t4EfQTUA8lzjohePqzGXgkgMBn9TG57I8rQpiwm2oBEELUQWXb2oRa3yuM+tCnyLFgFYnvgLZCiIT0lb1Ra4crEjsXogtqWr0MaIfyk1sFXE/V3zTUVLkCsFoI8Y8QonOyKglJss85+brOO1mvBCqjmCPOWn+mFsLLDuonZCW7p7tMWvAiKN6LoEWoddBQ9MmU9OAIah2wZQCBOz1tjCZ9cEUIE7JgJwz/F6JGa7WklA9KKXtKKUeh3iipWYz6wCcIVi/geyllNIAQohRqerkVKC2lbCql7CelHIfagEmBlPJroCoQglrnXCGE6GUtvmv9Wd7J1+VsYudbQNl7lJex9nUt1fU8tlUBJeTxqA2cDMWLoDgvguah8uW+BGifNtfZixpd1w0gUIdIy2G4IoTVrD8PW6d/jwCLracwklM3dUMp5T5UyKHuQohGqDW/BcmqNEGNpKZJKRNHgEKIYjgQHyllnJTyO6AxavSXcArEjBLPx114bc6wC6gphKjkoLwp8I+dNcgHUle07mo/AexN+DKwIkkaeac7XgTFehH0JWpp4UngZ3Ru5fuxDhU5+uEAAhcFEJjiRI8QorB1aWibEOKS1aXqnBBis9XDwQZr/d+SPV8phNAh+j2IK0LYFzV6+QP14bGgRjWJCCF6Ag87aL8Y9eELBsxSyuTReBPeXBVStbE5l5laiKSUt1DTZ2F9HmW9V5AQ4ik77YulvuYkc1Cju6lCiBR/NyFEb6AhMN1OuyFCiCqproWiRrRzUl2/ApS1CmWGYT2dstaLoK5WOz7A+aWE3MB1lEuVfwCB7QIIXGuvkhCiOWp0PQ61Dv4haqPua9RnK9hB/01Q3hDJn0eki+Uat7in+4wQYjhqdNUStev7spQyBogRQqwC+gsh4oDdKP+8zqhv0MfsdPcdyufvBZQbSnK2ovznpgkhagCXgA6AAdt1ufVCiN0oH7t4lLjWRrmiJDASeBQwCSGMqLXLEiiXkqW4kUtYSrldCPE+ynfxTyHEd6jpclOUC84P2AobqHXU3UKI2cBxq13PAuuB2anqbkF9eBYIIbYDf0spnfIldBcvgk4D71oIm4D6+3RD/R+LZuR9syAW1N//W2BxAIEO/UkBrI7+61H/355SylN26jjaCGuCWgrC+n4vAej1Rg9yPz/CBqjd3kjgJSnll8nKBqCcnjuiNj+2oXaMR9nrSEp5yrqr3BzrmyBZ2U3rDvBnwFCUwP2Iyvn7d6qu5lrv3Rm14fA30F5KuSZZf1eFEE1RjtQ9UOkyLwEbgV/v85odIqUcK4TYi/JlfA/1rW8GXgW+SubXmJzpQEmUb2Ml4DTq/OnHdtxwZgEPAl1RXwS93bXVVbwIikU5dv9kISwv0AYlil1QH9ScSDRKzH4EVgQQeNGZRkKIvMD3qC/ptlJKu24zUkqbjTLr4YByJI0IHwWOSCmvuWy9Jt0Q9j+7mrQihAhEOU33kFIu86w17mMhzAc1I3gCaIFaG86Xzrfp6kXQzwlPIggfjPpSyAhuoLwRfgTC3DkBIoR4AfWF3EVKucKJ+uW5t8dBcnpJKZe4apMmbaTlZIkmF+BFUBzwu/WBhbB8qKldC5RAPgoUcdiB54lErb9FoI5DbgogMCaNfT6NcotyNjbkXdSRSVAj7Jok5aMZgZpVJMxUNqTRNo0baCHUuIQXQdEo39FNWDezLISVR/kq+lsfCb/fy90oI7iKWmuLQE09IwIIjMyA+zQEdkopLc5Utk6RFwAIIYKBH6WUC4QQApiEOgr6ewbYqXESLYSaNONF0BnUZtdvya9b1xr9Uj1KWn8aUO8/b1TIqnsRh9rJjUz2OJP69wwSPXuUQK05O4XVUyFhOaEZsEgIUQbl1+kLHLc+j5FSZrhfqcYWLYSaDMMaCCJBrFxhLmoEFRtAYFb0c4xGHSZwlnDUkdIEfkhVfizZ9Z7um6VxF71ZotG4iBDiH8BHSlnHyfqtUSPCJqjITAmO1kNQI+OE9cJjUkodddwD6AjVGo3rbABqW0Oz3Rcp5QYp5WrUpsluKeVq6/MiwPqE51oEPYcWQo3GdWahjkNOvl/FVNTH6hdr3SipjzqMoPEwWgg1GheRUh4APgXaW8PP2aRgFYqaqS7XJ+mAQHXUiFALYRZAb5ZoNO4xGrVhMhQliD+gAuHmByoDQSj/wK6QeBolD0nxL2ugXHAuZK7ZGnvozRKNJg1YAy+8jDo6Whp17DMS5Wc5T0r5lwfN0ziJFkKNRpPr0WuEGo0m16OFUKPR5Hq0EGo0mlyPFkKNRpPr0UKo0WhyPVoINRpNrkcLoUajyfVoIdRoNLkeLYQajSbXo4VQo9HkerQQajSaXI8WQo1Gk+vRQqjRaHI9Wgg1Gk2uRwuhRqPJ9Wgh1Gg0uR4thBqNJtfzfweaeGpYTh8uAAAAAElFTkSuQmCC"/>

#### 도넛



```python
wedgeprops = {'width':0.5}
plt.pie(values,labels = labels, explode=explode, autopct='%.1f%%',colors=colors,wedgeprops=wedgeprops)
plt.show()
```

<img src="data:image/png;base64,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"/>


```python
wedgeprops = {'width':0.5,'edgecolor':'w','linewidth':2}
plt.pie(values,labels = labels,  autopct='%.1f%%',colors=colors,wedgeprops=wedgeprops)
plt.show()
```

<img src="data:image/png;base64,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"/>


```python
def custom_autopct(pct):
    return f'{pct:.1f}%' if pct >= 10 else '' #10퍼 이하삭제
plt.pie(values,labels = labels,  autopct=custom_autopct,colors=colors,wedgeprops=wedgeprops,pctdistance=0.7) #퍼센트 거리띄우기
plt.show()
```

<img src="data:image/png;base64,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"/>


```python
grp = df.groupby('학교')
```


```python
values1 = [grp.size()['북산고'],grp.size()['능남고']]
labels1 = ['북산고','능남고']
plt.pie(values1,labels=labels1)
plt.show()
```

<img src="data:image/png;base64,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"/>

## 산점도 그래프



```python
df['학년'] = [3,3,2,1,1,3,2,2]
df
```

<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>이름</th>
      <th>학교</th>
      <th>키</th>
      <th>국어</th>
      <th>영어</th>
      <th>수학</th>
      <th>과학</th>
      <th>사회</th>
      <th>SW특기</th>
      <th>학년</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>채치수</td>
      <td>북산고</td>
      <td>197</td>
      <td>90</td>
      <td>85</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>Python</td>
      <td>3</td>
    </tr>
    <tr>
      <th>1</th>
      <td>정대만</td>
      <td>북산고</td>
      <td>184</td>
      <td>40</td>
      <td>35</td>
      <td>50</td>
      <td>55</td>
      <td>25</td>
      <td>Java</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>송태섭</td>
      <td>북산고</td>
      <td>168</td>
      <td>80</td>
      <td>75</td>
      <td>70</td>
      <td>80</td>
      <td>75</td>
      <td>Javascript</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>서태웅</td>
      <td>북산고</td>
      <td>187</td>
      <td>40</td>
      <td>60</td>
      <td>70</td>
      <td>75</td>
      <td>80</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>강백호</td>
      <td>북산고</td>
      <td>188</td>
      <td>15</td>
      <td>20</td>
      <td>10</td>
      <td>35</td>
      <td>10</td>
      <td>NaN</td>
      <td>1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>변덕규</td>
      <td>능남고</td>
      <td>202</td>
      <td>80</td>
      <td>100</td>
      <td>95</td>
      <td>85</td>
      <td>80</td>
      <td>C</td>
      <td>3</td>
    </tr>
    <tr>
      <th>6</th>
      <td>황태산</td>
      <td>능남고</td>
      <td>188</td>
      <td>55</td>
      <td>65</td>
      <td>45</td>
      <td>40</td>
      <td>35</td>
      <td>PYTHON</td>
      <td>2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>윤대협</td>
      <td>능남고</td>
      <td>190</td>
      <td>100</td>
      <td>85</td>
      <td>90</td>
      <td>95</td>
      <td>95</td>
      <td>C#</td>
      <td>2</td>
    </tr>
  </tbody>
</table>
</div>



```python
plt.scatter(df['영어'],df['수학'])
plt.xlabel('영어')
plt.ylabel('수학')
```

<pre>
Text(0, 0.5, '수학')
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.scatter(df['영어'],df['수학'], s=[df['영어'] + df['수학']]) #사이즈 조절
plt.xlabel('영어')
plt.ylabel('수학')
```

<pre>
Text(0, 0.5, '수학')
</pre>
<img src="data:image/png;base64,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"/>

[cmap](https://matplotlib.org/stable/tutorials/colors/colormaps.html)



```python
plt.scatter(df['영어'],df['수학'], s=[df['영어'] + df['수학']],c=df['학년'],cmap = 'viridis',alpha=0.6) #색 조절
plt.xlabel('영어')
plt.ylabel('수학')
```

<pre>
Text(0, 0.5, '수학')
</pre>
<img src="data:image/png;base64,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"/>


```python
plt.figure(figsize=(10,10))
plt.scatter(df['영어'],df['수학'], s=[df['영어'] + df['수학']],c=df['학년'],cmap = 'viridis',alpha=0.6) 
plt.xlabel('영어')
plt.ylabel('수학')
plt.colorbar(ticks = [1,2,3], label='학년', shrink=0.5, orientation = 'horizontal')#컬러바  shrink = 사이즈  orientation= 세울지 눕힐지
```

<pre>
<matplotlib.colorbar.Colorbar at 0x1b72b759fc8>
</pre>
<img src="data:image/png;base64,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"/>

## 여러 그래프



```python
fig,axs = plt.subplots(2,2, figsize = (25,15)) # 2 X 2 에 해당하는 plot 들을 생성
fig.suptitle('여러그래프')

axs[0,0].bar(df['이름'],df['국어'],label='국어점수') #데이터 설정
axs[0,0].set_title('첫 그래프')#제목
axs[0,0].legend()#범례
axs[0,0].set(xlabel = '이름',ylabel = '점수') #x,y축 label
axs[0,0].set_facecolor('lightyellow')#전면 색
axs[0,0].grid(linestyle='--',linewidth=0.5)

# 두 번째 그래프
axs[0,1].plot(df['이름'],df['수학'],label = '수학')
axs[0,1].plot(df['이름'],df['영어'], label ='영어')
axs[0,1].legend()

#세번째
axs[1,0].barh(df['이름'],df['키'])
#네번째
axs[1,1].plot(df['이름'],df['사회'],alpha=0.5,color = 'green')
```

<pre>
[<matplotlib.lines.Line2D at 0x1b72c0cbec8>]
</pre>

## 히트맵



```python
data = np.random.random((8, 8))
plt.imshow(data, cmap='cool', interpolation='nearest')
plt.show()
```

<img src="data:image/png;base64,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"/>