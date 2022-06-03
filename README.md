# 오픈소스SW개론 과제2
---
## 1. 리눅스 명령어

**1. top**

* table of processess 의 약자
* 유닉스 계열 시스템에서 프로세스 목록을 CPU 사용률이 높은 것부터 보여주는 프로그램  
* 시스템의 프로세스와 메모리 사용 상태를 일정 간격으로 업데이트하여 화면에 출력

### 사용 방법

* top 옵션

|옵션|설명|
|---|---|
|-b|배치모드 옵션|
|-d + [초]|지정한 시간(초)의 간격으로 정보를 업데이트하여 출력|
|-n + [주기]|지정한 주기 마다 정보를 업데이트하여 출력|
|-p + [pid]|지정한 프로세스 ID(pid)의 정보만 출력|

* top 실행 후 명령어

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

#### top 실행화면 

![top 실행화면](https://user-images.githubusercontent.com/104612916/171825876-ad779645-9e73-4e72-b942-6483cfbad296.jpg)

1. 첫번째 행 : 시스템의 부하율

2. 두번째 행 : 프로세스들의 종합적인 상황
 
3. 세번째 행 : CPU의 사용 및 실행 상태

4. 네번째 행 : 실제메모리의 상태

5. 다섯번째 행 : 스왑메모리의 상태

6. 여섯번째 행 : 전체 개별프로세스들의 시스템 자원 사용현황과 실행상태


**2. ps**

* process status 의 약자
* 현재 실행중인 프로세스 목록과 상태를 확인할 수 있는 명령어
* ps의 옵션은 System V, BSD, GNU에 따라 결과가 다르게 나타나고 표기법 차이도 존재
* 원하는 프로세스의 상태를 출력하려면 **정확한 옵션 사용이 중요**

### 사용 방법

