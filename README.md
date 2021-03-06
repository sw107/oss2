# 오픈소스SW개론 과제2
---
## 1. 리눅스 명령어

### 1. top

* table of processess 의 약자
* 유닉스 계열 시스템에서 프로세스 목록을 CPU 사용률이 높은 것부터 보여주는 프로그램  
* 시스템의 프로세스와 메모리 사용 상태를 일정 간격으로 업데이트하여 화면에 출력

#### 사용 방법

**top 옵션**

|옵션|설명|
|---|---|
|-b|배치모드 옵션|
|-d + [초]|지정한 시간(초)의 간격으로 정보를 업데이트하여 출력|
|-n + [주기]|지정한 주기 마다 정보를 업데이트하여 출력|
|-p + [pid]|지정한 프로세스 ID(pid)의 정보만 출력|

**top 실행 후 명령어**

|명령어|설명|
|---|---|
|space bar|정보 업데이트|
|shift + p|CPU 사용률이 높은 프로세스 순서대로 표시|
|shift + m|메모리 사용률이 높은 프로세스 순서대로 표시|
|shift + t|프로세스가 돌아가고 있는 시간 순서대로 표시|
|k|프로세스 종료(k 입력후 종료할 PID입력, signaldms 9로 입력|
|a|메모리 사용량에 따라 정렬|
|b|Batch 모드|
|i|idle 또는 좀비 상태의 프로세스는 표시되지 않음
|c|command 뒤에 인자값 표시|
|l|uptime line(첫번째 행)을 표시/비표시|
|s|출력할 정보의 업데이트 시간을 지정|
|z|출력색상 변경|
|d|설정된 초 단위로 업데이트하여 출력|
|1|CPU 코어별로 사용량 표시|
|h|도움말 표시|
|q|top 종료|

##### top 실행화면 

![top 실행화면](https://user-images.githubusercontent.com/104612916/171825876-ad779645-9e73-4e72-b942-6483cfbad296.jpg)

|행|설명|
|---|---|
|첫번째 행|시스템의 부하율|
|두번째 행|프로세스들의 종합적인 상황|
|세번째 행|CPU의 사용 및 실행 상태|
|네번째 행|실제 메모리의 상태|
|다섯번째 행|스왑메모리의 상태|
|여섯번째 행|전체 개별프로세스들의 시스템 자원 사용현황과 실행상태|


### 2. ps

* process status 의 약자
* 현재 실행중인 프로세스 목록과 상태를 확인할 수 있는 명령어
* ps의 옵션은 System V, BSD, GNU에 따라 결과가 다르게 나타나고 표기법 차이도 존재
* 원하는 프로세스의 상태를 출력하려면 **정확한 옵션 사용이 중요**

#### 사용 방법

**ps 옵션**

|옵션|설명|
|---|---|
|-A|모든 프로세스 출력|
|a(BSD)|터미널과 연관된 프로세스 출력, 보통 x옵션과 연계|
|-a|세션리더를 제외하고 데몬 프로세스처럼 터미널에 종속되지 않은 모든 프로세스 출력|
|-e|커널 프로세스를 제외한 모든 프로세스 출력|
|-f|풀 포맷으로 보여줌, 유닉스 스타일로 출력해주는 옵션, UID, PID, PPID 등이 함께 표시|
|-l(sys V), l(BSD)|긴 포맷으로 보여줌, 프로세스의 정보를 길게 보여줌, 우선순위와 관련된 PRI와 NNI값을 확인가능|
|-o|출력 포맷 지정, pid, tty, time, cmd 값 등을 지정 가능|
|-M|64비트 프로세스들을 보여줌|
|-m|프로세스 뿐만 아니라 커널 스레드도 보여줌|
|-p|특정 PID를 지정할 때 사용|
|-r|현재 실행 중인 프로세서를 보여줌|
|u(BSD)|프로세스의 소유자를 기준으로 출력|
|-u|특정 사용자의 프로세스 정보를 확인할 때 사용. 사용자를 지정하지 않으면 현재 사용자를 기준으로 출력|
|x(BSD)|데몬 프로세스처럼 터미널에 종속되지 않는 프로세스를 출력. 보통 a 옵션과 결합하여 사용|
|-x|로그인 상태에 있는 동안 아직 완료되지 않은 프로세서들을 보여줌|

* 특정 프로세스를 확인하는데 주로 grep와 함께 사용
* System V 계열에서는 ps-ef를 가장 많이 사용 (ps -ef |grep '프로세스명')
* BSD 계열에서는 ps aux를 가장 많이 사용 (ps aux | grep '프로세스명') 

#### 실행 예시

**System V 계열**
* ps -ef : 모든 프로세스를 풀 포맷으로 출력
* ps -ef | grep '프로세스명' : '프로세스명'의 프로세스 구동 확인

**BSD 계열**
* ps aux : 실행 중인 모든 프로세스 확인
* ps auxf : 실행 중인 프로세스를 트리구조로 보여줌
* ps auxfww : 실행 중인 프로세스를 트리구조 + 모든 실행 중인 옵션 확인 가능 


#### 실행 화면

![ps 화면](https://user-images.githubusercontent.com/104612916/171854617-092516fe-b5cc-4394-a414-12c721bda5b5.jpg)

|행|내용|
|---|---|
|UID|실행유저|
|PID|프로세스 ID|
|PPID|부모 프로세스 PID|
|C|CPU 사용량|
|STIME|Start Time|
|TTY|프로세스 제어 위치 (콘솔 : tty1, 원격 : pts/1)|
|TIME|구동시간|
|CMD|실행 명령어|


### 3. jobs

* 백그라운드로 실행되는 작업목록(작업번호, 상태, 명령어)을 보여주는 명령어
* 작업번호는 PID와 별개로 별도로 부여되는 번호
* kill 명령어와 연관하여 프로세스를 종료시킬 수 있음(kill %작업번호)

**작업 상태**

|상태|설명|
|---|---|
|Running|작업 진행중|
|Done|작업 완료, 0을 반환|
|Done(code)|작업 종료, 0이 아닌 코드 반환|
|Stopped|작업 일시 중단|
|Stopped(SIGTSTP)|SIGTSTP 시그널이 작업을 일시 중단|
|Stopped(SIGSTOP)|SIGSTOP 시그널이 작업을 일시 중단|
|Stopped(SIGTTIN)|SIGTTIN 시그널이 작업을 일시 중단|
|Stopped(SIGTTOu)|SIGTTOU 시그널이 작업을 일시 중단| 


#### 사용 방법

**옵션**

|옵션|설명|
|---|---|
|-l|프로세스 그룹 ID를 state 필드 앞에 출력|
|-n|프로세스 그룹 중 대표 프로세스 ID를 출력|
|-p|각 프로세스 ID에 대해 한 행씩 출력|
|command|지정한 명령어 실행|


### 4. kill

* 프로세스에 특정한 signal을 보내는 명령어
* 일반적으로 종료되지 않는 프로세스를 종료 시킬 때 많이 사용
* kill [옵션 or 시그널(번호 또는 이름)] PID 의 형태로 사용

#### 사용 방법

**옵션**

|옵션|설명|
|---|---|
|-l|signal 의 종류를 출력(1~64)|
|-1(SIGHUP)|연결 끊기|
|-2(SIGINT)|인터럽트|
|-3(SIGQUIT)|종료|
|-4(SIGILL)|잘못된 명령|
|-5(SIGTRAP)|트랩 추적|
|-7(SIGBUS)|버스 에러|
|-8(SIGFPE)|고정 소수점 예외|
|-9(SIGKILL)|죽이기|
|-15(SIGTERM)|소프트웨어 종료 시그널|
|-19(SIGSTOP)|정지|


## 2. vim 에디터 매크로

* 매크로는 특정한 움직임 또는 입력을 키에 저장함으로써 단순하면서 반복되는 동작을 쉽고 빠르게 해주는 것
* vim 에서는 명령어 모드에서 q를 사용하여 매크로를 저장 가능

### 매크로 저장 순서

1. q + 문자(a ~ z) : 문자(a ~ z)키에 recording 시작
2. 반복을 원하는 동작
3. q : recording 종료
4. @ + (1에서 설정한 문자) : 매크로 1회 실행   
  *@@ : 방금 실행한 매크로 실행, (숫자) + @ + 설정한 문자 : 매크로 (숫자)회 실행*

### 매크로 예시

1. vim 에디터에서 1입력 
2. 매크로 설정<q a 숫자 1 복사후 다음줄에 붙여넣기 ctrl+a(숫자 증가) q>
3. 매크로 실행 -> 숫자 1씩 증가하며 입력

---
