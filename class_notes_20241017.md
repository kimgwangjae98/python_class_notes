서버세팅하는거 보여준다고함(나중에). 네트워크설정까지한다고함.
역함수. 함수의 출력 y를 입력하면 함수의 입력 x를 출력하는 함수. 함수는 하나 입력시 하나 출력함. 역함수 될려면 함수에도 조건이 있음. 관계가 성립해야되는데 일대응 대응 함수일 때만 역함수가 존재함(함수의 입력3개 결과가 1개 출력이면, 역함수면 입력1개가 출력 3개로 나옴). 역함수 조건은 즉슨 일대응 대응이다. 역함수를 왜 배우는가? 신경망의 역전파에 쓰이기 때문임. 
logarism : 가파르다. 값의 변화가 크다. 지수함수의 역함수!
sigmoid function : 1/(1 + e^-x). 자주쓰임. 시그마 기호를 씀(동그란거)
다변수 함수 : 변수가 여러개인 함수
벡터 함수 : '방향+양' 이 변수인 함수. 즉, 입력값이 벡터인 함수. 벡터계산(내적,외적)필요. 방향이 존재하기 때문.
dx는 x를 끝없이 나눈다는뜻. ofoa : 편미분. 하나만 편들어서 미분. 라운드 기호를 사용함.
스칼라 : 크기만을 나타냄
벡터 : 크기+방향. vehere 에서 파생된 용어.백터도 좌표계처럼 표시한다(x1,x2). 2개 차원에 x1,x2요소가 들어가있다. 백터 x1, x2 합쳐서 x가 됨. 즉슨, 벡터를 분해 가능하다는 의미. T=전치. transpose. 반시계로 돌림, T붙으면 시계방향으로 돌림. 열로된 요소를 행으로 꿈. 크기가 1인 벡터 = 단위벡터(u)
단변수 벡터함수. f1(t), t=(1,2). 0-> f(u1,u2) = (2u1,3u2) 리스트 반환같이 나옴. 요소가2(크기+방향)이면 n차원 벡터. 벡터가 n차원이면 결과도 n차원으로 나와야됨. t = (u1,u2,u3,...,un) -> r(t) = (f1(u1), f2(u2), f3(u3),... fn(un)). 요소마다 또 각각의 함수가 존재하는거지. 
다변수 함수 : 그냥 변수가 여러개인 함수.
3차 함수 : 단변수(변수가1개). 지수가 최대 3.
3차원 함수 : 다변수(변수가3개). xyz
기본적으로 스칼라 함수는 변수 갯수가 차원이 됨(다변수-다차원).
벡터 함수는 변수의 요소 갯수에 따라 차원의 갯수가 달라짐. (다요소-다차원)
왜 y=f(x) 꼴로 쓰냐? X가 집합이기때문
삼변수 함수에서 한 변수가 고정되면 결과는 2차원 선이 나옴. 등고선처럼 나옴. 
다변수 벡터함수도 있음. 단, 차원이 같아야함. 다변수 스칼라 함수 * 일변수 벡터함수 = 다변수 벡터함수. x = (t1=v1,v2,v3), y=(t2=v1,v2,v3)... 그저 그뿐. 벡터들의 합으로 나오기 때문에 결과가 면으로 나옴. 각각 요소에 따른 함수를 가져야됨. f1(x,y) = x = v1,u1. f2(x,y) = y = v2,u2. 입력이 2개(u,v)라 결과가 면으로 나왔음. 입력이 1개였다면 결과가 선으로 나왔을것임.점이 모여 선으로, 선이 모여 면으로 결과가 나왔지. 요소갯수=함수갯수. 3변수 3요소 -> 덩어리(volume). 벡터함수에서 그래프의 형태가 결정하는 것은 변수의 갯수(점,선,면,덩어리...) 차원결정은 요소의 갯수. 함수 갯수는 요소갯수가 결정함.

스칼라 - 요소가 1개.    
단변수 스칼라 함수- 그래프차원결정은 변수갯수(그래프 형태도 결정 x,y->선)이 결정. 2차원
다변수            -                         (그래프 형태도 결정 x,y,z->면)이 결정. 3차원

벡터 - 구성요소는 크기와 방향. 요소 갯수가 차원, 함수갯수을 결정. 벡터(변수) 갯수가 그래프 형태를 결정. 
일변수 벡터 함수- F(v)=u, v=(v1,v2). 차원은 2차원(v1,v2), 그래프 형태는 선(v,u). 함수는 2개(v1,v2)
F(v,u)= k, v=(v1,v2,v3). 벡터(변수) 3개, 요소 3개 , 함수 3개, 3차원 면 
벡터를 요소로 나눈 이유는 계산 편하게 하기 위해서임.

합성함수. 합성을 해주는 함수임. 콘볼루션 연산을 할 때 쓰여서 배움. 소프트맥스는 일변수 벡터 함수. 자연상수e는 정규화 할려고 들어감. 한값만 높으면 제대로 확률 안나와서 그럼. 그런데 책에선 다변수 벡터 함수라고 함. 아까전에 z의 요소들을 각각 벡터라고 본거지. k개 벡터들의 함수

가중치를 조정하면 정답에 가까워지는 값을 찾을 수 있고 그게 딥러닝이다.


우분투
Ubuntu 24.04.1 LTS (롱텀서비스) 다운받고
https://rufus.ie/ko/ 에서 부팅 드라이버 만들기. 파일 시스템 : FAT32. 이게 리눅스도 되는 공통적이기 때문. 권장 설정 사용.
F2키로 바이오스 진입. BIOS탭 진입. 부팅구성.boot메뉴 들어가기 드라이버 옵션 우선순위를 USB로 선택해서 설치. save해서 설치 시작.
try or install 선택. 
우분투 한국어로 설치 추가 다운받는거 다 해주면 좋음. 수동 파티션- 파티션 만들기 - ext4, 마운트 위치:/efi, 크기 : 500MB(알아서 해줄거임). 그리고 그냥 파티션 추가 / 하면 다 됨. 계정은 맘대로. 컴퓨터 이름도 server로 하든가. 암호는 곡 외우고. 다른거 생략하고. 