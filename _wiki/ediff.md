---
layout  : wiki
title   : Ediff 사용하기
summary : 
date    : 2020-03-25 16:39:23 +0900
updated : 2020-03-25 16:44:29 +0900
tags    : 
toc     : true
public  : false
parent  : 
latex   : false
---
* TOC
{:toc}

# Ediff 사용하기

Ediff는 커맨드용 창을 따로 제공한다. 커맨드 창에서는 코드를 덩어리 단위로 수정한다.
코드를 글자 단위로 수정하고 싶을 때는 코드가 있는 창에 둘어가서 직접 수정하면 된다.
ediff는 diff할 때 창을 3개 보여주는데 각각 "A", "B", "C"의 이름을 가진다.
여러 명령을 사용할 때 이 "A", "B", "C" 이름을 사용한다.

* `|`는 diff를 칼럼 기준으로 바꾼다.
* `n`은 다음 쳥크를 보여준다.
* `p`는 이전 청크를 보여준다.
* BC는 현재 diff 쳥크에 대해서 B의 내용으 C에 덮어 씌운다.
* `q`는 ediff를 마치고 나가는 키다.


