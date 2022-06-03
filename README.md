# 오픈소스SW - 20223186 정민재

**top, ps, jobs, kill 명령어**
---------------------------
***TOP*** = Window 작업관리자

top 명령어는 현재 OS의 상태를 나타내어주는 CLI 어플리케이션이다. 
메모리 사용량, CPU 사용량 등을 나타내주기에 시스템의 상태를 전반적으로 빠르게 파악이 가능하다.

리눅스를 사용하는 서버의 성능이나 현재 돌아가고 있는 상황을 파악하기 위해 사용하고, top를 실행하는 동안에는 주기적인 업데이트로 실시간에 근접한 내용을 보여준다.

* 옵션 없이 입력하면 interval 기본 3초의 간격으로 화면을 갱신하며 정보를 보여준다.

top 실행 전 옵션
* 순간의 정보를 확인하려면 -b 옵션 추가(batch 모드)
* -n : top 실행 주기 설정(반복 횟수)

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
* PRI(Priority) : 프로세스의 우선순위
* NI : NICE의 값, 일의 nice value 값이다. 마이너스를 가지는 nice value는 우선순위가 높다.
* VIRT(SWAP + RES) : 프로세스가 사용하고 있는 virtual memory의 전체 용량이자, 프로세스에 할당된 가상 메모리의 전체이다.
* **RES** : 현재 프로세스가 사용하고 있는 물리 메모리의 양(Resident Size) 
* SHR : 다른 프로세스와 공유하고 있는 shared memory의 양 = 라이브러리
* S : 프로세스의 상태 [ S(Sleeping/요청한 리소스를 즉시 사용 가능), R(Running/CPU 자원을 소모), W(swapped out process), Z(Zombied), D(Uninterruptiable sleep/디스크 혹은 네트워크 I/O를 대기), T(Traced or Stopped/보통의 시스템에서 자주 볼 수 없는 상태) ]
* %CPU : 프로세스가 사용하는 CPU의 사용율
* %MEM : 프로세스가 사용하는 메모리의 사용율
* COMMAND : 실행된 명령어 










ps와 top의 차이점
* ps는 ps한 시점에 proc에서 검색한 cpu 사용량
* top은 proc에서 일정 주기로 합산해 cpu 사용율 출력


```c
#include <stdio.h>
```
