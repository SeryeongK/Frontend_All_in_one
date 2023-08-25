# CORS

- [CORS](#cors)
  - [CORS가 뭔가요?](#cors가-뭔가요)
  - [CORS를 겪고 직접 해결해 본 경험이 있으면 말해주세요](#cors를-겪고-직접-해결해-본-경험이-있으면-말해주세요)

---

## <span style='background-color: #fff5b1; color: black'>CORS가 뭔가요?</span>

CORS는 "Cross-Origin Resource Sharing"의 약자로, 웹 브라우저에서 다른 도메인(Origin) 간에 자원(예: 데이터, 이미지, 스크립트 등)을 공유할 수 있도록 해주는 보안 메커니즘입니다. <span style="font-weight: 600; color: tomato;">웹 애플리케이션은 보안상의 이유로 동일 출처 정책(Same-Origin Policy)에 따라 다른 출처의 리소스에 접근할 수 없습니다. 출처는 프로토콜, 도메인, 포트 번호를 기준으로 결정됩니다.</span>
</br>
CORS는 이러한 동일 출처 정책을 우회하여 다른 도메인 간에 데이터를 공유하기 위한 방법을 제공합니다. 웹 애플리케이션의 서버와 브라우저 간에 정의된 규칙을 따라, 다른 도메인의 리소스 요청을 허용하거나 거부할 수 있습니다. 이를 통해 보안상의 이슈나 데이터 유출을 방지하면서도 필요한 데이터 교환을 할 수 있게 됩니다.
CORS는 HTTP 헤더를 사용하여 구현되며, 주로 서버 측에서 설정됩니다. 주요한 CORS 관련 헤더는 다음과 같습니다.

1. **`Access-Control-Allow-Origin`**: 허용할 출처(도메인) 목록을 지정합니다. "\*"를 사용하여 모든 출처를 허용할 수도 있습니다.
2. **`Access-Control-Allow-Methods`**: 허용할 HTTP 메서드 목록을 지정합니다.
3. **`Access-Control-Allow-Headers`**: 허용할 HTTP 헤더 목록을 지정합니다.
4. **`Access-Control-Expose-Headers`**: 클라이언트가 접근할 수 있는 헤더 목록을 지정합니다.
5. **`Access-Control-Allow-Credentials`**: 쿠키와 같은 인증 정보를 요청에 포함시킬지 여부를 나타냅니다.
6. **`Access-Control-Max-Age`**: 사전 요청(Preflight)의 유효 시간을 지정합니다.

CORS는 보안 및 데이터 공유의 중요한 측면을 다루므로 웹 개발자들은 이를 이해하고 올바르게 구성하여 웹 애플리케이션이 원활하게 작동하고 안전하게 운영될 수 있도록 해야 합니다.

## <span style='background-color: #fff5b1; color: black'>CORS를 겪고 직접 해결해 본 경험이 있으면 말해주세요</span>

React를 사용한 프로젝트에서 CORS 문제가 발생했을때 <span style="font-weight: 600; color: tomato;">proxy middleware를 사용하여 해결</span>했습니다.
클라이언트 코드에서 API 요청을 보낼 때, **`/api`** 경로를 사용하여 프록시 미들웨어를 통해 API 서버로 요청을 보냅니다.</br>
이렇게 설정하면 **`http-proxy-middleware`**를 사용하여 프록시 미들웨어를 통해 API 요청을 보내게 되며, 브라우저에서의 CORS 문제를 우회하면서 API 데이터를 가져올 수 있게 됩니다.
</br>
Next.js를 사용한 프로젝트에선 <span style="font-weight: 600; color: tomato;">Next.js의 기능인 API 경로 사용해서, CORS 문제를 해결</span>할 수 있습니다.
Next.js 프로젝트 내에서 **`pages/api`** 폴더를 생성하고, API 관련 로직을 해당 폴더 내에 구현합니다. 이렇게 구현된 API는 Next.js 서버와 동일한 도메인에서 실행되므로 CORS 문제가 발생하지 않습니다.
클라이언트 코드에서는 해당 API 경로를 호출하는 것으로 API 요청을 보냅니다.</br>
이렇게 설정하면 Next.js의 기본 기능을 사용하여 API 요청을 처리하면서, 브라우저에서의 CORS 문제를 회피할 수 있습니다. Next.js의 API 경로는 동일한 도메인에서 실행되므로, CORS 관련 문제 없이 데이터를 가져올 수 있게 됩니다.

[교차 출처 리소스 공유 (CORS) - HTTP | MDN](https://developer.mozilla.org/ko/docs/Web/HTTP/CORS)
