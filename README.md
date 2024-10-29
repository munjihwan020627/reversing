# reversing


1. 프로그램 제어 명령어

start: 프로그램을 시작하며 초기 context 화면을 출력

r or run: 프로그램을 실행, 만약 브레이크포인트가 설정되어 있다면 브레이크포인트까지 실행

예제: run → 프로그램을 처음부터 실행

k or kill: 프로그램을 종료

예제: kill → 실행 중인 프로그램을 강제로 종료

2. 코드 실행 관련 명령어

s, step, n, next: 소스 코드 한 줄을 실행
s는 함수 내부로 진입하여 디버깅하고, n은 함수를 건너뛰고 다음 줄로 이동

예제:
s → 현재 줄을 실행하고 함수 내부로 진입
n → 현재 줄을 실행하고 함수는 건너뛰고 실행

si(step instruction), ni(next instruction): 어셈블리 명령어를 한 줄씩 실행
si는 함수 내부로 진입하고, ni는 함수 내부로 들어가지 않고 실행함

예제:
si → 어셈블리 한 줄을 실행하고 함수 내부로 진입.
ni → 어셈블리 한 줄을 실행하고 함수는 건너뜀

return: 현재 함수 실행을 종료하고, 리턴 값을 강제로 지정하여 함수 바깥으로 나감

예제: return 1 → 현재 함수의 리턴 값을 1로 설정하고 함수 종료

3. 변수 및 메모리 관련 명령어

info locals: 현재 함수의 지역 변수를 표시

예제: info locals → 현재 함수의 지역 변수 값과 이름을 확인

p or print: 변수 값이나 메모리 주소의 값을 출력

예제:
p 변수 → 변수의 값을 출력
p main → main 함수의 주소값을 출력

jump: 특정 행 번호로 점프하여 실행 위치를 변경

예제: jump 100 → 100번째 줄로 점프하여 계속 실행

signal SIGKILL: 프로세스에 종료 시그널을 보내 강제 종료

예제: signal SIGKILL → 현재 실행 중인 프로그램을 종료

set: 특정 메모리 주소에 값을 설정하고 변수 타입을 명시할 수 있음

예제: set {int}0xdeadbeef = 1234 → 주소 0xdeadbeef에 int 타입으로 값 1234를 저장

4. 프로그램 시작 명령어

gdb ./[프로그램이름]: 특정 프로그램을 디버깅 모드에서 실행

예제: gdb ./a.out → a.out 프로그램을 GDB로 디버깅

5. 디버거 제어 명령어

q, quit, or Ctrl + D: pwndbg를 종료

예제: quit → 디버깅 세션을 종료

Ctrl + C: 실행 중인 프로그램을 일시 중단

예제: Ctrl + C → 실행 중단 후 디버깅 상태로 바꿈

c or continue: 중단된 프로그램을 이어서 실행

예제: continue → 중단된 프로그램을 다시 실행

6. 브레이크포인트 관련 명령어

b or breakpoint: 브레이크 포인트를 특정 함수나 주소에 설정

예제:
b main → main 함수 시작 위치에 브레이크 포인트 설정
b *0xdeadbeef → 주소 0xdeadbeef에 브레이크 포인트 설정

i b, info b, or info breakpoints: 설정된 모든 브레이크 포인트를 확인

예제: info breakpoints → 현재 설정된 모든 브레이크 포인트 출력

d or del: 특정 브레이크 포인트를 삭제하고, 번호를 지정하지 않으면 모든 브레이크 포인트를 삭제

예제:
del 1 → 브레이크 포인트 번호 1 삭제
del → 모든 브레이크 포인트 삭제

7. 메모리 관련 명령어

x: 메모리의 특정 주소의 값을 확인

예제: x/10x 0xdeadbeef → 주소 0xdeadbeef에서 10개의 값을 헥사 형식으로 출력

call: 특정 함수를 호출하고 인수를 지정

예제: call func(1, 2) → func 함수에 1과 2를 인수로 넣고 호출

1. 메모리 관련 명령어

hexdump: 메모리 주소의 데이터를 헥사 형식으로 덤프하여 메모리 내용을 파악할 수 있음

예제: hexdump 0xdeadbeef → 주소 0xdeadbeef부터의 메모리를 헥사 덤프로 출력

telescope: 특정 메모리 주소를 포인터 체인으로 따라가며 확인할 수 있음

예제: telescope $esp → 스택 포인터(esp)부터 시작해 포인터 체인을 따라가며 메모리 값 출력

vmmap: 프로그램의 가상 메모리 맵을 출력, 메모리 보호 권한도 함께 보여주고 섹션별 메모리 영역을 쉽게 파악할 수 있음

예제: vmmap → 메모리 맵 정보 표시

find: 특정 값이나 문자열을 메모리 전체에서 검색

예제: find 0xdeadbeef, +0x1000, "Hello" → 주소 0xdeadbeef부터 0x1000 바이트 범위 내에서 "Hello" 문자열 검색

2. 힙 분석 명령어

heap: 현재 프로그램의 힙 상태를 분석해 출력, 힙 영역의 할당 상태와 구조를 쉽게 파악할 수 있음

예제: heap → 힙의 전체 구조와 상태 출력

arena: 현재 힙 아레나의 정보를 표시

예제: arena → 기본 힙 할당 정보 출력

bins: fast, small, large 등 다양한 힙 빈(bins)의 상태를 표시, 오버플로우 취약점 분석 시 유용

예제: bins → 모든 힙 빈의 정보 출력

fastbins, smallbins, largebins: 힙 메모리 관리 시 사용하는 개별 빈 목록을 보여줌

예제: fastbins → fastbin 목록 확인

3. ROP 및 익스플로잇 명령어

rop: 현재 바이너리에서 ROP(Return-Oriented Programming) 가젯을 찾음, ROP 체인 제작 시 유용

예제: rop → 바이너리 내에서 사용 가능한 ROP 가젯 목록 출력

ropper: 여러 바이너리에서 ROP 가젯을 찾고 분석

예제: ropper --file a.out → a.out 파일에서 ROP 가젯을 찾음

4. 레지스터 및 디버깅 정보 관련 명령어

reg: 모든 레지스터의 현재 값을 출력

예제: reg → 레지스터 전체 값을 표시하여 디버깅 상태를 파악

context: 프로그램의 전체 컨텍스트를 출력

예제: context → 프로그램의 전체 디버깅 정보를 요약하여 출력

context code, context regs, context stack, context mem: 각기 코드, 레지스터, 스택, 메모리 정보를 개별적으로 출력

예제: context stack → 스택 상태만 출력

5. 기타 유용한 명령어

shellcode: 지정한 아키텍처에 맞는 쉘코드를 생성

예제: shellcode i386.linux.sh → x86 리눅스용 쉘코드 생성

aslr: Address Space Layout Randomization (ASLR)을 켜거나 끔

예제: aslr off → ASLR을 비활성화

elfheader: ELF 헤더 정보를 출력합니다.

예제: elfheader → ELF 바이너리의 헤더 정보 표시

searchmem: 특정 문자열이나 값을 메모리에서 찾음

예제: searchmem "/bin/sh" → 메모리에서 "/bin/sh" 문자열을 검색

got, plt: GOT (Global Offset Table)와 PLT (Procedure Linkage Table) 테이블의 정보를 출력

예제:
got → 바이너리의 GOT 정보를 출력
plt → 바이너리의 PLT 정보를 출력
