---
layout: post
title: "Chrome Extension Release Log in 2015"
date:   2015-03-22 13:00:00
categories: HTML5
post_author: coremaker
description: "Chrome WebStore에 Installable Packaged App을 개발하여 발행하는 과정을 설명하고자 합니다."
published: true
---

## **Packaged App의 Chrome Web Store 발행기**

---

### [개요]

**0.목표**

**1.WebApp 형태 알아보기**

**2.WebApp 형태 선택하기**

**3.개발목표 정하기**

**4.개발에 필요한 것 Research**

---

### 0. 목표
WebApp을 만들어 WebStore에 발행하는 Cycle을 익혀보자!

---

### 1. WebApp 형태 알아보기

- **Server-based WebApp**
: OAuth 2.0 등으로 Server에서 보호/처리되는 Resource를 접근하여 서비스를 제공하는 방식

- **Browser-based WebApp**
: Javasciprt Library 등을 이용하여, 모던 브라우저 상에서 사용자에게 서비스를 제공하는 방식

- **Chrome App and Extension**
: chrome의 내부정의 API를 이용하여 서비스할 수 있으며, Install이 가능한 Packaged App을 지원

---

### 2. WebApp 형태 선택하기
대부분의 방식으로 Chrome WebStore에서 발행 할 수 있으나, 다음과 같은 기술과 도구를 적용해보고자 Packaged App 방식으로 선택하게 되었다. 특히, Chrome 내부 API를 사용하여 배포하기 위해서는 CSP를 반드시 적용해야 함을 잊지말자.

- App 배포
  : [ [CRX Package Format](https://developer.chrome.com/extensions/crx) ]

- WebComponents 사용
  : [ [W3C WebComponents Intro](http://www.w3.org/TR/components-intro/) ]
  : [ [WebComponents.org](http://webcomponents.org/) ]

- **Manifest For Packaged App**
  : [ [W3C Web Applications manifest](https://w3c.github.io/manifest/) ]
  : [ [Chrome Manifest ](https://developer.chrome.com/extensions/manifest) ]
  : [ [Mozilla Manifest](https://developer.mozilla.org/en-US/Marketplace/Options/Packaged_apps) ]

- **Content Security Policy For Packaged App**
  : [ [W3C CSP2](http://www.w3.org/TR/CSP2/) ]
  : [ [Chrome CSP](https://developer.chrome.com/extensions/contentSecurityPolicy) ]
  : [ [Mozilla CSP](https://developer.mozilla.org/ko/docs/Security/CSP) ]

- Chrome App Launcher
  : [ [Chrome App Launcher](https://chrome.google.com/webstore/launcher) ]

- Polymer 적용
  : [ [Polymer Home](https://www.polymer-project.org/0.5/) ]

- Chrome Dev Editor 사용
  : [ [Install Page](https://chrome.google.com/webstore/detail/chrome-dev-editor-develop/pnoffddplpippgcfjdhbmhkofpnaalpg) ]

- Chrome Apps & Extensions Developer Tool 사용
  : [ [Install Page](https://chrome.google.com/webstore/detail/chrome-apps-extensions-de/ohmmkhmmmpcnpikjeljgnaoabkaalbgc) ]

- **기능 추가 및 성능 향상을 위한 Chrome API 도입**
  : [ [Chrome Javascript API](https://developer.chrome.com/extensions/api_index) ]
  : [ [Chrome Web API](https://developer.chrome.com/extensions/api_other)]

---

### 3. 개발목표 정하기
현재 직장에서 반복되는 작업 중 웹기술을 이용하면 금방 적용이 가능한 App을 만들기로 생각했으며 다음과 같은 결정하였다.

**[개발목표]**

- OOXML 기반의 DOCX의 Data 뷰어
- 개발 방식 지식 공유(#thispage) 및 소스 Github 공개 [ [Link](https://github.com/popdance/OOXMLDataViewer) ]

**[분석결과]**

- DOCX는 ZIP으로 압축되어 있음
- DOCX는 xml과 각종 multimedia format을 포함하고 있음

**[기능분류]**

- load / unzip 기능
- zip entry view 기능 (tree type)
- xml view 기능
- xml code highligte 기능
- xml code beautify 기능
- xml editing 기능
- xml 이외의 multimedia format view 기능 (우선순위 낮음)
- save / zip 기능

---

### 4. 개발에 필요한 것 Research

**[ 사용할 Javascript Library ]**

- jszip [ [Github](https://github.com/Stuk/jszip) ]
- ace editor [ [Github](https://github.com/ajaxorg/ace) ]
- vkbeatify [ [Github](https://github.com/rt/vkbeautify-wrapper) ]
- polymer [ [Github](https://github.com/polymer/polymer) ]

**[ 개발 지원 기술 ]**

- nodejs [ [Homepage](https://nodejs.org/) ]
  : bower나 gulp 등 web 개발 편의성 도구 설치를 위해 설치

- bower [ [Homepage](http://bower.io/) ] / [ [Github](https://github.com/bower/bower) ]
  : Github 기반의 JS Library Package 관리를 위해 설치

- vulcanize [ [Github](https://github.com/polymer/vulcanize) ]
  : packaged app 개발 시 build 과정에서 문법/코드스타일/압축/**CSP(!)** 등을 지원

마지막으로 개발환경을 결정해야했다. 다음과 같이 결정하였다.

- Brakcet 사용 [ [Homepage](http://brackets.io/) ]
  : git/nodejs 등 plugin 풍부하며, web 개발 지원이 양호함

- Chrome dev tool 사용 - Chrome 기본 포함
  : App Runtime debugging을 위해 사용

- Chrome dev editor 사용 [ [Install Page](https://chrome.google.com/webstore/detail/chrome-dev-editor-develop/pnoffddplpippgcfjdhbmhkofpnaalpg) ]
  : Web Application 개발을 지원하며, Chrome WebStore Publising 기능이 있음

- Chrome Apps & Extensions Developer Tool 사용 [ [Install Page](https://chrome.google.com/webstore/detail/chrome-apps-extensions-de/ohmmkhmmmpcnpikjeljgnaoabkaalbgc) ]
  : Chrome Extension 개발(디버깅 등)을 지원하며, CRX로 패키징하는 것을 지원한다.
