---
layout  : wiki
title   : Atomic Ordering
summary : 
date    : 2020-04-23 21:49:51 +0900
updated : 2020-04-23 22:08:29 +0900
tags    : 
toc     : true
public  : false
parent  : 
latex   : false
---
* TOC
{:toc}

# Atomic Ordering

멀티쓰레드 환경에서 값을 공유하는 방법 중 하나는 Atomic 변수를 사용하는 것이다.
변수 값을 읽고, 쓰기가 atomic하게 동작한다면 멀티쓰레드에서 쉽게 일고 쓸 수 있다.

Atomic 변수를 읽거나 쓸 때 Memory Ordering을 설정할 수 있다.

## Data Race

하나의 값을 여러 쓰레드가 동시에 읽거나 쓰면, 일부만 바뀐 값이나 랜덤한 값이 읽히거나 쓰일 수 있는 문제.

## Race Condition

Async한 이벤트의 순서가 꼬이는 문제.

## Ordering::Relaxed

Ordering에 제한을 두지 않는다.

## Ordering::Released


