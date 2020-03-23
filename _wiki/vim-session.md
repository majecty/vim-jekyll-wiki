## Vim session

작업하던 환경을 저장해놓는 기능이다.
다른 IDE의 워크스페이스 기능에 대응된다.

## 세션 만들기

:mks ~/.vim/session/xxx.vim

## 세션 열기

:source ~/.vim/session/xxx.vim
OR
vim -S ~/.vim/session/rooster.vim

## Startify way

Startify plugin을 설치하면 더 쉽게 session을 관리할 수 있다.

```vim
:SLoad    load a session
:SSave    save a session
:SDelete  delete a session
:SClose   close current session
```

## 레퍼런스

* https://bocoup.com/blog/sessions-the-vim-feature-you-probably-arent-using
* https://github.com/mhinz/vim-startify/wiki/Plugin-features-in-detail
