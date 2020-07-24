---
layout  : wiki
title   : 
summary : 
date    : 2020-07-24 07:01:56 +0900
updated : 2020-07-24 11:05:07 +0900
tags    : 
toc     : true
public  : true
parent  : 
latex   : false
---
* TOC
{:toc}

# Web Event

HTMLElement은 이벤트를 통해서 UI에서 발생한 유저 입력을 JavaScript에게 전달한다.

## Event의 발생

클릭 벤트나 키보드 입력 이벤트와 같은 브라우저가 제공하는 이벤트들은 상황에 맞춰서 브라우저가 이벤트를 발생시킨다.
이 이외에 JavaScript를 사용해서 원하는 이벤트를 생성할 수 있다.

### 정해진 함수 호출

몇몇 이벤트들은 HTMLElement에 정의되어 있는 특정 함수를 호출하여 발생시킬 수 있다.

```javascript
// click 함수를 호출하면 "click" 이벤트가 발생하한다.
document.getElementById("myButton").click();
```

* [MDN HTMLElement.click()](https://developer.mozilla.org/en-US/docs/Web/API/HTMLElement/click)

### elem.dispatchEvent(event); 

HTMLElement의 dispatchEvent 함수를 사용해서 이벤트를 발생시킬 수 있다.

```javascript
elem.dispatchEvent(new CustomEvent("awesome"));
```

* [MDN 이벤트 생성 및 트리거](https://developer.mozilla.org/ko/docs/Web/Guide/Events/Creating_and_triggering_events)

## Event의 처리

이벤트가 발생하면 미리 등록한 자바스크립트 함수가 실행된다.

### Event handler property

HTMLElement들은 자신이 발생시킬 수 있는 event들에 대해서 event ᄂhandler에 한 property를 제공한다.

```javascript
btn.onclick = function () {
  console.log("hi");
}
```

### addEventListener와 removeEventListener

addEventListenr를 사용해서도 특정 함수를 이벤트 핸들러로 등록할 수 있다.
앞선 방법보다 나중에 표준에 포함된 방법이며, 한 이벤트에 여러 핸들러를 등록할 수 있는 특징이 있다.

```javascript 
btn.addEventListener("click", function () {
  console.log("hi");
});
```

* [Introduction to events](https://developer.mozilla.org/en-US/docs/Learn/JavaScript/Building_blocks/Events#Event_bubbling_and_capture): 이벤트 핸들러를 등록하는 방법에 대한 자세한 설명이 담겨있다.

## capturing과 bubbling

HTML은 트리 구조다. 자식 노드에 이벤트가 발생하면 해당 이벤트를 부모 노드들도 처리할 수 있다.
이 때 부모에 등록된 이벤트부터 처리하는 방식을 capturing, 자식에 등록된 이벤트부터 처리하는 방식을 bubbling이라고 한다.
지금 웹 표준은 capturing 모드로 등록된 이벤트들을 먼저 처리하고, bubbling으로 등록된 이벤트들을 처리한다.
`addEventListener`함수의 두번째 인자로 bubbling인지 capturing인지 명시할 수 있다.
bubbling이 기본값이며 bubbling을 권장한다. 

### stopPropagation

이벤트 핸들러 안에서 이벤트.stopPropagation()을 호출하면 그 이후 bubbling 전파를 중단시킬 수 있다.
bubbling이 원치 않은 경우나, 성능을 위해서 설정한다.

## 레퍼런스

* [MDN에서 Event 타입 문서](https://developer.mozilla.org/en-US/docs/Web/API/Event): 문서의 초반부에 이벤트에 대한 개괄적인 내용이 잘 정리되어 있다.
