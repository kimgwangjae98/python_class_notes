os 주요기능
프로세스 관리 = 스케줄링 이라고도 함. 동시실행 가능하게 관리함. 멀티코어랑 멀티프로세서, posix 등등이 들어감. 이것들은 스케줄러가 한다. cpu 디바이드 드라이버로 스케줄러가 있다는 점? IPC를 사용함. IPC는 파이프라인을 이용하지(명령어쪼갠거).  메세지 큐(선입선출 메모리구조)도 쓰고. 메세지큐는 알람에 사용하지. 프로세스 동기화도 사용함. 이건 mutex인데 급식에서 배식하는사람임. 사람(프로세스) 줄세우고 적당량 밥주는거지(자원관리).
메모리 관리는 메모리 디바이스 드라이버. 입출력 시스템 관리는 io 디바이스 드라이버. 윈도우에선 기본내장임. 파일 시스템 관리는 FS라고 줄여서 부름. FAT 같은거 파일 관리를 해주는 드라이버지. 보완 및 보호 기능은 TPM이라고 하는 암호화 칩씀. 이 암호화 칩이 2.0 최신형이어야 윈도우11깔림. 내컴은 이게 구버전 1.0이라 조건을 만족하지 못한다. 이런거였어?
사실 운영체제의 주요 기능은 커널의 주요기능임. 커널만 잘 만들면 잘 쓸수있음. 커널이 잘 돌아가면 무탈하다. 그래서 커널 잘 돌아갈때 건들면 안된다. 
흐름 : 하드웨어 배우고 OS역할 배우고 OS다룰수있는 법 배우면 하드웨어를 다룰수있다! 컴퓨터 구조로 HW를 배워서 어떻게 동작하는가? 를 배우고 운영체제SW로 커널을 어떻게 관리를 하는가? 를 배우고 사용자 영역에서 커널을 이용에서 자원을 다뤄보는법을 배시쉘 스크립트, 프로그래밍 언어로 배운다. 이렇게 배워야 프로그램을 더 잘 짤수있다!
리눅스는 커널이름이랑 운영체제이름이랑 같다고 보면됨.
시스템 호출 인터페이스는 시스템을 호출한다. OS 커널 서비를 요청하는 방법이지. 이거 이용해 커널에 명령가능. 커널에 있는 CPU 드라이버를 제어하는 C언어 FORK 라이브러리가 있음. 스케줄러에 직접 관여할 수 있지.
운영체제 구조에서 모놀리식 구조는 한 덩어리 구조임. 다 섞여있음. 윈도우임. 기능이 워낙 많아서 그럼. 모듈형 구조는 기능마다 덩어리가 나뉨. 리눅스임. 업데이트 적용이 실시간으로 가능해서 안꺼도됨. 

커널은 HW를 다루게 해주는 SW임. 드라이버와 같지. 커널은 ISA를 직접 다루게 해주는 디바이스 드라이버로 이루어짐. 파이썬이랑 C언어로 커널 제어 가능. 프로세스 관리랑 메모리 관리가 주요함.
이제부터 커널을 다루는 방법을 배움. 배시쉘같은거. 
C언어는 더이상 안씀. 자원에 직접적으로 접근할 수 있기 때문에. 빨라서 좋은데 복잡한 코드에선 오류가 있을 가능성이 커 위험하기 때문에 안씀. 커널간 충돌을 유발하는 오류가 나타날 수 있기 때문. 물론 임베디드시스템 때문에 C언어를 씀. 직접접근할수있기 때문. 
CSV 나 TXT 파일도 파이썬이 커널 건들여서 작성해줌. OS라이브러리같은경우지...
임베디드 있냐 컴파일러 있냐 등등 다 물어봐야함. 

프로세스는 실행 중인 프로그램의 인스턴스임. 프로그램 실행하면 램에 하나 올라감. 똑같은 프로그램을 5개 실행하면 인스턴스 5개 실행한거고, 이는 5개의 프로세스를 생성한 것과 같다. 우리가 짠 코드가 램 위에 복제되어 올라가는거지. 하나 올라가면 1개 프로세스 만들어진거지. 클래스의 인스턴스 개념과 비슷하다. 멀티 프로세서는 제작가가 여러개의 프로세스를 만들어 한덩이로 만든거임. 프로세스는 생성은 복제되서 램에 올라간 상태이고, 준비는 실행전 체크상태. 실행 대기 종료는 말 그대로임. 대기는 인터럽트 상태에서 사용됨. 응답없음은 코드 충돌이 일어난 실행상태임. 이런 오류나면 저장장치에서 코드 불러와 복구를 시도함. 멀티 프로세스는 프로그램이 여러개 실행되는 방식. 1~4번 코드가 각각 실행되면 4개 프로세스가 동시에 돌아가서 멀티 프로세스임. 주로 제작가가 멀티 프로세스를 정의함. 멀티 프로세스는 빠르게 만들려고 만듬.  예제처럼 코드내에서 여러개의 프로세스로 나눠줄수있음. 멀티코어를 쓰기위해 멀티프로세스를 생성했음. 옛날 국산게임은 단일프로세스라서 단일코어만 씀. 그러니까 프로세스 = 단 블럭. 멀티프로세스 = 작은블럭 뭉쳐서 만든 블럭. 프로세스=프로세서 발음차이. 멀티스레드는 프로세스를 스레드로 나눠서 연산하는거임. 멀티스레드 멀티프로세스 동시에 사용가능. 스레드 쓰면 함수가 무작위 순서로 동시에 실행됨. 스케줄러에 의해 결정됨. 멀티스레드는 한개의 코어에서 활용됨. 스레드 여러개를 아주 빠르게 순서대로 처리하기에 동시처럼 보이는거지. 그걸 위해 코어가 1개 스레드 일 때보다 여러 스레드 일 때 열일하지.  멀티스레드는 한 프로세스내의 자원만 공유함.  중국인 한국인 마라탕 국밥 으로 설명해주셨지. 자꾸 동시에 집착하면 안되. 동시처럼 보이는거지. 그래서 동시취급인거고.

정리하자면, 파이프라인은 그냥 명령어 순서를 나눈거고, 멀티스레드는 코어 하나 갈궈서 일 동시에 처리하도록 만드는 거고, 멀티프로세스는 프로세스마다 코어가 많으면 각자 배분해서 코어에 일시키는거지. 

직접 실습해봤는데 꽤 괜찮다. 챗 gpt가 최고야. 다만 스레드 수가 2배가 되어도 시간 반으로 정확히 절반으로 단축되지는 않는다. 다큰 코드를 때문이겠지. 그래도 자원충돌만 없으면 엄청난 시간단축 효과를 누릴 수 있을 것이다. 4초가 걸리던 문제가 0.5초 걸리더라. 아니, 거진 그래도 두배 늘리면 절반저도가 줄어드네. 무섭다. 이렇게 파이썬으로 직접 운영체제, 커널을 건들여서 cpu를 제어해봤음. 자원관리만 조심하면 HW의 성능을 최대한 사용하여 성능을 높일 수 있음을 직접 확인하였음.

나중에 정리해보기. 
정리할 때 마인드맵 같은걸 그려서라도 내가 배운 지식들을 연결해야됨. 

[강사 이준기] [오후 4:38] 내일 11월 27일 수요일 오전에 쉘 스크립트 수업 한다음에 컴퓨터구조 및 운영체제 기초, 리눅스 시스템 익히기 (with Ubuntu) 시험 치도록 하겠습니다
[강사 이준기] [오후 4:39] 총 8문제가 나오면 흐름을 익히는 곳에서 문제가 나옵니다. 노션에 내용은 컴퓨터구조 및 운영체제 ( feat. 어렵게 배워보자 ) 에서 나옵니다
