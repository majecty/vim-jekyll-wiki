---
layout  : wiki
title   : 리눅스 키보드 세팅
summary : 
date    : 2020-04-25 11:08:29 +0900
updated : 2020-04-25 16:48:27 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# Linux keyboard 세팅

## 목적

gnome-tweaks에서 "Additional Oayout Options" 버튼을 누르면 나오는 창에서 설정한 키보드 옵션이 어떻게 적용되는지 분석하자.

## Gnome Tweaks

Gnome Tweaks는 Gnome 3의 고급 기능을 설정하는 GUI도구다.
Keyboard & Mouse 탭의 "Additional Layout Options" 버튼을 클릭하면 키보드의 조합키를 다양하게 설정할 수 있는 옵션이 있다.

Gnome Tweaks의 소스코드는 Gitlab[^1]에서 받을 수 있다. Gnome Tweaks는 Python으로 작성된 프로그램이다.

[^1]: [Gnome Tweaks repository](https://gitlab.gnome.org/GNOME/gnome-tweaks)

모든 소스코드는 gtweak 디렉토리 안에 있다,
gtweak 디렉토리에 바로 있는 소스코드들은 프로젝트의 얼개에 대한 코드가 있다. gtweak/tweaks 디렉토리 안에는 각 메뉴 UI에 대한 소스코드가 있다.

gtweak/tweaks/tweak_group_keymouse.py[^2] 파일이 "Keyboard & Mouse" 탭을 담당한다.
이 파일 안에 `AdditionalLayoutButton`[^3] 코드가 있다.
이 버튼은 클릭[^4]했을 dialog를 만들고[^5] 그 안에 `ScrolledWindow`를 만들고[^6], 다시 그 안에 `TypingTweakGroup`[^7]을 만든다.

[^2]: [gtweak/tweaks/tweak_group_keymouse.py](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py)
[^3]: [gtweak/tweaks/tweak_group_keymouse.py](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py)
[^4]: [gtweak/tweaks/tweak_group_keymouse.py#L229](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py#L229)
[^5]: [gtweak/tweaks/tweak_group_keymouse.py#L229](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py#L229)
[^6]: [gtweak/tweaks/tweak_group_keymouse.py#L241](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py#L241)
[^7]: [gtweak/tweaks/tweak_group_keymouse.py#L241](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_keymouse.py#L241)

gtweak/tweaks/tweak_group_xkb.py[^8] 파일 안에 `TypingTweakGroup`[^9] 클래스가 정의되어 있다.
이 클래스는 `GnomeDesktop.XKBInfo.get_all_options_groups`함수를 호출해[^10] 옵션들을 읽고 각 옵션마다 _XkbOption UI를 만들어 `self.pack_start(option, ...)`을 호출해 화면에 옵션을 표시한다.

[^8]: [gtweak/tweaks/tweak_group_xkb.py](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py)
[^9]: [gtweak/tweaks/tweak_group_xkb.py](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py)
[^10]: [gtweak/tweaks/tweak_group_xkb.py#L162](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py#L162)

`_XkbOption` class[^11]는 `TypingTweakGroup`과 같은 파일에 선언되어있다. 
`_XkbOption`은 GTK의 `Expander` 클래스를 상속하고 있으며, 각 옵션 그룹 안의 옵션값 읽어온 다음[^12] 옵션별로 체크버튼[^13]이나 라디오 버튼[^14]을 만든다.
각 옵션은 토글되었을 때 `_XkbOption`의 `_on_toggled` 함수를 호출한다[^15].
_on_toggled 함수[^16]는 상태에 따라서 `self._parent_settings`의 `setting_remove_from_list`, `setting_add_to_list` 중 하나를 호출한다.

[^11]: [gtweak/tweaks/tweak_group_xkb.py#17](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py#L17)
[^12]: [gtweak/tweaks/tweak_group_xkb.py#L43](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py#L43)
[^13]: [gtweak/tweaks/tweak_group_xkb.py#L80](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py#L80)
[^14]: [gtweak/tweaks/tweak_group_xkb.py#L82](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py#L82)
[^15]: [gtweak/tweaks/tweak_group_xkb.py#L88](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py#L88)
[^16]: [gtweak/tweaks/tweak_group_xkb.py#L126](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/tweaks/tweak_group_xkb.py#L126)

`setting_add_to_list` 함수 `GsettingsSetting` 클래스의 메소드로 gtweak/gsettings.py[^17] 파일에 선언되어있다.
`setting_add_to_list` 함수는 `self[key] = vals`[^18] 코드로 설정 값을 저장한다. Python에서 `[]` 연산자로 값을 쓰는 경우 `__setitem__` 함수가 호출된다.

[^17]: [gtweak/gsettings.py#L161](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/gsettings.py#L161)
[^18]: [gtweak/gsettings.py#L178](https://gitlab.gnome.org/GNOME/gnome-tweaks/-/blob/ebc0f25d361d172385302b9c9ba12503571a11cf/gtweak/gsettings.py#L178)

`__setitem__` 함수는 `GsettingsSetting`가 상속하고 있는 `Gio.Settings` 클래스에 정의되어있다. `Gio` 코드는 PyGObject[^19] 프로젝트에 정의되어 있다. PyGObject레포지토리의 gi/overrides/Gio.py[^20] 코드 안에 `Settings`[^21] class가 선언되어있으며, 그 안에 `__setitem__`[^22] 함수가 선언되어있다.

[^19]: [PyGObject repository](https://gitlab.gnome.org/GNOME/pygobject)
[^20]: [gi/overrides/Gio.py](https://gitlab.gnome.org/GNOME/pygobject/-/blob/1a2bc1d0806ab6178f65125bf0b2283eb3378d4d/gi/overrides/Gio.py)
[^21]: [gi/overrides/Gio.py#L233](https://gitlab.gnome.org/GNOME/pygobject/-/blob/1a2bc1d0806ab6178f65125bf0b2283eb3378d4d/gi/overrides/Gio.py#L233)
[^22]: [gi/overrides/Gio.py#L264](https://gitlab.gnome.org/GNOME/pygobject/-/blob/1a2bc1d0806ab6178f65125bf0b2283eb3378d4d/gi/overrides/Gio.py#L264)

GSettings[^18]는 Gnome 설정파일을 수정하는 라이브러리다.
다양한 backend를 쓸 수 있다. GSettings를 사용하려면 Schema를 제공해야하며, Schema는 키에 대한 설명과 기본 값들을 들고 있다.

?? Schema는 어디에 어떻게 저장되어있는가. setting backend의 기본 값은 무엇이며 지금 읽고자 하는 값은 어디에 저장되어 있는가.

https://developer.gnome.org/gio/stable/GSettings.html
