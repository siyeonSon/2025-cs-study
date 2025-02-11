## DNS (Domain Name System)

DNS는 **호스트의 도메인 네임을 네트워크 주소로 변환**하거나 그 반대의 역할을 수행하는 시스템입니다. 사용자가 도메인 네임(예: `naver.com`)을 입력하면 아래와 같은 과정이 이루어집니다.

## 동작원리

### 1. 브라우저에서 도메인 입력

- 사용자가 `www.naver.com`을 입력하면 **네임 서버(DNS 서버)**에 접속합니다.

### 2. Local DNS Server에서 IP 요청

- 먼저 **PC의 Local DNS Server**에서 `www.naver.com`의 IP 주소를 요청합니다.
  1. **인터넷 연결** 시, 기본적으로 통신사의 DNS 서버가 등록됩니다.
  2. **이전에 접속한 기록이 있는 경우**:
     - Local DNS 서버에서 캐싱된 IP 주소를 PC에 전달하여 요청 종료.
  3. **접속 기록이 없는 경우**:
     - Local DNS 서버가 **다른 DNS 서버들과 통신**을 시작합니다.

### 3. 도메인과 연결된 IP 정보 확인

1. **Root DNS Server에 요청**
   - `Root DNS Server`는 도메인 정보가 있는 상위 DNS 서버로 요청을 전달합니다.
   - 해당 도메인 정보가 없는 경우, 다음 서버로 이동하라는 응답을 보냅니다.
2. **TLD DNS Server 요청**

   - `TLD DNS Server`는 도메인의 최상위 도메인(`.com`, `.co.kr` 등)을 관리합니다.
   - 예: `naver.com`의 `.com` 정보 확인.
   - 해당 도메인이 없다면 다른 서버를 찾아보라는 응답을 보냅니다.

3. **Authoritative DNS Server 요청**
   - 실제 도메인과 IP 주소의 관계가 기록/저장/변경되는 서버입니다.
   - 예: `naver.com`의 Authoritative DNS Server에서 `www.naver.com`의 IP 주소를 확인하여 응답.

### 4. 사용자 PC에 IP 전달

- PC는 전달받은 IP 주소를 사용하여 서버에 접속합니다.
- 이 과정에서 **IP 주소를 캐싱**하여 다음 요청 시 빠르게 연결될 수 있도록 합니다.

### 5. 브라우저에 서버 내용 출력

- 최종적으로 서버의 IP 주소를 통해 **브라우저에 요청된 페이지가 출력**됩니다.
