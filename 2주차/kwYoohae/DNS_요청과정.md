## DNS 요청 과정
1. 사용자가 Browser에 www.naver.com과 같은 도메인 이름을 입력해서 요청을 합니다. 
2. 우선 DNS 캐시에 www.naver.com의 주소가 있는지 확인합니다
    - 캐시는 컴퓨터에도 있지만, 브라우저에도 존재합니다 `chrome://net-internals/#dns`로 확인이 가능합니다
3. 만약 없으면 로컬 DNS서버에서도 DNS 쿼리를 보내서 확인을합니다. 
4. 그럼에도 불구하고 없다면 이제 루트 DNS -> TLD DNS -> Domain Name Server순으로 반복 혹은 재귀적 쿼리를 보내서 IP 주소를 얻어옵니다
     - 도메인서버까지 가기전에 TLD나 Root등은 어떤 DNS 서버가 알고있다고 알려주는 역학을 수행합니다
5. IP 주소는 DNS 캐시에 저장되고, 이를 사용해서 통신을 합니다 