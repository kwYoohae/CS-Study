참고 자료
- https://wpaud16.tistory.com/304

---
### TLB(Translation Lookaside Buffer)

**Page Table**
- 가상 주소와 실제 주소를 mapping 하는 table
- 프로세스마다 고유의 Page Table 존재, Context switching 시 변경

**TLB**
- CPU는 명령어를 수행하기 위해 메인 메모리에 최소 2번은 접근해야 원하는 데이터를 얻을 수 있음
  1. page table 접근
  2. page table 기반으로 실제 메모리 접근
- 이 경우 같은 table을 사용하지만 메인 메모리에 접근해야 하는 불필요한 일이 발생
- 이런 메모리의 접근을 줄이고자 TLB 사용 -> page table의 임시저장 cache 역할
- 최근에 읽었던 page table entry를 매핑하여 저장
- context switching 할 때 모두 flush? 비효율 -> task의 table 정보를 같이 저장해야 함 -> ASID(Address Space ID)

