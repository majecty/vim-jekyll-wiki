# Vim Jekyll wiki

이 wiki는 Johngrib님의 위키를 클론한 프로젝트다.
자세한 사항은 https://johngrib.github.io/wiki/my-wiki/ 을 참고하자.
위 문서에서 vim 설정에 관한 내용만 추려서 정리한다.

## 설정하기

### Vimwiki 설정

Johngrib님의 문서에서 Vimwiki설정을 따라한다.

### Startify 설정

Startify는 쓰기 쉽게 vim의 첫 화면을 만들어준다.
wiki session을 만들고  startify에서 먼저 나오게 설정하면 쉽게 wiki에 접근할 수 있다.

```vim
let g:startify_lists = [
      \ { 'type': 'sessions',  'header': ['   Sessions']       },
      \ { 'type': 'files',     'header': ['   MRU']            },
      \ { 'type': 'dir',       'header': ['   MRU '. getcwd()] },
      \ { 'type': 'bookmarks', 'header': ['   Bookmarks']      },
      \ { 'type': 'commands',  'header': ['   Commands']       },
      \ ]

```

### fzf 설정

이미 작성한 문서를 찾는 용도로 fzf를 사용한다.
F1키 두 번 누르면 fzf가 뜨도록 설정하면 편리하다.
또한 preview window를 설정하면 파일의 내용이 오른쪽에 보인다.

```vim
nnoremap <F1><F1> :Files<cr>
let g:fzf_preview_window = 'right:60%'
```

### Vim wiki 상세 설정

Johngrib님이 따로 작성하신 [vimwiki문서](https://johngrib.github.io/wiki/vimwiki/)가 있다. 참고해서 적용하자.

### Tagbar 설정

Johngrib님의 [vim tagbar에서 markdown을 적용시키자](https://johngrib.github.io/wiki/vim-tagbar-with-markdown/)를 따라하자.

## 새 파일 만들기

index.md 새로운 문서를 추가한다. 

