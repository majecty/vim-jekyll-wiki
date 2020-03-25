---
layout  : wiki
title   : OAuth
summary : 
date    : 2020-03-25 17:37:53 +0900
updated : 2020-03-25 20:06:48 +0900
tags    : 
toc     : true
public  : false
parent  : 
latex   : false
---
* TOC
{:toc}

# OAuth의 동작원리를 중요한 부분만 요약

[네이버 D2 블로그](https://d2.naver.com/helloworld/24942)를 요약했다.

## OAuth 1과 2

OAuth 2는 OAuth 1의 간략화한 버전이다.

## OAuth 1의 동작 과정

대표 용어
* User: Service Provider에 계정을 가지고 있으며, Consumer를 이용하는 사람
* Service Provider: API를 제공하는 사람. OAuth를 사용해 인증해야 API를 사용할 수 있다.
* Consumer: Service Provider의 API를 사용하는 어플리케이션
* Request Token: Consumer가 Service Provider에게 접근 권한을 인증받기 위해 사용하는 값.
* Access Token: 인증 후 Consumer가 Service Provider의 API를 사용하기 위해 사용하는 값.

Consumer는 다음 과정을 거쳐서 권한을 얻는다.

간략하게 보자면 Request Token획득, 유저 로그인, Access Token 획득의 세 단계다.

아래에 좀 더 자세히 단계를 구분했다.
1. Consumer는 Service Provider에게 Request Token을 요구한다.
2. Service Provider로부터 Request Token을 받은 뒤 유저를 Service Provider의 페이지로 보낸다.
3. 유저는 ServiceProvider에 로그인한다.
4. ServiceProvider는 유저가 로그인한 뒤 결과를 Consumer에게 보내준다.
5. Consumer는 유저가 로그인 성공함을 확인하고 Service Provider에게 Access Token을 요청한다.
6. Service Provider가 준 Access Token을 사용해서 API들을 사용한다.

다음은 Request Token은 요청할 때 필요한 매개변수들이다.
* oauth_callback: Service Provider가 인증은 완료한 후 리다이렉트할 Consumer의 웹 주소이다. 웹 주소가 없다면 "oob"를 사용한다.
* oauth_consumer_key: Consumer를 구분하는 키.
* oauth_nonce: Consumer가 임의로 생성한 문자열이다. 악의적인 목적으로 계속 요청하는 것을 막기 위해 있다고 한다.
* oauth_signature: 다른 파라미트덜을 암호화하고 인코딩하여 서명한 값
* oauth_signature_method: oauth_signature를 암호화하는 방법
* oauth_timestamp: 요청을 생성한 시점의 타임스탬프
* oauth_version: 버전

다음은 Request Token Response로 받는 값들
* oauth_token: 다음 요청에서 사용할 토큰
* oauth_secret: 다음부터 서명 생성할 때 사용

다음은 사용자 인증 페이지를 호출할 때 사용할 매개변수들이다.
* oauth_token: Request Token Response 에서 받은 토큰

다음은 사용자 인증 성공했을 때 Consumer가 받는 값들
* oauth_token: 다음 요청부터 사용할 토큰
* oauth_verifier


## 관심가질만한 과정들

* oauth_signature를 만들 때 사용하는 키는 Consumer Secret Key다. 이 키는 보통 Service Provider가 이전에 Consumer에게 발급해준다.
* Reuest Token 요청에 대한 응답으로 oauth_token과 oauth_secret를 준다.
* 유저가 Service Provider에 로그인 성공하면, Consumer는 Service Provider로부터 새로운 oauth_token과 oauth_verifier를 받는다. 왜 다른 필드에 같은 이름을 쓸까?
* 

## 궁금한 점

* Request Token이 필요한 이유는 무엇일까?
* Signature가 필요한 이유는?
* 콜백에 필요한 이유는? 없이는 무엇을 할 수 있나?
* oauth_nonce와 timestamp의 역할은 무엇인가?
* oauth_verifier의 역할은 무엇인가?

## Reference

* https://d2.naver.com/helloworld/24942
* https://tools.ietf.org/html/rfc5849
