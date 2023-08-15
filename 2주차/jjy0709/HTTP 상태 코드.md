## HTTP Status Code
HTTP 요청이 성공적으로 수행되었는지 나타냄

### 100번대: Information Responses
요청을 받았으며 프로세스를 계속함
- 100, Continue: 클라이언트가 요청을 계속 보내거나 이미 요청이 끝났을 경우 무시
- 101, Switching Protocols: Upgrade request header에 응답, 서버가 옮기려는 protocol 명시
- 102, Processing: 서버가 요청을 받았고 처리중이지만 아직 응답이 가능하지 않음
- 103, Early Hints: Link header와 사용, 서버가 응답을 준비하는 동안 user agent가 자원을 preload하도록 함

### 200번대: Successful Responses
요청을 성공적으로 받았으며 인식했고 수용함
- 200, OK: 요청을 정상적으로 처리함
- 201, Created: 새로운 resource가 정상적으로 생성됨, 보통 POST나 PUT 요청에 대한 응답
- 202, Accepted: 요청을 받았으나 아직 실행되진 않음
- 203, Non-Authoritative Information: 요청을 성공적으로 처리했지만 다른 소스에서 수신된 정보를 제공, 검증 되지 않은 상태
- 204, No Content: 요청에 대한 응답 content가 없음, headers may be useful
- 205, Reset Content: 새로운 내용을 확인해야 함(새로고침 등)
- 206, Partial Content: Range header 존재 시 resource의 일부만 요청되었을 때 사용.
- 207, Multi Status: 여러 개의 리소스가 여러 상태 코드를 갖고 있는 상황에서 적절한 정보 전달
- 208, Already Reported: DAV에서 사용

### 300번대: Redirection Messages
클라이언트의 요청에 대해 적절한 위치를 제공하거나 대안의 응답 제공
- 300, Multiple Choice: 여러 응답이 가능한 요청을 보냈을 경우 선택지 반환
- 301, Moved Permanently: 요청된 자원의 URL이 바뀌었음. 변경된 새 URL 반환
- 302, Found: 요청된 자원의 URI가 일시적으로 변경되었음. 원래 요청했던 URI로 요청해야 함.
- 303, See Other: 클라이언트가 다른 URI에서 요청된 자원을 얻도록 direct
- 304, Not Modified: caching 목적으로 사용, 응답이 수정되지 않았으므로 클라이언트가 응답의 같은 캐시된 버전을 사용 가능
- 305, Use Proxy: 이전 HTTP 버전에서 정의, 프록시를 통해 접근해야 함. 보안 이슈로 deprecated
- 306, Unused: no longer used, just reserved. HTTP/1.1에서 사용되었음.
- 307, Temporary Redirect: 302와 동일, HTTP 메소드 변경 X
- 308, Permanent Redirect: 301과 동일, HTTP 메소드 변경 X 

### 400번대: Client Error Responses
클라이언트의 잘못된 요청
- 400, Bad Request: 잘못된 문법, 유효하지 않은 요청 메세지 등 클라이언트의 잘못된 요청으로 서버가 요청을 처리할 수 없음.
- 401, Unauthorized: Unauthenticated, 클라이언트가 응답을 받기 위해서는 권한 인증이 필요함.
- 402, Payment Required: future use를 위해 예약, 원래 목적은 digital payment system에 사용
- 403, Forbidden: 클라이언트가 content에 대해 접근 권한이 없음, 401과 달리 클라이언트의 identity를 서버가 아는 상태
- 404, Not Found: 요청된 리소스를 찾을 수 없음. 브라우저: URL 인식 불가, API: endpoint는 유효하나 리소스가 존재하지 않는 의미로 사용 가능
- 405, Method Not Allowed: 타겟 리소스에 대해 해당 메소드를 지원하지 않음.
- 406, Not Acceptable: user agent의 기준에 부합하는 content를 찾을 수 없음
- 407, Proxy Authentication Required: 401과 유사, 권한 인증이 proxy에 의해 수행되어야 함.
- 408, Request Timeout: idle connection에 사용, 서버가 사용되지 않는 연결을 종료할 것을 의미, 안보내고 끊을 때도 있음
- 409, Conflict: 서버의 현재 상태와 요청이 충돌
- 410, Gone: 요청된 content가 forwarding 주소 없이 서버에서 영원히 삭제됨.
- 411, Length Required: 서버가 필요로 하는 Content-Length 헤더 필드가 정의되지 않음.
- 412, Precondition Failed: 클라이언트가 precondition 명시하였으나 서버가 만족하지 않음.
- 413, Payload Too Large: 서버에 정의된 최대 크기보다 request entity가 큼
- 414, URI Too Long: 요청된 URI가 너무 길어서 처리할 수 없음.
- 415, Unsupported Media Type: 요청한 데이터의 미디어 포맷이 서버에 의해 지원되지 않음.
- 416, Range Not Satisfiable: Range 헤더의 범위가 충족되지 않음. 타겟 URI 데이터의 크기 밖인 경우 발생 가능.
- 417, Expectation Failed: Expect 헤더의 expectation이 서버에 의해 처리될 수 없음.
- 418, I'm a teapot: brew coffee 시도를 teapot으로 거부. 서버는 티팟이므로 커피 내리기를 거절했음
- 421, Misdirected Request: 요청이 응답을 생성할 수 없는 서버로 지정됨
- 422, Unprocessable Content: 요청은 well-formed but semantic error로 인해 처리 불가
- 423, Locked: 접근하려는 리소스가 locked
- 424, Failed Dependency: 이전 요청의 실패로 인해 요청 실패
- 425, Too Early: 서버가 재실행될 요청을 처리하길 원치 않음
- 426, Upgrade Required: 현재 프로토콜로 요청을 처리하길 거부. 클라이언트가 다른 프로토콜로 업그레이드하면 처리할 수도
- 428, Precondition Required: 요청이 conditional 되어야 함. 필수 전제 조건 헤더가 누락됨
- 429, Too Many Requests: 유저가 주어진 시간에 너무 많은 요청을 보냄
- 431, Request Header Fields Too Large: 헤더 필드가 너무 커서 처리 거부
- 451, Unavailable For Legal Reasons: legally 제공할 수 없는 리소스에 대한 요청, 정부에 의해 검열된 불법적인 리소스

### 500번대: Server Error Responses
정상적인 클라이언트 요청에 대해 서버 문제로 응답 불가
- 500, Internal Server Error: 서버가 처리할 수 없는 상, 서버의 문제로 응답할 수 없음
- 501, Not Implemented: 서버가 지원하지 않는 요청 메소드, 클라이언트 요청에 대해 서버가 수행할 수 있는 기능이 없음
- 502, Bad Gateway: 서버 위의 서버에서 오류 발생, proxy나 gateway 등에서 응답
- 503, Service Unavailable: 서버가 요청을 처리할 준비가 되지 않음, 서버가 일시적으로 사용 불가(유지보수로 인해 중단되거나 과부하가 걸림)
- 504, Gateway Timeout: 서버가 다른 서버로 요청을 보냈으나 delay가 발생하여 처리 불가
- 505, HTTP Version Not Supported: 요청의 HTTP 버전이 서버에 의해 지원되지 않음
- 506, Variant Also Negotiates: 서버에 내부 구성 오류가 있음.
- 507, Insufficient Storage: 서버가 요청을 성공적으로 처리하기 위해 필요한 representation을 저장할 수 없음.
- 508, Loop Detected: 요청을 처리하는 동안 무한 루프를 감지함
- 510, Not Extended: 서버가 처리하기 위해서는 요청을 더 확장해야 함.
- 511, Network Authentication Required: 클라이언트가 네트워크 접근 위한 권한 인증을 해야 함.

### 400번대와 500번대 차이
400: 클라이언트 요청 오류, 새로고침해도 에러가 고쳐지지 않음
500: 서버 문제, 서버가 복구되거나 디비가 복구되는 경우 반복 요청 시 접근 가능할 수 있음.


**참고 자료**
- https://developer.mozilla.org/en-US/docs/Web/HTTP/Status
- https://hocheon.tistory.com/68#recentEntries
