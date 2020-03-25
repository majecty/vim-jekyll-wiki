---
layout  : wiki
title   : vim mapping
summary : 
date    : 2020-03-25 15:10:15 +0900
updated : 2020-03-25 15:31:27 +0900
tags    : 
toc     : true
public  : false
parent  : 
latex   : false
---
* TOC
{:toc}

## Mapping debugging하기

`:map` 키워드를 사용하면 매핑 목록을 볼 수 있다. 

자세한 디버깅 방법은 [[./vim-debug-config]] 문서를 참고하자.

## Leader 설정하기

기본 Leader키는 `\`이며, `let mapleader = ","` 설정으로 리더키를 바꿀 수 있다.

많은 플러그인들이 Leader키로 시작하는 단축키를 사용한다.
추측하건데 시스템 단축키와 구별하기 위하여 Leader키를 사용하는 것으로 보인다.

