커리큘럼 과정을 간단히 설명함

컴퓨터 사이언스(컴퓨터구조, 반도체) - 운영체제(드라이버, 커널) - 수학(편미분,그레디언트, 선형대수학, 행렬, 기초개념 등) - 머신러닝(지도학습-sum, linearegession, 비지도학습-dbsm,gmm) - 딥러닝(비전opencv, 오디오melspec, 센서earlyfusion, 모델-함수같은거. 구조를 배움. CNN RNN 트랜스포머 LMM 등등) - 파이썬, C, C++, SVM(git), virtualenv(가상환경. 아나콘다, docker), ROS2(Robot Operating System). 사실 다 한꺼번에 배움. 다 이어져있거든. 프로그래밍 언어는 다 알려주진 않고 미리 공부를 좀 하고 궁금한 점을 질문하는 형식이 좋음. gpt활용하면 더욱 좋고. 

→ 이론 대충 배웠으니 자동차 개론 → 자율주행, 체계0to5, 단계1to3, 방법론how → project(텔러스, TTNG, EINTEL, IGIS, 시뮬, 로보아이) + 개인프로젝트. 프로젝트는 대충 1주일 정도. 전 기수들도 다 할수 있었데. 그럼 우리도 할 수 있지 암. 

싸피 수준으로 알차게 배울 예정이니 기쁘게 임하자. 싸피 못되서 아쉬웠는데 잘됬다.

컴퓨터 구조는 완료했음! OS도 웬만하면 다 설명했고 커널, 쉘, 유저 인터페이스, GUI CUI도 다 했음. 리눅스도 할거임. 오늘 리눅스 설명할거임.

커널은 시스템의 모든 자원(프로세스, 메모리, 하드웨어, 파일)을 관리하고, 사용자와 하드웨어 간의 인터페이스를 제공.

커널 위에 쉘(사용자가 컴퓨터랑 소통할수 있게 해주는 것)이 있음. 

퀴즈 : 우분투는 무슨 쉘을 쓸까? →벳시쉘! 

centos는 t쉘. 쉘에 치는 명령어를 모아둔 것이 쉘스크립트. 쉘스크립트로 우리가 명령한 것들 한꺼번에 수행할 수 있게 해줌.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/914cd412-d6e9-4c46-8afb-88e9c6594671/9078d94c-3ff3-4e4a-acb8-44e00acd0e66/image.png)

컴파일러는 번역기. 우리가 쓴 코드 컴퓨터가 알아먹을 수 있는 언어로 바꿔줌. 벳시쉘도 컴파일러다! 그래서 쉘스크립트 만들어 쓰면 효율적이다. 윈도우에서 ~~.bat 파일은 바로 명령어창 뜨고 쫙 실행됨. 리눅스는 ~~.sh 파일임. ~~.mzk 파일도 있음.

드라이버 도 중요

환경변수 도 중요- 이건 뭐지?

환경변수(environment variable)는 환경이 쉘, 즉 쉘에 변수를 미리 지정해 주는것. import a,b,c… 이런것들을 미리 시스템에 박아두는것. 초기값이라는거지. path도 있는데 그 경로를 다 탐색해보라고 하는거. 인스톨은 어느 경로에 그 프로그램 까는거. 그래서 쉘에 파이썬 실행하라 명령어 치고 나서 환경변수로 파이썬 파일 실행 경로를 적어야됨. 일정한 프로그램을 계속 실행할려면 환경변수를 미리 지정해두고(사용할 코어 수 같은거) 실행하면 효율적으로 다를 수 있다. 유저만 쓸수있는 지역변수

os마다 컴파일러가 달라서 os마다 사용할수 있는 프로그램이 다름. 윈도우에서 잘 돌아가던 프로그램이 리눅스에선 안돌아가는 경우가 있어서 윈도우용, 리눅스용으로 프로그램이 개발하거나, 전부 통합한 프로그램도 있음. 

x86, x64같이 구분되는건 다 미리 컴파일이 된거(~.dll들)이고 exe는 코드랑 컴파일러가 같이 담겨있음. 

패키지 만들거면 그냥 코드짜서 배포하면 된다.

레지스트는 커널이 작동할 때 미리 지정한 변수들

환경변수는 쉘이 작동할 때 미리 지정한 변수들 

레지스트를 수정할 수 있음. 왜냐? 사용자마다 다른 환경이기 때문. 

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/914cd412-d6e9-4c46-8afb-88e9c6594671/e985d218-a299-4e1d-b34c-96aeaac6858f/image.png)

퀴즈 : 왜 윈도우는 업데이트 할때마다 껐다 킬까? 부트매니저! efi영역에서 불러오는 방식이 달라서 그럼. 부팅 가능한 영역을 불러와야됨. 리눅스는 

윈도우는 시작할 때만 땅하고 끝남. 이때 

윈도우 부트매니저는 윈도우 실행 도와주는거. 이게 efi에 저장되어있음. 이게 한번에 불러와서 efi 망가트려도 실행됨. 껐다키면 실행안되겠지만. 즉 통짜구조라서 한번 전체 실행하는 구조를 가지는게 윈도우. 리눅스는 한 파트 한 파트 일부 영역만 efi영역을 불러와서 업뎃해도 안꺼도됨. 리눅스가 efi 삭제하면 잘되다 갑자기 꺼질수있음. 참조 : 운영체제 구조. 모놀리닉이랑 모듈형

쉘 스크립트도 라이브러리에 있음?. 명령어도 환경변수 path가 존재. ~~~.bin(바이너리, 이진법이란 뜻)이란 환경변수 폴더에 명령어(~~.exe)가 있지. 

쉘 스크립트도 라이브러리를 사용한다.! 물어본거임. 

C:\Users\김광재>where calc
C:\Windows\System32\calc.exe

이렇게 있다! 이게 왜 알려주나? 파이썬 버전 다른거 설치할 때 그 위치 알기 위해서임. 그래서 where을 cmd에 쳐서 찾아보는거지. 만약 여러개 버전다른 실행 파일이 있으면 가장 첫번째 걸 실행하라고 설정되어있기 때문. 나중에 실행되는거 실행하고 싶으면 폴더이름 바꿔서 가장 첫번째걸로 실행하게 할수있음

변수이름 짓기가 가장 까다롭데 ㅋㅋ. 그래서 삼성에선 가이드라인도 있다네? 그래야 인수인계도 편하고 다른사람도 알아먹을수있다고 가이드라인 통해서.

링크도 2가지가 있음 : 심볼링크, 하드링크. 심볼링크는 바로가기. 하드링크는 복제된거.

리눅스 ls -al (폴더있는거 싹다 출력해!) → xxx.sh의 링크가 bin\xxx.sh 가 폴더안에 있음. 바로가기 버튼 지워도 본래 프로그램 안지워짐. 이걸 자세히 알려면 시스템 구조?를 알아야됨 

이제 파일 시스템 공부할거임

파일 시스템에 따라 os마다 실행되기도하고 안되기도함. 파일 시스템을 배워야 파일 접근이나 관리를 할수있음. 데이터를 파일 단위로 조직하고 저장하는 시스템을 파일 시스템이라 함

os종류 : 윈도우, mac, 리눅스(커널이름이자 os이름. unix기반).

윈도우는 NTFS, FAT32, EXFAT

MAC은 APFS, …

세 os 모두 exFAT, FAT32를 다 공통적으로 씀. 그냥 파일 저장 방식이 다름

FAT32는 4kbyte씩 쪼개서 저장. 용량도 많아지면 엄청많이 쪼개야됨. 대용량일때를 위해 exFAT을 사용

A 4kb B 8kb C 12kb 를 4kb찍 저장하는 방법은… 알고리즘 따라서. 파일들 찾을 때는 저장된 주소를 이용함. 파일 시스템은 이런 알고리즘을 효율적으로 짜서 저장공간을 최대한 잘 쓸 수 있도록 함. 모든 파일 시스템은 저장공간에 무작위로 저장됨. 파일 인덱싱으로 파일 위치를 찾아야 파일을 찾을 수 있고 접근이 가능함. 파일 주소는 저장공간에 따로 위치함(인덱스 저장공간). 진짜 데이터는 데이터 저장된 곳에 있음. 심볼릭 링크는 인덱스 저장공간에 있는 주소를 복사한거. 하드 링크는 데이터 주소에 직접 접근함. 우리 파일 복구 가능한 이유가 파일 삭제할 때 파일 시스템이 쓰는 인덱스만 삭제하기 때문. 안에 진짜 데이터는 남아있음.  그래서 파일 복구업체에서 복구가 가능하고, 모든 용량을 전부 조사해서 복구하기에 시간도 걸리고 값도 나감(일부만 복구가 못해. 전수조사거든). 데이터 복구 못하게 할려면 덮어쓰기로 의미없는 값을 집어넣는 방식을 사용하면됨(더미데이터).

ssd는 용량 50% 넘어가면 인덱스 읽는데 속도가 떨어짐(인덱스 많아져서). 그래서 dram이 ssd에 부착해서 캐싱을 하여 속도감소를 방지함. 그래서 ssd는 용량이 많을수록 dram도 많이 넣어서 속도가 빠름.  ssd 1개 통짜보다 ssd 2개로 같은 용량 만들면 2개 쓴 컴퓨터가 더 읽는속도 빠름. ssd 2개가 동시에 돌아가 읽는 속도가 빠름. 

NAS(natwork attach system) : 네트워크(인터넷)로 접속하여 데이터에 접근하는 용도의 저장장치 시스템. 웹페이지도 돌릴 수 있는 모델이 존재한데. 이것도 램을 쓴데. 

하드디스크들을 묶는 개념이 raid.(플랫 여러장 묶어서 쓰는거). 버전이 여러개ㅣㅜ

raid0 - 스트레이트. 하드웨어 2개를 묶어서 소프트웨어로 보면 1개로 보이도록 함. 속도가 빠름

raid1 - mirror(복제). 하드웨어 하나가 뻑나도 다른거에 저장된 동일 데이터를 가져와서 안전성이 좋음

raid5 - swap. 

raid10 - raid0+raid1. 하드 2개 묶고 하드 2개는 미러링을 해서 2개 쓰고 2개는 백업용도로 써서 4베이라고 함. 최소 4개의 하드가 필요함. 속도와 안정성 모두 잡을려면 이거쓰기(돈이 많이들어)

djob - 

하드대신 ssd박아서 가능함. 물론 SATA3는 500MB속도뿐이라 한계는 분명이 존재함. SATA선으로 하드 묶어쓰거든.

인덱스영역을 아예 빼고 순수 저장용으로 저장장치를 쓰는 경우가 있음. 엄청빠른 SSD에 다른 저장장치에 있는 인덱스 영역을 전부 박아버려서 빠른 속도를 낼 수 있음.

듀얼코어 쓰는 이유는 버스 때문임. 듀얼로 써야 버스도 많기 때문임.

### 운영체제별 파일 시스템 구조

### Windows 파일 시스템

- **FAT32**: 파일 할당 테이블 기반의 파일 시스템으로, 호환성이 높으나 대용량 파일 지원이 제한적입니다.
    - **특징**: 최대 파일 크기 4GB, 최대 파티션 크기 2TB, 호환성 높음.
- **NTFS (New Technology File System)**: 고성능, 보안, 대용량 파일 지원 등 다양한 기능을 제공하는 파일 시스템입니다.
    - **특징**: 파일 및 폴더 압축, 암호화, 디스크 사용량 제한, 복구 로그, 보안 권한.
- **exFAT (Extended File Allocation Table)**: FAT32의 제한을 보완하여 대용량 파일과 파티션을 지원합니다.
    - **특징**: 최대 파일 크기와 파티션 크기에 제한이 없으며, 플래시 메모리 장치에 적합.

### Linux 파일 시스템

- **ext3 (Third Extended File System)**: 저널링 기능을 제공하는 파일 시스템입니다.
    - **특징**: 저널링으로 데이터 무결성 보장, 최대 파일 크기 2TB, 최대 파일 시스템 크기 32TB.
- **ext4 (Fourth Extended File System)**: ext3의 성능과 기능을 개선한 파일 시스템입니다.
    - **특징**: 최대 파일 크기 16TB, 최대 파일 시스템 크기 1EB, 익스텐트, 저널링, 빠른 파일 시스템 점검.
- **XFS**: 높은 성능과 확장성을 제공하는 64비트 파일 시스템입니다.
    - **특징**: 고성능, 빠른 복구, 대용량 파일과 파일 시스템 지원.
- **Btrfs (B-tree File System)**: 고급 기능을 제공하는 최신 파일 시스템입니다.
    - **특징**: 스냅샷, 서브볼륨, 데이터 중복 제거, RAID 지원, 파일 시스템 크기 조정.

### macOS 파일 시스템

- **HFS+ (Hierarchical File System Plus)**: 전통적인 Mac 파일 시스템으로, 저널링과 파일 압축을 지원합니다.
    - **특징**: 저널링, 파일 압축, 최대 파일 크기 8EB, 최대 파일 시스템 크기 8EB.
- **APFS (Apple File System)**: macOS, iOS, tvOS, watchOS에서 사용되는 최신 파일 시스템입니다.
    - **특징**: 스냅샷, 클론, 빠른 디렉토리 크기 계산, 파일 및 디렉토리 암호화, 공간 공유.

하이닉스 p41를 써야 게임할때 좋다. 읽기쓰기 속도 빨라서. picgen4 메인보드가 규격을 지원하는지 확인할것. → 그냥 싹다 바꿔야 업글할수있겠네.

심볼릭 링크 :

하드 링크 :

파일 시스템까지 했으니 이 파일 시스템이 어떻게 했겼는지 알게됨. efi영역은 들어봤을거임. 이런 영역을 잠깐 설명할것임. 그다음 인터럽터, 폴링?을 배울것임.

32비트와 64비트 차이는 명령어 갯수 차이, 메모리 크기 인식 차이(4기가, 16엑사)가 남.

윈도우 저장장치 디스크 형식. 파일 시스템이랑은 다름(디스크를 초기화하는 방식)

MBR. master boot record

GPT. general purpose table

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/914cd412-d6e9-4c46-8afb-88e9c6594671/d73f3f3b-f215-459f-8ec2-844f06f6767f/image.png)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/914cd412-d6e9-4c46-8afb-88e9c6594671/1f3e40c9-bc8e-4797-8dfd-1be3c7ccb935/image.png)

EFI 에 드라이버라던가 OS라던가가 있음. NTFS로 디스크 정리 프로그램도 보임.

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/914cd412-d6e9-4c46-8afb-88e9c6594671/5777b747-03dd-4595-8d0a-3cad93fdf0ea/image.png)

~변환이 디스크 초기화 방식임.

다른데서도 쓸수있기 때문에 FAT32로 하는 이유임

외장하드는 exFAT로 포멧하기(용랑 크니까). 파일 시스템 다른 외장하드 컴퓨터에 꽃아서 쓰면 불량 디스크로 인식해 포멧해버림…. 조심해. 

요즘엔 MAC은 한국어쓰면 받침이 탈락하는 현상이 일어남. MAC은 ‘ㄱ’을 다루는 명령어가 다르기 때문임(MAC은 UTF-8KR). 파일 인코딩 방식이 다르기 때문임. 파일 제목도 윈도우에서 못쓰는거 MAC에서 쓸수있지만 윈도우에선 인식못함. 파일에 한글이나 한글 경로가 있으면 오류가 나는 프로그램의 경우 EN-ns로 파일 인코딩을 했기 때문임. 즉 인코딩 방식도 주의해야됨

WTG는 USB에다가 EFI 넣어서 그걸로 부팅시키는 물건임. 

시작 프로그램은 왜 작동하는가? 윈도우 부팅될때 시작프로그램 목록있는곳에 링크를 걸어두기때문. Win+R :shell:startup 쳐서 시작 프로그램 폴더 안에 프로그램 올리면 부팅될때마다 시작됨. 골때리는건 윈도우가 레거시 시스템도 지원하니까 구형이랑 신형 방식이 서로 호환이 안됨. 봐봐 시작 프로그램 있는데 폴더는 텅텅 비었잔아. 웬만하면 편한거 하나만 써. 

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/914cd412-d6e9-4c46-8afb-88e9c6594671/67bf7439-f055-4f18-b198-83e20e1b2a80/image.png)

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/914cd412-d6e9-4c46-8afb-88e9c6594671/125ad471-e184-4169-998e-aad749627518/image.png)

업데이트는 시작 프로그램인가?

아니다! 윈도우 서비스에 들어가봐라. 레지스터 단에서 실행되기 때문에 계속 돌아가고 있음(실시간). 커널(os) 속에서 돌아가는 프로그램들을 통틀어 서비스라고 칭함. 아래에 있는 사진이 서비스 목록들임

![image.png](https://prod-files-secure.s3.us-west-2.amazonaws.com/914cd412-d6e9-4c46-8afb-88e9c6594671/13766324-dad8-4834-ad07-e74b72d717ac/image.png)

왜 이런걸 배우느냐?

우리가 쓸수 있을지도 모름. 쓰레드 건드리면 커널단에서 난 오류를 보고 오류수정을 할 수 있기 때문임

퀴즈

1.  커널과 쉘을 서술하시오-
2.  환경변수란? - 
3.  컴파일러란 뭐고 윈도우에서 배치파일이란 뭘까
4.  프로그램이 윈도우용, 리눅스용 이렇게 나뉘는 이유는?
5.  왜 윈도우는 업데이트 할때마다 껐다 킬까?
6.  심볼링크와 하드링크의 차이점은?
7.  파일 시스템이란?-
8.  raid는 무엇이고 왜 쓰는가? raid 10은 뭐개?-
9.  업데이트는 시작 프로그램인가?
10.  인코딩 방식도 주의해야되는 이유는?
- 정답
    1.  시스템의 모든 자원(프로세스, 메모리, 하드웨어, 파일)을 관리하고, 사용자와 하드웨어 간의 인터페이스를 제공.쉘은 사용자가 컴퓨터랑 소통할수 있게 해주는 것(cmd,파워쉘)
    2.  쉘에 변수를 미리 지정해 주는것
    3. 우리가 쓴 코드 컴퓨터가 알아먹을 수 있는 언어로 바꿔줌(쉘). 윈도우에서 ~~.bat 파일이 이미 컴파일 된 파일
    4.  os마다 컴파일러가 달라서. 그래서 os마다 따로 개발하거나 통합 프로그램을 제작함
    5.  윈도우는 efi를 처음 켜질때 한번 전체 실행하는 구조를 가지기 때문. 리눅스는 한 파트 한 파트 일부 영역만 efi영역을 불러와서 업뎃해도 안꺼도됨. 실시간으로 적용되기 때문
    6.  볼링크는 바로가기. 하드링크는 복제된거.
    7.  데이터를 파일 단위로 조직하고 저장하는 시스템을 파일 시스템이라 함. FAT32, NTFS, exFAT같은 것들이 파일 시스템
    8.  저장장치 여러 개를 묶어 고용량, 고성능인 저장 장치 한 개와 같은 효과를 얻기 위해 개발된 기법. raid0 + raid1 합성한거로 저장장치 2개를 동시에 쓰고, 다른 저장장치2개를 백업 용도로 쓰는 방식
    9.  아니다! 윈도우 서비스에 들어가봐라. 레지스터 단에서 실행되기 때문에 계속 돌아가고 있음
    10.  파일 인코딩 방식이 다르면 글자가 깨지거나 프로그램을 읽지 못하는 경우가 발생하기 때문임.