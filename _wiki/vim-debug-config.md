---
layout  : wiki
title   : VIM 설정 디버깅하기
summary : 
date    : 2020-03-25 15:10:15 +0900
updated : 2020-03-25 15:22:02 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

## 로깅

```vim
:echo "Hello, world!"
:echom "Hello world persistent"
```

`echo`와 `echom`을 사용해서 로그를 남길 수 있다.
`echo`는 밑의 창에 메시지를 한 번 보여주고 끝난다.
`:messages`를 사용하면 `echom`이 남긴 로그를 확인할 수 있다.

### 레퍼런스

* https://learnvimscriptthehardway.stevelosh.com/chapters/01.html

## 매핑 확인하기

`:map`을 사용하면 vim이 지금 설정되어있는 모든 매핑을 출력한다.
`:map <c-e>`을 사용하면 vim이 `<c-e>`에 매핑되어있는 커맨드를 출력한다.
연속된 키로된 매핑들이 있다면 그 중 앞 글자만 사용해서 공통 prefix 검색을 할 수 있다.
`:map \w`를 입력하면 `:map \wa`, `:map \ww` 와 같이 `\w`로 시작하는 모든 매핑이 출력된다.

* 주의: leader키를 사용해서 정의한 매핑은 실제 사용되는 키로 바뀌어서 검색된다.

`:map`은 현재 매핑을 출력해주지만 검색을 지원하지 않는다.
검색을 하고 싶다면 불편하겠지만 내용을 레지스터에 적은 뒤 버퍼에 붙여넣어야 한다.

```vim
:redir @a>
:map
:redir END
:put a
```

### 레퍼런스

* https://stackoverflow.com/a/24843350/2756490
 
### 함수 호출하기

autocmd에서 호출하는 함수가 동작이 되는지 의심스럽다면, 직접 호출해서 결과를 볼 수 있다.
`call functionname()`을 사용하자.
