---
layout  : wiki
title   : 리눅스 키보드 세팅
summary : 
date    : 2020-04-25 11:08:29 +0900
updated : 2020-04-25 12:27:57 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# Linux keyboard 세팅

gnome-tweaks에서 설정한 키보드 옵션이 어떻게 적용되는지 분석하자.

## Gnome Tweaks

Gnome Tweaks는 Gnome 3의 고급 기능을 설정하는 GUI도구다.
Keyboard & Mouse 탭의 "Additional Layout Options" 버튼을 클릭하면 키보드의 조합키를 다양하게 설정할 수 있는 옵션이 있다.

Gnome Tweaks의 소스코드는 Gitlab[^1]에서 받을 수 있다. Gnome Tweaks는 Python으로 작성된 프로그램이다.

[^1]: [Gnome Tweaks repository](https://gitlab.gnome.org/GNOME/gnome-tweaks)

모든 소스코드는 gtweak 디렉토리 안에 있다,
gtweak 디렉토리에 바로 있는 소스코드들은 프로젝트의 얼개에 대한 코드가 있다. gtweak/tweaks 디렉토리 안에는 각 메뉴 UI에 대한 소스코드가 있다.

gtweak/tweaks/tweak_group_keymouse.py[^2] 파일이 "Keyboard & Mouse" 탭을 담당한다.
이 파일 안에 AdditionalLayoutButton[^3] 코드가 있다.
이 버튼은 클릭[^4]했을 dialog를 만들고[^5] 그 안에 ScrolledWindow를 만들고[^6], 다시 그 안에 TypingTweakGroup[^7]을 만든다.

[^2]: [gtweak/tweaks/tweak_group_keymouse.py](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py)
[^3]: [gtweak/tweaks/tweak_group_keymouse.py](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py)
[^4]: [gtweak/tweaks/tweak_group_keymouse.py#L229](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py#L229)
[^5]: [gtweak/tweaks/tweak_group_keymouse.py#L229](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py#L229)
[^6]: [gtweak/tweaks/tweak_group_keymouse.py#L241](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py#L241)
[^7]: [gtweak/tweaks/tweak_group_keymouse.py#L241](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py#L241)

gtweak/tweaks/tweak_group_xkb.py[^8] 파일 안에 TypingTweakGroup[^9] 클래스가 정의되어 있다.
이 클래스는 GnomeDesktop.XKBInfo 로부터 모든 옵션그룹을 읽는다[^10]. 이 옵션들을 TweakGroup[^11]으로 화면에 표현한다.

[^8]: [gtweak/tweaks/tweak_group_xkb.py](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py)
[^9]: [gtweak/tweaks/tweak_group_xkb.py](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py)
[^10]: [gtweak/tweaks/tweak_group_xkb.py#L162](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py#L162)
[^11]: [gtweak/tweaks/tweak_group_xkb.py#L166](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py#L166)
