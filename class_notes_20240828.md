인터럽트랑 풀링을 배울것임.

인터럽트는 중간에 끼어서 가로채는 것임. 

왜 인터럽트가 중요하나? 프로그램이 동작 중일때 키보드로 타이핑을 하면 어떻게 알아먹고있는지? 미리 약속된 신호를 보내면 됨. 그게 인터럽트임. 

폴링 POOLING 어떤 이벤트(사건)을 계속 기다리는 것. 소프트웨어가 기다리는 것. 예시는 메일 시스템. 일정한 주기로 메일이 왔는지 감지함. 하긴 실시간으로 할 필요가 없지. 서버도 풀링에 가깝다고한다네.

인터럽트 INTERUPT 이벤트가 발생되면 어딘가(키보드 마우스)에서 약속된 신호를 보냄 → 신호가 CPU로 보냄. 인터럽트도 하드웨어 인터럽트, 소프트웨어 인터럽트로 나뉨 분류가 2개. 하드웨어 인터럽트는 입력장치에서 발생한 약속된 신호를 CPU로 전달함. CPU가 계속 감시하지 않고 신호가 오면 알아채고 확인함. 택배왔다고 알림오면 나가서 받는것이지.  풀링은 택배를 계속 기다리는 것( WAIT)처럼 CPU가 계속 기다림. 소프트웨어 인터럽트는 커널 단에서만 신호를 처리하지. 주체가 CPU, 커널로 다르다! A란 소프트가 동작하는데 동작이 잠시 멈추면 CPU에서 대기하라는 신호를 보낸다. 인터럽트 종류는 키보드, 마우스, 터치패널 인터럽트 등이 있음. CPU 속에도 하드웨어 인터럽트가 있다. 타임 인터럽트라고 한다. 시간초 올라가는 기능이 달려있음(그래서 가끔 시간이 맞지않습니다 라는 오류가 뜬거 시간이 맞지않는거지 시간이 계속 흐르는거임). 타임 인터럽트의 가장 중요한 역할은? 바로! 클럭을 조정하는 기능! 이것을 타임 인터럽트가 한다! CPU 동작시간을 보장하는 게 타임 인터럽트. 1클럭은 명령어가 수행되는데 걸리는 시간인데, 이 시간 정보를 타임 인터럽트가 제공함.

소프트웨어 인터럽트는 갑자기 프로그램 중지됬을때. 

하드웨어 - 키보드 눌러서 하드웨어-커널-CPU—가서 영향

소프트웨어 - 커널-프로그램-커널-소프트웨어로 신호를 줌. 녹화 저작권 프로그램은 프로그램 감지하면 그 프로그램 중지 인터럽트를 녹화 프로그램으로 주는거지.

CPU,메모리,SSD도 고유한 클럭에 대한 시간이 존재함.

→CPU 클럭에 맞춰서 동기화를 함. CPU가 가장 빠르기 때문(CPU기준 1클럭이라면, RAM은 2클럭은 1클럭 취급하고 SSD가 4클럭이면 1클럭 취급함). 옛날엔 동기화 안했음. 클럭이 참 중요하지. 명령어 처리들이 전부 클럭 안에서 처리되기 때문임. 이걸 왜! 설명했냐면, 패치1클럭, 디코드1클럭, 익스큐트2클럭 다음에 인터럽트가 왔다면, ISR(인터럽트 서비스 루틴)이 끼어들어서 키보드 입력(INPUT)이 다음 클럭에 들어감. 그런다음 PC(프로그램 카운터)에 저장된 익스큐트가 다시 나와서 실행됨. PC는 인터럽트가 들어오면 프로세스의 주소를 저장하는 레지스터에 있음. 주소 코드를 저장하는거지. 클럭이 엄청나게 빨라서 실시간처럼 보임. 프로그램 카운터는 레지스트, 램에서 저장됨. 프로그램 실행하면 프로세스가 실행됨. 프로세스는 램에 올라감.

램에 프로세스1이랑 코드가 있고 전역벽수가 저장됨. 그담에 클래스나 함수같은걸 불러서 램에 스택처럼 차오름. 힙은 위에서 아래로 축적됨. 힙이랑 스택이 충돌하면 프로그램이 터짐(C언어). 파이썬은 가비지 콜렉터(GC)가 안쓸거같은거 없애버리기 때문에 메모리관리에 신경안써도됨. 경우에 따라서 방식을 달리 쓰면됨. GC는 정해진 시간에 쓰레기를 청소하기 때문에, 즉 중간에 실행되기 때문에 기존 프로그램이 멈춰가 처리를 못하는 경우가 발생함. 그리고 기껏 만들어둔거 쓸데없는거라 처리하기도함. 이런 메모리에 메모리 주소를 PC가 저장하고있으면 언제든지 프로세스 멈추고 인터럽트를 처리한 뒤 다시 메모리 주소를 가져와 프로세스 동작하면 됨.

왜 이런걸 배우냐면 메모리나 다른거 최적화를 위해서임. 어떤 구조로 짜야 더 빠르고 메모리 덜들고, 입력받았을 때 지연을 줄일 수 있겠나를 위해서임. 게임에서 쓰레드를 나눠 입력만 받는 쓰레드를 따로 돌리는 경우도 있음.  

프로그램 카운터는 그 프로그램의 실행 주소임. CPU가 연산도중 인터럽트가 들어오면 인터럽트 처리하고 연산을 계속함. ISR은 인터럽트 발생됬을때 실행되는 코드와 같음. 우리가 짤수는 있는데 기본적으로 짜여있음(키보드, 마우스). 게임 조작키 변경은 ISR이 아니래. 게임안에서 자체적으로 처리한데.

퀴즈

1.  인터럽트와 폴링의 차이는? 왜 중요한가?
2.  인터럽트는 소프트웨어랑 하드웨어 인터럽트로 나뉘는데 그 차이는?
3.  ISR은 뭐고 PC는 뭘까? 그들의 역할은?
4.  타임 인터럽트란 무엇인가? 왜 중요한가?
5.  인터럽트랑 폴링같은걸 배운 이유는?
- 정답
    1.  폴링 POOLING 어떤 이벤트(사건)을 계속 기다리는 것. 메일이 예시. 인터럽트 INTERUPT 이벤트가 발생되면 어딘가(키보드 마우스)에서 약속된 신호를 보냄. CPU가 일 하고 있는 도중에 신호가 발생하면 그걸 즉각적으로 처리해야 하기 때문에 중요함
    2.  하드웨어 인터럽트는 입력장치에서 발생한 약속된 신호를 CPU로 전달함. 소프트웨어 인터럽트는 소프트웨어에서 발생한 신호를 커널 단에서만 처리해 다른 소프트웨어에 영향을 줌.
    3.  ISR(인터럽트 서비스 루틴) 인터럽트가 발생됬을때 실행되는 코드 모음. PC(프로그램 카운터)는 인터럽트가 발생하기 전의 명령어 주소를 저장해 ISR이 끝나면 그 주소를 이용해 다시 명령어 주소로 찾아가는 용도다. 
    4.  CPU에 자체적으로 달려있는 시계. 다른 하드웨어와의 클럭을 동기화 하기 위해서 사용함
    5.  메모리나 다른거 최적화를 위해서임. 어떤 구조로 짜야 더 빠르고 메모리 덜들고, 입력받았을 때 지연을 줄일 수 있겠나를 위해서임