# DOCTYPE
- [DOCTYPE란?](#doctype)
  - [Quirks Mode란](#quirks)
  - [DOCTYPE을 최상단에 선언하는 이유는?](#ann)
- [Meta tag란?](#meta0)
  - [Meta tag를 왜 알아야할까?](#meta1)
  - [Meta tag의 요소는?](#meta2)
- [💡 출처](#source)
--- 

## <span style='background-color: #fff5b1; color: black' id='doctype'>DOCTYPE이란?</span>
DOCTYPE은 "Document Type Declaration"의 약어로, HTML 문서의 버전 및 유형을 정의하는데 사용됩니다. 웹 브라우저는 이 DOCTYPE 선언을 통해 문서를 어떻게 렌더링해야 하는지 결정합니다. 

```html
1. html5 선언
<!DOCTYPE html>

2. html4.01 strict version 선언
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01//EN" "http://www.w3.org/TR/html4/strict.dtd">
``` 

다음과 같이 HTML 문서의 맨 처음에 위치합니다. 만약 이와 같은 선언이 없다면 Quirks Mode로 동작하게 되어, 예상치 못한 레이아웃 문제가 호환성 문제를 일으 킬 수 있습니다. HTML 문서를 작성할 때는 반드시 DOCTYPE을 선언해야 합니다.

## <span style='background-color: #fff5b1; color: black' id='quirks'>Quirks Mode란</span>

__역사적 이야기__ : MDN Web doc을 참고하게 되면 예전에는 페이지가 2가지의 버전이 있었다고 한다. Netscape Navigator, Microsoft 인터넷 익스플로어 이렇게 존재 했었다. W3C(웹 표준을 만드는 곳)에서 기준을 만들었을 때, 브라우저들은 바로 웹 기준을 적용할 수 없었다. 왜냐하면 기존에 존재하는 페이지들에 대한 문제가 생길것이기 문이다. 그래서 브라우저가 예전 레거시 사이트와는 달리 2가지 모드를 제공하여 새로운 기준에 적합하게 만들었다.


- Quirks Mode 

  레이아웃은 navigator4 와 인터넷 익스플로어5에 해당한다. 웹 표준에 맞추기전에 있던 웹페이지들에 해당한다.

- Limited-quirks mode (Almost standard mode)

  아주 작은 quirk가 적용된다.


- No-quirks mode(Full standard mode)

  모던 HTML과 CSS에 해당하기 때문에 현재 2023 우리는 이 방법을 채택하고 있다.




## <span style='background-color: #fff5b1; color: black' id='ann'>DOCTYPE을 최상단에 선언하는 이유는?</span>

이유를 크게 두 가지로 나눌 수 있을 것 같다.

1. 최상단에 선언하는 이유

  웹 브라우저 에게 어떠한 HTML 버전을 사용하여 작성되었는지 알려주기 위해 선언합니다. 이 방식을 사용하여 어떤 방식으로 렌더링을 할지 브라우저 결정을 한다.


2. 선언을 해주어야되는 이유 

  위와 중복되지만 쿼크스모드로 전환되는 것을 방지하기 위해. 표준에 맞는 HTML 방식을 굳이 바꿀 필요가 없지 않는가? 


## <span style='background-color: #fff5b1; color: black' id='meta0'>Meta tag란?</span>

meta 태그는 해당 문서 혹은 application의 metadata를 담기 위한 요소입니다.
metadata는 데이터를 설명해주기 위한 데이터로 알고 있습니다. 대표적으로 charset, viewport, description, facebook에서의 open graph 요소가 있습니다.


## <span style='background-color: #fff5b1; color: black' id='meta1'>Meta tag를 왜 알아야할까? </span>

1. 검색 엔진 최적화: 검색 엔진이 페이지를 제대로 인식 할 수 있도록 설명(description) 을 주며 검색 결과에 표시 될 수 있도록한다.

2. 문자 인코딩 지정: charset을 사용하여 웹페이지의 문자 인코딩을 지정 할 수 있다

3. 반응형 디자인: viewport 메타 태그를 사용하여 웹페이지가 작은 기기에서도 제대로 콘텐츠를 보여줄수 있게 노력한다

한 마디로 `<meta>` 태그를 올바르게 사용하면 웹 페이지의 가독성, 접근성, 검색 엔진 최적화가 향상될 수 있습니다.


## <span style='background-color: #fff5b1; color: black' id='meta2'>Meta tag의 요소는? </span>


```html 
<!-- charset, 문자 인코딩을 어떻게 할 것인지 결정-->
<!-- utf-8, 전세계 언어의 대부분을 지원 -->
<!-- DB의 charset과 맞춰서 선언해주는 것이 가장 바람직-->
<meta charset="utf-8">

<!-- viewport, 모바일, 태플릿 pc에서 화면을 어떻게 노출시킬지 알려주기 위하여 사용 -->
<!-- 해당 meta tag가 없으면 모바일 브라우저에서 이상하게 렌더링 됨 -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">


<!-- SEO에 대한 도움을 주는 metadata -->
<meta name="description" content="웹 사이트에 대한 정보">


<!-- facebook -->
<!-- open graph protocol -->
<meta property="og:title" content="metadata element">
<meta property="og:description" content="metadata element">
<meta property="og:url" content="metadata element">
<meta property="og:image" content="metadata element">


```
여기서 몰랐는데 redirection도 가능한 것으로 보인다. 

```
<meta charset="utf-8">

<!-- 3초 후 리다이렉트 -->
<meta http-equiv="refresh" content="3;url=https://www.mozilla.org">
```


---
## <span style='background-color: #fff5b1; color: black' id='source'>💡출처 </span>
- https://developer.mozilla.org/ko/docs/Glossary/Doctype#%EB%8D%94%EB%B3%B4%EA%B8%B0
- https://developer.mozilla.org/ko/docs/Web/HTML/Element/meta