
---
published: true
layout: single
title: "Matplotlib style"
categories:
  - TIL
  - DA
tags:
  - [TIL,PANDAS,시각화]

toc: true
toc_sticky: true

---
# Matplotlib Style!

matplotlib을 보다보니 너무 못생긴 모습에 이것저것 컬러를 만져봐도 색감각이 없어서인지 완전 보노보노급이다

그렇게 찾다보니 stytle이라는걸 찾았는데 꽤나 상태가 괜찮아진다
다양한 스타일은 여기서 보면 될 것 같다

[matplotlib style sheet github](https://github.com/topics/matplotlib-style-sheets)

그리고 아래로 내가 본 몇개를 소개하겠다

먼저 
## Default
![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220731014304.png)

이상한건 아닌데 뭔가 많이 어색하다



## [dufte](https://github.com/nschloe/dufte)

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220731015128.png)

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220731015538.png)


이쪽에서 밀고있는건 연한 색감에 최대한 아무것도 안보이게 하는 스타일을 밀고있다
기본에서 크게 벗어나지않는데 조금 자연스러운 것 같다
SIMPLE IS IMPACT
``` python
!pip install dufte
import dufte
plt.style.use(dufte.style)
```



## [Pitaya](https://github.com/dhaitz/matplotlib-stylesheets)

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220731013347.png)

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220731014746.png)

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220731014831.png)

깔끔하고 이쁜 피타야 스타일 (light, dark)
은은한 파스텔빛으로 이쁜 것 같다
``` python
#dark 버전
plt.style.use('https://github.com/dhaitz/matplotlib-stylesheets/raw/master/pitayasmoothie-dark.mplstyle')

#light 버전
plt.style.use('https://github.com/dhaitz/matplotlib-stylesheets/raw/master/pitayasmoothie-light.mplstyle')
```


## [mplcyberpunk](https://github.com/dhaitz/mplcyberpunk)

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220731013753.png)

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220731015216.png)

![](https://raw.githubusercontent.com/Cloudblack/Forpicture/image//img/20220731015301.png)


사이버펑크wwww
어두운건 이제 제일 이쁜거같다
``` python
!pip install mplcyberpunk
import mplcyberpunk
plt.style.use("cyberpunk")
```


여기서 보여준건 각 style들기능에서도 그냥 기본적인 기능만을 사용했다
github에 들어가서 자세히보고 사용하면 더욱 좋은 스타일을 만들 수 있을 것이다