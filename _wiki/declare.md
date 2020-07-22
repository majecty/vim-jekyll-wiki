---
layout  : wiki
title   : 
summary : 
date    : 2020-07-22 11:30:30 +0900
updated : 2020-07-22 11:50:00 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# declare

kakoune 설정을 검색하다가 만난 `declare -a extraArgs=()`를 이해하자.

`declare`는 bash에서 제공하는 커맨드다. `bash -c "help declare"`를 사용해서 도움말을 출력할 수 있다. declare를 사용해서 변수를 선언할 수 있다. 쉘 스크립트에서 자주 사용하는 MY_VAR=XX 방식은 문자열 값을 저장하는 방식이다. `declare`를 사용하면 변수에 숫자나 함수, 어레이만 사용하도록 강제할 수 있다.

`declare -a extraArgs=()`는 array 타입의 extraArgs를 선언하고 초기값으로 `()`를 준다는 의미이다.
