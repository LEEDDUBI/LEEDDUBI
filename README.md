# 오픈소스SW개론 - README 파일 작성하기
## 리눅스 명령어

### 1. top
  - 리눅스 및 유닉스 시스템에서 실시간으로 시스템의 프로세스 상태와 시스템 리소스 사용량을 모니터링 하는 도구임.
  - 리눅스 시스템의 CPU 사용량, 메모리 사용량 등 전반적인 상황을 실시간으로 모니터링할 수 있는 명령어임.
  - 명령어를 실행하면 최상단 5줄에 top, Tasks, %Cpu(s), MIB Mem, MIB Swap 정보가 우선적으로 출력됨.
    → 첫번쨰 라인의 top은 순서대로 System time, System 구동 시간, 서버에 접속한 유저 수, load average를 보여줌.
  - 명령어 실행 시 시스템 요약 정보, 작업 요약 정보, 프로세스 목록 등 표시됨.   
  - 시스템 관리와 성능 모니터링에 매우 유용함
  - 다양한 옵션과 키를 사용하여 필요한 정보를 효율적으로 확인할 수 있음.
  - < img src="C:\\Users\\이수빈\\OneDrive\\바탕 화면\\top 명령어" width = "1920" height= "1080">

#### top 실행 후 명령어

- shift + p : cpu 사용률을 내림차순으로 보여줌.
- shift + m : 메모리 사용률을 내림차순으로 보여줌.
- shift + t: 프로세스가 돌아가고 있는 시간순으로 보여줌.
- k: kill.k 입력 후 PID 번호를 작성함.
- f: sort filed 선택 화면이 나옴.(q를 누르면 RES순으로 정렬)
- a: 메모리 사용량에 따라 정렬함.
- b: Batch 모드로 작동함.
- 1: CPU Core별로 사용량을 보여줌.
  
    
### 2. ps
- 현재 실행 중인 프로세스 목록과 상태를 보여줌.
- 정확한 옵션 사용이 중요함. (ex: a와 -a의 옵션이 다른 것처럼)
- ps[option]의 사용

  #### ps 옵션들
  
 - -A: 모든 프로세스를 출력함.
 - a: 터미널과 관련된 프로세스를 출력함.
 - -a: 세션 리더를 제외하고 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스를 출력함.
 - -e: 커널 프로세스를 제외한 모든 프로세스를 출력함.
 - -f: 풀 포맷을 보여줌.
 - -o: 출력 포맷을 지정하는 옵션(pid,tty,time,cmd)
 - -m: 64비트 프로세스를 보여줌.
 - -p 특정 PID를 지정할 때 사용함.
 - -r: 실행 중인 프로세스를 보여줌.
 - -u:특정 사용자의 프로세스 정보를 확인할 때 사용함. (사용자를 지정하지 않으면 현재를 기준)
 - -x: 로그인 상태에 있는 동안 아직 완료되지 않은 프로세스를 보여줌.

#### ps 명령어 사용 예시
- ps 단독 사용
   -기본적으로는 프로세스 번호(PID), 프로세스가 연결된 터미널(TTY), TIME, CMD이 출력.
- ps ax 사용
   -시스템에 동작 중인 모든 프로세스를 보고 싶을 때 사용(PID,TTY,STAT,TIME,COMMAND 출력)
- ps aux 사용
   - 시스템에 동작 중인 모든 프로세스를 소유자 정보와 함께 다양한 정보를 같이 출력(특정 프로세스는 ps aux|grep apache)

 #### ps 명령어 사용 시 나타낼 수 있는 항목
 - USER: BSD계열에서 나타나는 항목으로 프로세스 소유자의 이름
 - UID:SYSTEM V계열에서 나타나는 항목으로 프로세스 소유자의 이름
 - PID:프로세스의 식별번호
 - PPID:부모 프로세스 ID
 - %CPU:CPU 사용 비율의 추정치(BSD)
 - %MEM:메모리의 사용 비율의 추정치(BSD)
 - VSZ:K단위 또는 페이지 단위의 가상메모리 사용량
 - RSS:실제 메모리 사용량(Resident Set Size)
 - TTY:프로세스와 연결된 터미널
 - S, STAT:현재 프로세스의 상태 코드 (S: Sys V, STAT:BSD)
 - TIME:총 CPU 사용 시간
 - COMMAND: 프로세스의 실행 명령행
 - STIME:프로세스가 시작된 시간 혹은 날짜
 - C, CP:짧은 기간 동안의 CPU사용률(C: Sys V, CP:BSD)
 - F:프로세스의 플래그
 - PRI:실제 실행 우선순위
 - NI:nice 우선순위 번호


   -----------------------------------------------
   ps와 top의 차이점
   -----------------------------------------------
   - ps는 __ps한 시점에 proc에서 검색한 cpu 사용량
   - top은 __proc에서 일정 주기로 합산해 cpu 사용률 출력
   -----------------------------------------------

### 3. jobs
- 백그라운드에서 실행된 프로그램이나 작업 목록을 보여주는 명령어임.
- jops[옵션] [작업번호] 명령어로 사용함

  #### jobs 사용법
  ##### jobs로 출력되는 백그라운드 작업의 상태값
_________________________________
  상태   |  설명
----------------------------------
 Running | 작업이 계속 진행 중임
-----------------------------------
 Done    | 작업이 완료되어 0을 반환
-----------------------------------
 Done    | 작업이 종료 되었으며 0이 아닌 코드를 반환
 ------------------------------------
 Stopped | 작업이 일시 중단
 ------------------------------------
 Stopped (SIGTSTP) | SIGTSTP 시그널이 작업을 일시 중단
 ------------------------------------
 Stopped (SIGSTOP) | SIGSTOP 시그널이 작업을 일시 중단
 ------------------------------------
 Stopped (SIGTTIN) | SIGTTIN 시그널이 작업을 일시 중단
 ------------------------------------
 Stopped (SIGTTOU) | SIGTTOU 시그널이 작업을 일시 중단
 ----------------------------------------------
______________________________________________________
- kill


