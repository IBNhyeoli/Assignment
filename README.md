# Open Source Software Assignment 

+ ## A Table of Contents
  + ### Linux Command
  + ### Vim Macro Command

---

# Linux Command

  ## top
  
+ __시스템의 상태를 전반적으로 가장 빠르게 파악 가능 (CPU, Memory, Process)__
  
+ __옵션 없이 입력하면 interval 간격으로 화면을 갱신하면 정보를 보여줌__
  > ___기본 간격은 3초로 설정되어 있음___
  
+ __top 실행 전 옵션__
    
  > ___순간의 정보를 확인 하려면 `-b` 옵션 추가 (batch 모드)___
    
  > ___`-n` : top 실행 주기 설정 (반복 횟수)___
    
+ __top 실행 후 명령어__

|명령어|설명|
|:---:|:---:|
|__shift + p__|__CPU 사용률이 높은 프로세스 순서대로 표시__|
|__shift + m__|__메모리 사용률이 높은 프로세스 순서대로 표시__|
|__shift + t__|__프로세스가 돌아가고 있는 시간 순서대로 표시__|
|__a__|__메모리 사용량에 따라 정렬__|
|__b__|__Batch 모드 작동__|
|__f__|__sort field 선택 화면 >> q 누르면 RES 순으로 정렬__|
|__H__|__상단의 Tasks 기준을 Thread로 변경__|
|__k__|__프로세스 kill -k 입력 후 종료할 PID입력 signal을 입력하라고 하면 kill signal인 9를 입력__|
|__m__|__메모리 사용률 시각화 표시__|
|__u__|__모니터링 할 user를 선택하여, 해당 권한 프로세스 감시__|
|__1__|__CPU Core 별로 사용량을 보여줌__|

+ __`top` or `top -b -n 1`__

<img src = "https://user-images.githubusercontent.com/95179732/169704385-e3e442bc-5265-4814-8e41-1477df75a302.PNG" width = "100%" height = "100%"/>

+ __20:49:01 : 현재 시간__
  > ___up 0 min : 0분 전에 구동 (시간이 지나면 몇 분전에 구동했는지 확인 가능)___

+ __load average : 현재 시스템이 얼마나 일을 하는지를 나타냄.__
  > ___3개의 숫자는 1분, 5분, 15분 간의 평균 실행 / 대기 중인 프로세스의 수___

+ __Tasks : 프로세스 개수__

+ __%CPU(s) : CPU의 사용률__
  > ___us : 사용자 레벨의 CPU 사용 비중___
  
  > ___sy : 시스템 레벨의 CPU 사용 비중___
  
  > ___ni : 우선순위가 낮은 프로세스의 CPU 사용 비중___
  
  > ___id : 유휴 상태의 CPU 사용 비중___
  
  > ___wa : I / O를 대기중인 CPU 사용률___
  
  > ___hi : interrupt handler에서 사용 중인 CPU 사용률, 빠르게 수행을 마쳐야 하는 작업___
  
  > ___si : hi에서 오래 걸리는 작업 때문에 미뤄놓은 작업___
  
  > ___st : 하이퍼바이저가 다른 가상 프로세서를 서비스하는 동안 가상 CPU가 실제 CPU를 기다리는 시간___

+ __MiB Mem, Swap : 각 메모리의 사용량__
  > ___전체 물리적인 Mem, 사용하고 있는 Mem, 여유 Mem, 버퍼된 Mem / 캐싱 Mem___
  >
  > ___전체 Swap Mem, 사용하고 있는 Swap Mem, 남아있는 Swap Mem, 사용 가능한 Mem___

+ __PR : 실행 우선순위__

+ __VIRT, RES, SHR : 메모리 사용량 → 메모리 누수 확인 가능__

+ __S : 프로세스의 상태__
  > ___작업 중, I / O 대기, 유휴 상태 등___

---

### VIRT, RES, SHR

+ __현재 프로세스가 사용하고 있는 메모리__

+ __VIRT__

  > __프로세스가 사용하고 있는__ ___virtual memory___ __의 전체 용량__

  > __프로세스에 할당된 가상 메모리 전체__

  > __SWAP + RES__

+ __RES__

  > __현재 프로세스가 사용하고 있는 물리 메모리의 양__

  > __실제로 메모리에 올려서 사용하고 있는 물리 메모리__

+ __SHR__

  > __다른 프로세스와 공유하고 있는__ ___shared memory___ __의 양__

---

### 프로세스 상태

+ __SHR 옆에 있는 S 항목으로 볼 수 있음__

  + __D :__ ___Uninterruptiable sleep___
    > __디스크 혹은 네트워크 I / O 를 대기__

  + __R : 실행 중 (CPU 자원을 소모)__

  + __S :__ ___Sleeping___ __상태__
    > __요청한 리소스를 즉시 사용 가능__

  + __T :__ ___Traced or Stopped___
    > __보통의 시스템에서 자주 볼 수 없는 상태__

  + __Z :__ ___zombie___
    > __부모 프로세스가 죽은 자식 프로세스__

 ## ps (Process Status)
  
  현재 실행중인 프로세스 목록을 보여줌
  
### ps 명령어
  
  + ### 사용법
  
    ### __`ps [option]`__
    
      > __주로 | (파이프라인),__ ___grep___ __명령어와 함께 사용하여 프로세스를 확인하는데 많이 사용__

  + ### 옵션

|명령어|설명|
|:---:|:---:|
|-A|모든 프로세스를 출력|
|a (BSD)|터미널과 연관된 프로세스를 출력하는 옵션|
|-a|세션 리더(일반저긍로 로그인 셀)을 제외하고 터미널에 종속되지 않은 모든 프로세스를 출력|
|-e|커널 프로세스를 제외한 모든 프로세스를 출력|
|-f|풀 포맷으로 보여줌, 유닉스 스타일로 출력해주는 옵션으로 UID, PID, PPID 등이 함께 표시|
|-l (Sys V), l (BSD)|긴 포맷으로 보여줌, 프로세스의 정보를 길게 보여주는 옵션으로 우선순위와 관련된 PRI와 NI값 확인 가능|
|-o 값|출력 포맷을 지정하는 옵션으로 값으로는 pid, tty, time, cmd 등으로 지정 가능|
|-M|64비트 프로세스들을 보여줌|
|-m|프로세스들 뿐만 아니라 커널 스레드들도 보여줌|
|-p|특정 PID를 지정할 때 사용|
|-r|현재 실행 중인 프로세서를 보여줌|
|u (BSD)|프로세스의 소유자를 기준으로 출력|
|-u|특정 사용자의 프로세스 정보를 확인할 때 사용|
|x (BSD)| 터미널에 종속되지 않는 프로세스를 출력. 보통 a옵션과 결합해 사용|
|-x|사용자가 로그아웃 한 이후에도 실행중인 프로세스 출력|

특정 프로세스를 확인하는데 주로 grep과 함께 사용

그 중에서 `ps -ef`를 가장 많이 사용

---

### ps명령어와 ps가 보여주는 항목, 필드 의미

$ ps
> ps 명령어만 단독으로 사용했을 때의 결과
> 사용자와 관련된 프로세스를 출력

![ps](https://user-images.githubusercontent.com/95179732/170050031-118c79c4-62f5-4b10-8e23-d8b7ffca0559.PNG)

> 기본적으로 PID, TTY, TIME, CMD의 정보가 출력

> PID : 프로세스 번호
> 
> TTY : 프로세스가 연결된 터미널
> 
> TIME : 프로세스에 사용된 CPU 시간
> 
> CMD : 프로세스 실행 명령어

+ ps 항목

|항목|의미|항목|의미|
|:---:|:---:|:---:|:---:|
|USER|프로세스 소유자의 이름 (BSD 계열)|S, STAT|현재 프로세스의 상태 코드 (S: Sys V, STAT: BSD)|
|UID|프로세스 소유자의 이름 (SYSTEM V 계열)|TIME|총 CPU 사용 시간|
|PID|프로세스의 식별번호|COMMAND|프로세스의 실행 명령행|
|PPID|부모 프로세스 ID|STIME|프로세스가 시작된 시간 혹은 날짜|
|%CPU|CPU 사용 비율의 추정치 (BSD)|C, CP|짧은 기간 동안의 CPU 사용률 (C: Sys V, CP: BSD)|
|%MEM|메모리의 사용 비율의 추정치 (BSD)|F|프로세스의 플래그|
|VSZ|K 단위 or 페이지 단위의 가상메모리 사용량|PRI|실제 실행 우선순위|
|RSS|실제 메모리 사용량 (Resident Set Size)|NI|nice 우선순위 번호|
|TTY|프로세스와 연결된 터미널|||

---

### ps 명령어 사용 예시

$ ps ax
> 시스템에 동작중인 모든 프로세스를 보고 싶을 때 위와 같은 명령어를 사용해 BSD 포맷으로 출력 (UNIX에서는 주로 `ps -e`와 비슷)

![ps ax](https://user-images.githubusercontent.com/95179732/170055637-bd613a42-1582-4900-8734-b3afaba81c7e.PNG)

$ ps aux
> 시스템에 동작중인 모든 프로세스를 소유자 정보와 함께 다양한 정보를 출력 (BSD 포맷으로 출력)

![ps aux](https://user-images.githubusercontent.com/95179732/170056268-bebb2eb6-e0ea-4636-a062-c679145436f5.PNG)

$ ps -ef | more
> `ps -ef`는 System V 계열 옵션으로 `ps aux`처럼 시스템에 동작중인 모든 프로세스를 자세히 출력

> more 명령어는 추가로 한 페이지씩 화면에 출력되도록 사용

![ps -ef](https://user-images.githubusercontent.com/95179732/170056360-3a96987b-c80b-496e-9696-6ea8cdd0879b.PNG)

$ ps -el | head
> 긴 포맷으로 출력하고 싶을 경우 -l 옵션을 사용

> `ps -ef`에서 보이지 않았던 F, S, PRI, NI, ADDR~ 등등 더 많은 정보들이 출력

![ps -el](https://user-images.githubusercontent.com/95179732/170056830-f4a7f70c-d7e2-43a9-bd76-ada337f48445.PNG)

## jobs

작업이 중지된 상태, 백그라운드로 진행 중인 작업 상태, 변경 되었지만 보고되지 않은 상태 등을 표시함

+ 사용법

`jobs [옵션][작업명]`

`jobs -x command [args]`

+ ### 옵션

|명령어|설명|
|:---:|:---:|
|-l|프로세스 그룹 ID를 state 필드 앞에 출력|
|-n|프로세스 그룹 중에 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대해 한 행씩 출력|
|command|지정한 명령어를 실행|

+ ### 알 수 있는 세션의 상태 값

|상태|설명|
|:---:|:---:|
|Running|작업이 일시 중단되지 않았고 종료하지 않고 계속 진행 중|
|Done|작업이 완료되어 0을 반환하고 종료됨|
|Done(code)|작업이 정상적으로 완료되었으며, 0이 아닌 코드가 반환됨|
|Stopped|작업이 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 신호가 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 신호가 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 신호가 작업을 일시 중단|
|Stopped(SIGTTOU)|SIGTTOU 신호가 작업을 일시 중단|

## kill

프로세스에 특정한 signal을 보내는 명령어
> 일반적으로 종료되지 않는 프로세스를 종료 시킬 때 많이 

+ 사용법

`kill [옵션 or 시그널] PID`

`$kill -9 11`

+ 종류

|옵션 or 시그널|내용|
|:---:|:---:|
|1 SIGHUP(HUP)|Hang Up의 약자로 프로세스를 재시작시키는 시그널|
|2 SIGINT(INT)|Interrupt 실행을 중지|
|3 SIGQUIT(QUIT)|키보드 종료 [Ctrl] + [\]|
|9 SIGKILL(KILL)|무조건 종료, 즉 강제 종료시키는 시그널|
|15 SIGTERM(TERM)|Terminate의 약자로 가능한 정상 종료시키는 시그널|
|18 CONT|Continue. Stop등에 의해 정지된 프로세스를 다시 실행|
|19 STOP|무조건적, 즉각적 정지|
|20 TSTP|실행 정지 후 다시 실행을 계속하기 위해 대기시키는 시그널|
