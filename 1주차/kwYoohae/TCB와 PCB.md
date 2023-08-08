## Context Switching이란? 
### Context Switching의 배경
- 우리는 현재도 수십 수백개의 Process를 컴퓨터에서 동작시키고 있다.
  - 이런 Process들은 모두 동시에 돌아가는 것 처럼 보인다. 
  - 하지만, 컴퓨터의 자원은 한정되어있다. (ex. 4코어 8쓰레드... )
  - 그렇기 때문에, 동시에 동작하는것 처럼 보이는 **동시성**을 지키기 위해서 Task를 짧은 시간을 가지고 왔다갔다하면서 실행을 하게된다.
- 이런 Task의 전환을 위해서 Context Switching이라는 단어가 나오게 되었다. 

### 그래서 Context Switching이 뭔데?
```text
즉, Context Switching은 한 프로세스가 실행되다가 어떤 이유로 다음 프로세스로 전환되어야 할때, 현재 Procss의 정보를 저장하고 다음 프로세스의 상태 정보를 불러오는 과정을 말합니다. 
```
- 이러한 과정에서, Process의 정보는 *PCB**라는 자료구조에 저장을 합니다.

## PCB란? 
- PCB는 Process Control Block으로, Process들을 관리하는 자료구조이다.
  - PCB의 목적은 **Context Switching**을 할때 정보를 저장하는 목적을 가지고 있다 
  - 커널이 프로세스를 관리하기 위한 것으로 볼 수 있다.
### PCB가 가지고 있는 정보들
- Process ID : Process의 ID 값
- Process State : 프로세스가 생성이 되었는지, 준비인지, 대기인지 등의 상태정보를 저장합니다 
- PC Register : PC Register는 다음에 실행될 명령어의 위치 (주소)를 저장합니다
- Register Information : Register에 대한 정보를 저장합니다
- Memory Limits : 메모리 관리 시스템에 대한 정보를 저장 합니다. (ex. Page Table, Segment Table 등)
- 이 뿐만이 아닌 여러 정보들을 저장하고 있습니다. 
  - 우리는 이러한 정보들을 `top`, `ps`등과 같은 명령어를 통해 쉽게 볼 수 있습니다.

![img](https://github.com/h2database/h2database/assets/74089271/8a417708-0edb-4298-8c46-d5293b9785a7)

## TCB란? 
- TCB는 Thread Control Block으로 쓰레드의 상태님 제어 정보를 저장하는 자료구조 입니다. 
  - Process나 Thread들은 모두 OS가 관리하기 때문에 상태 및 동작을 효율적으로 관리하기 위해 저장하는 정보입니다. 
### TCB가 가지고 있는 정보
- Thread ID : Thread에 대한 ID 정보를 저장합니다. 
- Stack Pointer : Thread는 Stack영역을 새로 할당 받기 떄문에 Stack의 위치에 대한 정보를 저장합니다.
- Thread의 상태 : Thread가 어떤 상태인지 등을 나타냅니다.  
- PC : 다음에 실행될 명령어의 위치 (주소)를 저장합니다. 
- 등등에 대한 정보를 저장합니다.