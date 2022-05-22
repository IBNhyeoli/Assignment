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
