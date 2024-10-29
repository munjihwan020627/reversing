###pwndbg 명령어 익히기


예제: kill → 실행 중인 프로그램을 강제로 종료

코드 실행 관련 명령어
s, step, n, next: 소스 코드 한 줄을 실행 s는 함수 내부로 진입하여 디버깅하고, n은 함수를 건너뛰고 다음 줄로 이동

예제: s → 현재 줄을 실행하고 함수 내부로 진입 n → 현재 줄을 실행하고 함수는 건너뛰고 실행

si(step instruction), ni(next instruction): 어셈블리 명령어를 한 줄씩 실행 si는 함수 내부로 진입하고, ni는 함수 내부로 들어가지 않고 실행함

예제: si → 어셈블리 한 줄을 실행하고 함수 내부로 진입. ni → 어셈블리 한 줄을 실행하고 함수는 건너뜀

jump: 특정 행 번호로 점프하여 실행 위치를 변경

예제: jump 100 → 100번째 줄로 점프하여 계속 실행


브레이크포인트 사용하기
b or breakpoint (line number) : 해당 line부분에 실행중일때 중단부분을 실행함
혹은 실행중 빨간 버튼 클릭
      

i b, info b, or info breakpoints: 설정된 모든 브레이크 포인트를 확인

예제: info breakpoints → 현재 설정된 모든 브레이크 포인트 출력

d or del: 특정 브레이크 포인트를 삭제하고, 번호를 지정하지 않으면 모든 브레이크 포인트를 삭제

예제: del 1 → 브레이크 포인트 번호 1 삭제 del → 모든 브레이크 포인트 삭제

context: 프로그램의 전체 컨텍스트를 출력

예제: context → 프로그램의 전체 디버깅 정보를 요약하여 출력

context code, context regs, context stack, context mem: 각기 코드, 레지스터, 스택, 메모리 정보를 개별적으로 출력

예제: context stack → 스택 상태만 출력

