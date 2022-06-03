# 오픈소스SW - 20223186 정민재

**top, ps, jobs, kill 명령어**
---------------------------
***top***

top 명령어는 현재 OS의 상태를 나타내어주는 CLI 어플리케이션이다. 
메모리 사용량, CPU 사용량 등을 나타내주기에 시스템의 상태를 전반적으로 빠르게 파악이 가능하다.

top를 실행하는 동안에는 주기적인 업데이트로 실시간에 근접한 내용을 보여준다.

* 옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하며 정보를 보여줌

top 실행 전 옵션
* 순간의 정보를 확인하려면 -b 옵션 추가(batch 모드)
* -n : top 실행 주기 설정(반복 횟수)

top 실행 후 명령어
* shift + p : CPU 사용률 내림차순
* shit + m : 메모리 사용률 내림차순
* shift + t : 프로세스가 돌아가고 있는 시간 순
* k : kill. k 입력 후 PID 번호 작성. signal은 9
* f : sort field 선택 화면 -> q 누르면 RES순으로 정렬
* a : 메모리 사용량에 따라 정렬
* b : Batch 모드로 작동
* 1 : CPU Core별로 사용량 보여줌


ps와 top의 차이점
* ps는 ps한 시점에 proc에서 검색한 cpu 사용량
* top은 proc에서 일정 주기로 합산해 cpu 사용율 출력

<img width="670" alt="43t3" src="https://user-images.githubusercontent.com/106823471/171884838-cc272601-d36d-4971-9686-0d931cab209c.png">


```c
#include <stdio.h>
```
