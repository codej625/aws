# 로드 밸런서를 사용하면서 주의점을 알아보자!

<br />

1. http 접속시 리디렉션 관련
```
https 접속이 아닌 http 접속 시,
실제 운영 되는 사이트는 http 프로토콜에 보안 소켓 계층(SSL)을 사용한 https를 사용할 수 있게끔 리디렉션 되어야 한다.
```
```
작업
│
├─ 작업 유형
│  │ 
│  ├─ 라우팅 액션
│  │  │ 
│  │  ├─ 대상 그룹으로 전달
│  │  ├─ URL로 리디렉션
│  │  ├─ 고정 응답 반환
│  │  │
│  │
│

위에 경로에서 URL로 리디렉션을 선택한다.
```
```
"URI 부분", "전체 URL 옵션" 중 한 가지를 선택할 수 있는데,
URI 부분을 선택하고 프로토콜은 HTTPS, 포트는 443
(밑에 사용자 지정 호스트, 경로, 쿼리를 사용하시오... 옵션은 체크 해제)
상태 코드는 301 - 영구 이동됨으로 선택한다.
```
```
다음을 누르면 최종적으로

작업(다음 수행)
리디렉션 대상 HTTPS://#{host}:443/#{path}?#{query}
상태 코드: HTTP_301
이처럼 적용된 것을 알 수 있다.

변경 내용 저장을 누르고 나온다.
```
