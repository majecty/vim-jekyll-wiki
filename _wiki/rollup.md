---
layout  : wiki
title   : Rollup
summary : 
date    : 2020-05-30 21:18:33 +0900
updated : 2020-05-30 21:27:11 +0900
tags    : 
toc     : true
public  : false
parent  : 
latex   : false
---
* TOC
{:toc}

# Rollup

Rollup은 JavaScript 번들러다. 자바 스크립트 소스코드들을 하나로 모은다.
input 파일과 output 파일을 받아서 input 파일이 의존하는 모든 파일을 묶어서 하나의 out파일을 만든다.

Rollup의 가장 큰 특징은 ES module 시스템을 사용한다는 점이다.
commonjs용으로 만들어진 라이브러리도 플러그인을 통해서 사용 가능하다.

## 신경쓸 점

Rollup은 상대경로에 있는 파일들만 하나로 합쳐준다.
Node JS의 라이브러리들을 out파일에 포함시키고 싶다면 @rollup/plugin-node-resolve 플러그인을 사용해야 한다.
