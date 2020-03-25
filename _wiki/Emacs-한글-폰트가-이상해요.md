---
layout  : wiki
title   : Emacs 한글 폰트가 이상해요
summary : 
date    : 2020-03-25 16:45:56 +0900
updated : 2020-03-25 16:50:33 +0900
tags    : 
toc     : true
public  : false
parent  : 
latex   : false
---
* TOC
{:toc}

# Emacs를 GUI로 사용할 때 한글 폰트가 serif일 때가 있다

Emacs GUI에서 한글 폰트가 sans serif로 표시되는데 여러 폰트 설정을 바꾸어도 적용되지 않았다.
메뉴에서 Options -> Multilingual Environment -> Set Language Environment -> UTF-8로 바꾸었을 때 Sans Serif글꼴이 적용되었다.
자세한 동작 원리는 아직 파악하지 않았다.

init.el에 `'(current-language-environment "UTF-8")`를 사용해도 똑같은 효과가 나온다.
