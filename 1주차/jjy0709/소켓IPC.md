참고자료
- https://www.inflearn.com/questions/11347/%EC%86%8C%EC%BC%93%EC%9D%84-%EC%9D%B4%EC%9A%A9%ED%95%9C-ipc%EB%8A%94-%EA%B8%B0%EC%A1%B4-%EB%8B%A4%EB%A5%B8-%EB%B0%A9%EC%8B%9D%EB%93%A4%EA%B3%BC-%EC%96%B4%EB%96%A0%ED%95%9C-%EC%A0%90%EC%9D%B4-%EC%B0%A8%EC%9D%B4%EA%B0%80-%EC%9E%88%EB%82%98%EC%9A%94
- https://noel-embedded.tistory.com/692
---
**Socket**
- 네트워크 소켓: 컴퓨터 네트워크를 경유하는 프로세스 간 통신의 종착점
- 프로그램이 네트워크에서 데이터를 통신할 수 있도록 해주는 연결부
- stream 형식으로 사용 가능 & datagram 형식으로 사용 가능
- Internet domain으로 bind 가능 & unix domain으로 bind 가능
- 외부 프로세스와도 통신하면서 내부 프로세스와도 통신 가능
- 네트워크 기능을 이용해 IPC로도 사용 가능
- 소켓의 다양한 기능을 사용할 수 있다 but 사용하기에 까다롭다.