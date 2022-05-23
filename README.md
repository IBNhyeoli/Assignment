# Open Source Software Assignment 

+ ## A Table of Contents
+ ### Linux Command
+ ### Vim Macro Command

---

+ ## Linux Command

### top
  
시스템의 상태를 전반적으로 가장 빠르게 파악 가능(CPU, Memory, Process)
  
옵션 없이 입력하면 interval 간격(기본 3초)으로 화면을 갱신하면 정보를 보여줌
  
top 실행 전 옵션
    
순간의 정보를 확인 하려면 `-b` 옵션 추가(batch 모드)
    
`-n` : top 실행 주기 설정(반복 횟수)
    
top 실행 후 명령어

|명령어|설명|
|:---:|:---:|
|shift + p|CPU 사용률이 높은 프로세스 순서대로 표시|
|shift + m|메모리 사용률이 높은 프로세스 순서대로 표시|
|shift + t|프로세스가 돌아가고 있는 시간 순서대로 표시|
|-k|프로세스 kill -k 입력 후 종료할 PID입력 signal을 입력하라고 하면 kill signal인 9를 입력|
|-a|메모리 사용량에 따라 정렬|
|-b|Batch 모드 작동|
|-f|sort field 선택 화면 >> q 누르면 RES 순으로 정렬|
|1|CPU Core 별로 사용량을 보여줌|

`top`

<img src = "https://user-images.githubusercontent.com/95179732/169704385-e3e442bc-5265-4814-8e41-1477df75a302.PNG" width = "100%" height = "100%"/>

20:49:01 : 현재 시간

up 0 min : 0분 전에 구동 (시간이 지나면 몇 분전에 구동했는지 확인 가능)

load average : 현재 시스템이 얼마나 일을 하는지를 나타냄.
> 3개의 숫자는 1분, 5분, 15분 간의 평균 실행 / 대기 중인 프로세스의 수

Tasks : 프로세스 개수

MiB Mem, Swap : 각 메모리의 사용량
> MiB(메비바이트) : MB의 이진 접두어

PR : 실행 우선순위

VIRT, RES, SHR : 메모리 사용량 >> 메모리 누수 확인 가능

S : 프로세스의 상태
> 작업 중, I / O 대기, 유휴 상태 등

---

VIRT, RES, SHR

현재 프로세스가 사용하고 있는 메모리

VIRT

> 프로세스가 사용하고 있는 virtual memory의 전체 용량

> 프로세스에 할당된 가상 메모리 전체

> SWAP + RES

RES

> 현재 프로세스가 사용하고 있는 물리 메모리의 양

> 실제로 메모리에 올려서 사용하고 있는 물리 메모리

SHR

> 다른 프로세스와 공유하고 있는 shared memory의 양

---

Memory Commit

프로세스가 커널에게 필요한 메모리를 요청하면 커널은 프로세스에 메모리 영역을 주고 실제로 할당은 하지 않지만 해당 영역을 프로세스에게 준 것을 저장해둠

이 과정을 ___Memory commit___ 이라 함

커널이 프로세스의 메모리 요청에 따라 즉시 할당하지 않고 Memory Commit과 같은 기술을 사용해 요청을 지연키는 이유

> `fork()` 와 같은 새로운 프로세스를 만들기 위한 콜을 처리해야 하기 때문

> `fork()` 시스템 콜을 사용해 커널이 실행중인 프로세스와 똑같은 프로세스를 하나 더 만듦
>
> 그 후, `exec()` 시스템 콜을 통해 다른 프로세스로 변함

> COW(Copy-On-Write) 기법을 통해 복사된 메모리 영역에 실제 쓰기 작업이 발생한 후 실질적인 메모리 할당을 진행

---

프로세스 상태

SHR 옆에 있는 S 항목으로 볼 수 있음

D : Uninterruptiable sleep. 
> 디스크 혹은 네트워크 I / O 를 대기

R : 실행 중 (CPU 자원을 소모)

S : Sleeping 상태, 요청한 리소스를 즉시 사용 가능

T : Traced or Stopped.
> 보통의 시스템에서 자주 볼 수 없는 상태

Z : zombie
> 부모 프로세스가 죽은 자식 프로세스
