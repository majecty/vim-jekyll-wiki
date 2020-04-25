---
layout  : wiki
title   : Rust의 Pin
summary : 
date    : 2020-04-12 21:35:34 +0900
updated : 2020-04-12 21:58:55 +0900
tags    : 
toc     : true
public  : false
parent  : 
latex   : false
---
* TOC
{:toc}

# Rust Pin

Rust의 Pin<T> 타입은 T가 포인터 타입일 때 포인터 타입이 가리키는의 메모리 위치를 고정시킨다.
unsafe한 코드가 소유하지 않은 다른 메모리 영역을 포인트하고 싶을 때 사용한다.

## 동작 원리

# 의문

왜 Pin의 타입은 포인터 타입이어야 하는가.

# 힌트

Box는 안에 있는 메모리 영역을 변경할 수 있을까?
Box는 Pin이 없어도 그대로 동작하지 않을까?

