
우분투
Ubuntu 24.04.1 LTS (롱텀서비스) 다운받고
https://rufus.ie/ko/ 에서 부팅 드라이버 만들기. 파일 시스템 : FAT32. 이게 리눅스도 되는 공통적이기 때문. 권장 설정 사용.
F2키로 바이오스 진입. BIOS탭 진입. 부팅구성.boot메뉴 들어가기 드라이버 옵션 우선순위를 USB로 선택해서 설치. save해서 설치 시작.
try or install 선택. 
우분투 한국어로 설치 추가 다운받는거 다 해주면 좋음. 수동 파티션- 파티션 만들기 - ext4, 마운트 위치:/efi, 크기 : 500MB(알아서 해줄거임). 그리고 그냥 파티션 추가 / 하면 다 됨. 계정은 맘대로. 컴퓨터 이름도 server로 하든가. 암호는 곡 외우고. 다른거 생략하고. 
우분투 터미널 ip addr show -> enp4s0 에 inet 이 아이피임. or ifconfig는 sudo apt install net-tools 깔아서 씀. 
공유기라면 192.168.x.1 를 인터넷에 들어가기. 네트워크 설정- DHCP 서버 설정. 왜하냐면 DHCP는 아이피가 계속 바뀌어서 고정시켜 설정함. 등록된 주소 관리에 올라가면 고정임. 
DDNS 설정 - 호스트이름-자율로설정, 아이디도 자율로설정. 그러고 나서 정상등록 상태 확인. 이제 내부 IP 설정해줘야됨. 
NAT/라우터 관리-포트포워드 설정-규칙이름:SSH, 프로토콜:TCP//UDP, 외부포트6303 SSH22 하면됨. 이러면 외부도메인+외부포트->내부IP+내부포트로 감. DDNS,포트포워딩해주면됨.
터미널 sudo apt install openssh
ssh -p 6303 서버설정한거도메인주소
이러면 가능함. 여기까지 아이피세팅법. 동영상도 올려준다고함. 
vscode 호스트연결이 안될거임(핑거프린트 바뀌어서 그런거임). .ssh 폴더 들어가서 known 파일들 전부 삭제. 자기 이름 폴더 밑에 있음 주의.
카카오 서버로 주소 바꿔서 업뎃하면 빨라짐. 
sudo apt update
sudo apt upgrade    (업데이트 안하면 업그레이드 목록을 얻을 수 없어서 업그레이드 못함)
sudo swapoff -v /swap.img 로 스왑파일 오프
sudo fallocate -l 64G /swap.img 로 64기가 할당 (램의 1~2배 정도)
sudo chmod 600 /swap.img
sudo mkswap /swap.img
sudo swapon /swap.img
free -n
sudo useradd -m -s /bin/bash hkit   사용자추가
sudo passwd hkit
쉘 다시 시작
su hkit 로 유저바꾸기
기본설치는 딱히 설치 안해도 되긴 함. 글카 드라이버도 apt로 바로 설치 가능해서 편리해졌다네.
글카 드라이버를 apt로 설치했으면 나머지도 apt로 설치하기
sudo apt autoremove 로 빈폴더 삭제
sudo apt install nvidia-dirver-550  nvidia 한 후 탭키 누르면 그거 목록 가능
nvidia-smi
wget 아나콘다리눅스다운주소 로 다운받기
sudo anacond...sh 파일 이름 넣어서 아나콘다 설치하기.  
yes 로 하면 좋음. 
다같이 쓸려면 /opt/anaconda3 에 설치하도록 명령어 치기.
그다음 엔터치고
conda init 하면 안될거임. 콘다 초기설정 안해줬기 때문임. 
cd /opt/anaconda3/bin
conda... 아니sudo 써서 설치하면 안됨. 

sudo mkdir -p /data1
sudo mkdir -p /data2
sudo mount /dev/sda1 sda하면 아무것도 없음. sda1하면 파티션 설정된것
sudo mount /dev/sda1 /data1/
sudo mount /dev/sdb /data2 로 임시 마운트(영구마운트는 코드 따로 작성해야됨)
... 아무튼 참조 보고하기

도커는 apt로 깔리지 않는다. 설치하기 까다로운 프로그램이... 어라 apt에 있네?
근데 안되네
도커설치는 참조 보고해.
sudo apt update로 도커 리스트 보기.
sudo apt upgrade
sudo apt autoremove
sudo systemctl enable docker 하면 서버 실행할때 도커가 같이 실행됨
s


서버 관리는 서버 버전이 바뀔때마다 관리법도 바뀌어서 계속 공부해야됨. 쉘 스크립트로 만들어서 하면 되는데 업뎃 계속 해줘야되서 손으로 치는게 빠를것 같을것.
https://www.notion.so/planet-ms/e498a4b95a9f4ba6aa3435525a8f38f1
참조
