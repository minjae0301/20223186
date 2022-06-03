# 오픈소스SW - 20223186 정민재

**top, ps, jobs, kill 명령어**
---------------------------
***TOP*** = Window 작업관리자

top 명령어는 현재 OS의 상태를 나타내어주는 CLI 어플리케이션이다. 
메모리 사용량, CPU 사용량 등을 나타내주기에 시스템의 상태를 전반적으로 빠르게 파악이 가능하다.

리눅스를 사용하는 서버의 성능이나 현재 돌아가고 있는 상황을 파악하기 위해 사용하고, top를 실행하는 동안에는 주기적인 업데이트로 실시간에 근접한 내용을 보여준다.

* 옵션 없이 입력하면 interval 기본 3초의 간격으로 화면을 갱신하며 정보를 보여준다.

top 실행 전 옵션
* 순간의 모든 정보를 확인하려면 -b 옵션 추가(batch 모드)
* top -n : top 실행 주기 설정(반복 횟수)

top 실행 후 명령어
* shift + p : CPU 사용률이 높은 프로세스 순서대로 표시
* shit + m : 메모리 사용률 높은 프로세스 순서대로 표시
* shift + t : 프로세스가 돌아가고 있는 시간 순서대로 표시
* k : kill  -k 입력 후 종료할 PID 번호 작성. signal에는 9입력
* f : sort field 선택 화면 -> q 누르면 RES순으로 정렬
* a : 메모리 사용량에 따라 정렬
* b : Batch 모드로 작동
* 1 : CPU Core별로 사용량을 보여준다.


* Page Down : 프로세스의 다음페이지 목록 / Page Up : 프로세스의 이전페이지 목록
= 방향키로도 목록 확인 가능


![3t3t3t](https://user-images.githubusercontent.com/106823471/171893473-344cc2ae-791d-4897-8096-075ba554896b.PNG)


**TOP 명령어 정보 시스템 내용**
* 00:35:38 : 현재 서버의 시간
* days, 1 min : uptime(리눅스 서버가 구동되고 있는 시간)
* load average : 현재 시스템이 얼마나 일을 하는지를 나타낸다. 3개의 숫자는 1분, 5분, 15분 단위로 평균 실행, 대기 중인 프로세스의 수이고, CPU 코어수 보다 적으면 문제가 없다.
* Tasks : 프로세스 개수
* KiB Mem, Swap : 각 메모리의 상태 정보
* PR : 실행 우선순위
* VIRT, RES, SHR : 메모리 사용량 => 누수 체크 가능
* S : 프로세스 상태(작업중, I/O 대기, 유휴 상태 등)

**CPU**
* %us : 유저 레벨에서 사용하고 있는 CPU 비중
* %sy : 시스템 레벨에서 사용하고 있는 CPU 비중
* %id : 유휴 상태에서의 CPU 비중
* %wa : 시스템이 I/O 요청을 처리하지 못한 상태에서의 CPU idle 상태인 비중

**프로세스 상태 정보**
* PID : 프로세스의 ID
* USER : 프로세스를 실행시킨 사용자의 ID
* PRI (Priority) : 프로세스의 우선순위
* NI : NICE의 값, 일의 nice value 값이다. 마이너스를 가지는 nice value는 우선순위가 높다.
* VIRT (Virtual Image) : 프로세스가 사용하고 있는 virtual memory의 전체 용량이자, 프로세스에 할당된 가상 메모리의 전체이다. (SWAP + RES)
* **RES** (Resident Size) : 현재 프로세스가 사용하고 있는 물리 메모리의 양 
* SHR (Shared Memory Size) : 다른 프로세스와 공유하고 있는 메모리의 양 = 라이브러리
* S : 프로세스의 상태 [ S(Sleeping/요청한 리소스를 즉시 사용 가능), R(Running/CPU 자원을 소모), W(swapped out process), Z(Zombied), D(Uninterruptiable sleep/디스크 혹은 네트워크 I/O를 대기), T(Traced or Stopped/보통의 시스템에서 자주 볼 수 없는 상태) ]
* %CPU : 프로세스가 사용하는 CPU의 사용율
* %MEM : 프로세스가 사용하는 메모리의 사용율
* COMMAND : 실행된 명령어 

---------------------------

***ps*** (Process Status) = Window 작업관리자

ps 명령어는 현재 실행중인 프로세스 목록과 상태를 보여준다.  

ps 실행 전 옵션
* -e : 실행중인 모든 프로세스의 정보를 출력
* -aux : 실행중인 모든 프로세스 정보를 출력
* -f : 프로세스에 대한 자세한 정보를 출력(PPID 확인 가능)
* -u [사용자 이름] : 특정 사용자에 대한 모든 프로세스 정보 출력
* -p pid : pid로 지정한 프로세스 정보 출력

* u : 프로세스 소유자의 이름, 메모리 사용량, CPU 사용량 등 상세 정보를 출력
* a : 터미널에서 실행한 프로세스의 정보를 출력
* x : 실행 중인 모든 프로세스 정보 출력

![2r2r2r2r](https://user-images.githubusercontent.com/106823471/171907685-2b6b5be2-ca0e-40ff-9857-4e861b25c5f4.PNG)

**ps 명령어 정보 시스템 내용**
* PID : 프로세스의 ID
* TTY : 프로세스가 실행된 터미널의 종류와 번호
* TIME : 해당 프로세스가 사용한 CPU 시간의 양
* CMD : 프로세스가 실행중인 명령이 무엇인지 알려줌

![-f](https://user-images.githubusercontent.com/106823471/171909170-7c7851c3-7a35-4648-b565-8be2f46a3994.PNG)

**ps -f**
* UID : 프로세스를 실행한 사용자 ID
* PPID : 부모의 프로세스 번호
* C : CPU 사용량(%)
* STIME : 프로세스 시작 시간

**BSD 계열**
* BSD 계열 옵션은 '-'을 제외하고 사용한다. (a / u / x / f / ww)

**GNU 계열**
* GNU 계열 옵션은 명령어 앞에 '--'를 붙이고 사용한다.


**top과 ps의 차이점**
|top|ps|
|--------|--------|
|proc에서 일정 주기로 합산하여 CPU 사용율 출력|ps한 시점에 proc에서 검색한 CPU 사용량 출력|

---------------------------

***jobs*** 

jobs 명령어는 작업이 중지된 상태나 진행중인 상태를 표시한다.

실행시킨 백그라운드 작업의 목록이 출력되며, 각 작업에는 번호가 붙어 있어서 kill 명령어 뒤에 '%번호' 등으로 사용 가능하다.

* #bg : 백그라운드 실행
* #fg : 포그라운드 실행
* -l : 프로세스 그룹 ID를 state 필드 앞에 출력
* -n : 프로세스 그룹 중 대표 프로세스 ID 출력
* -p : 각 프로세스 ID에 대해 한 행씩 출력
* command : 지정한 명령어 실행 

![jobs](https://user-images.githubusercontent.com/106823471/171914448-475a145e-bd3d-42a3-a8ed-c0a871b088ce.PNG)

**jobs 명령어 작업 상태값**
* Running : 작업 계속 진행중임
* Done : 작업이 완료되어 0을 반환(Done code => 작업 완료, 0이 아닌 코드 반환)
* Stopped : 작업 일시 중단
* Stopped(SIGTSTP/SIGSTOP/SIGTTIN/SIGTTOU) : 시그널이 작업을 일시 중단

---------------------------

***kill***

kill 명령어는 프로세스에 시그널을 보내는 명령어이다.

* kill : 프로세스에 종료 시그널 보내기.
* killall : 프로세스 이름으로 종료하는 명령어(ps로 확인한 PID로 가능 => kill -PID)
* shutdown : 시스템을 안전하게 종료  

**프로세스에 시그널 보내기**
```c
$ kill [option] PID

# 12345(PID) 프로세스 종료 
$ kill -9 12345
$ kill -SIGKILL 12345
```
**kill -l (시그널 목록)**
  
![-l](https://user-images.githubusercontent.com/106823471/171917561-b48182e4-7107-4761-98c8-566abee687b4.PNG)
  
**주요한 시그널**
* SIGHUP : 세션이 종료될 때 시스템이 내리는 시그널
* SIGINT : Ctrl + C, 종료 요청의 시그널
* SIGKILL : 강제 종료 시그널
* SIGSEGV : 메모리 침범이 일어날 때 시스템이 보내는 시그널
* SIGTERM : 기본 값, 종료 요청의 시그널
* SIFTSTP : Ctrl + Z, 일시 중지 요청의 시그널

**kill -9 보다는 kill -15 우선**
|kill -9 [pid]|kill -15 [pid]|
|--------|--------|
|프로세스 강제 종료|프로세스 작업 종료|
|진행중인 작업이나 데이터가 삭제되는 경우 발생|순차적으로 진행중인 작업을 안전하게 종료|
