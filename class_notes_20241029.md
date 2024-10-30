오늘은 openCV 배움. CV(Computer Vision)는 굉장히 생소한 단어임. 쉽게 말해서 '디지털로 표현되는 모든 시각적 데이터를 처리한다' 를 의미함. 왜 배우냐? 데이터 전처리에 쓰이기 때문이다.  그러니까 시각적 데이터의 전처리에 사용된다. 전처리는 설명하자면, 딥러닝 모델은 일단 일관된 입력(비슷한 입력)을 받아야됨. 만약 사진을 예로 들자면, 밝기만 다른 사진을 컴퓨터가 다르게 인식하는데 그걸 전처리를 통해 똑같다고 인식시켜주는 거지. 전처리 말고도 시각적 데이터의 특징을 추출하는데에도 쓰이기 때문임. 특징 추출은 또 뭐냐? 세부적인 특징(세로선만 추출하는 필터 같은거로 귀만 추출하거나 가로선만 추출하는 필터로 수염을 추출하는거)을 추출해서 다른 고양이 사진이 들어와도 겹치는 특징으로 고양이라고 인식시키기. 귀신처럼 보이는 것도 이런 원리(파레이돌리아) 때문이지. openCV는 쉬운 도구(비슷한걸로 numpy. 필터 생성)임. 그리고 공짜다! 

파이썬하다가 openCV로 C언어로 작성된 코드와 비요해서 얼마나 속도 차이가 나는지 확인할 것이다. conda install opencv 로 콘다써서 설치하기. opencv는 의존성이 엄청 강해서 의존성 관리 잘해서는 conda 서서 설치하기. 우리는 먼저 이론부터 짚고 넘어갈것임.

색공간? 그냥 RGB임. 3개 벡터(R,G,B)가 모여서 3차원인 공간을 표현하기 때문이지. 투명도 a까지 더하는 png는 4차원임. 밝기는 RGB에 포함된 값임. jpg는 RGB씀. 원본그림은 raw, tiff 로 표기됨. 이거 압축같은것도 안해서 용량 엄청큼. 빨초파 3개 색 조합이라 3개의 채널을 가진다고 함. 각각 색은 0~255값을 가짐. 8비트로 색을 표현. RGB를 하나로 표현하기 때문에 24비트가 아닌 8비트로 표현함. 빛의 삼원색을 표현하기 위해 RGB씀. grayscale 색공간은 1채널, 즉 흑(0)~백(255)임. 사진은 RGB 로 3장으로 분해할 수 있음. 그레이스캐일을 RGB로 바꿀수도 있음. 보통 채널을 복사해서3개로 만들어 붙임. 이걸 왜 보냐? 데이터가 1차원이냐, 3차원이냐 보기 위함. 흑백 사진인데 RGB일 수도 있음. HSV 색공간은 색 표현 방법중 하나일 뿐임. cmyk 색공간도 있음. HSV 색공간을 조금 다른게 색상, 채도, 명도로 색을 결정하는 방식이다. 그림판이나 그림그리기툴에 나온 원반에 쓰이는거지. 픽셀의 단점으로 엘리어싱이라고 있음. 안티엘리어싱???? 어찌됬든, 픽셀은 이미지의 최소 단위라고 생각하기. grayscale은 단원식. opencv랑 맵플로립이 이미지 처리 방식임... 와.
이미지 구성 기본 단위 : 픽셀(pixel). 점 하나. 다른 이미지 구성 단위도 있긴한데 잘 안씀. 벡터맵이라고 있음. 

5장 임계값. 임계값은 threshold(쓰레스홀드)라고 하는 한계치라고 보면 됨. 바이너리 이미지(0,1로 색 표현)도 있음. 원하는 부분만 보는 필터로 많이씀(얼굴만 본다거나). 임계값은 기준점이 됨. 기준점을 넘거나 안넘으면 1또는0으로 표현한다. gray를 바이너리로 변환하는데도 쓰임. 문제는 흑백 두가지만 있는 이미지가 그레이스케일일수도, 바이너리이미지일수도 있어서 꼭 확인해야 요량이 달라지고 처리법도 달라짐. 그래서 항상 데이터를 확인하는 습관을 들여야함. openCV에선 바이너리이미지의 흑색을 0, 백색을 1로 표현함. 이거 중요함 mat은 반대임. 게다가 cv는 RGB가 아니라 BRG로 읽으니 주의할것. 그래서 입력을 알아야되.

6장 블렌딩은 2개의 입력 이미지의 투명도를 조정해 2개의 이미지가 겹쳐보이도록 만드는 것이다. 즉 AB의 투명도를 조정해서 합치는 것. 투명도는 a(알파)를 씀. RGBa로 씀. 두 이미지 섞을 때 씀. 특히 특정 이미지 위해 오버레이할 때 씀. 단순히 합치는 것을 블렌딩이라고 하지 않음. 단순함침이 아니라 이미지 투명도 조절이 추가되됨. 차영상은 차동차 영상이 아니라 같은장소를 촬영한 2장 이상의 이미지를 사용해 새로 추가된 객체를 검출하는 방법. 새로 생긴 이미지를 검출하는 방법이지. 이미지 센서 만들때 쓰이나? 이미지 비트 연산은 이미지를 합치는데 사용함. 덧씌워서 원래 값은 지워지고 새로운 값을 새기지. 이미지 비트 연산은, 일단 이미지는 벡터이자 배열임. opencv 내부 코드는 numpy로 구현되어 있음. 그래서 둘의 궁합이 좋음. 이미지 프로세싱 원리만 알고있으면 numpy로 구현가능. 이미지 비트 연산은 AND OR 연산을 이미지에 적용함. 두 이미지를 합성하면 색깔이 같은 부분만 백색(1)로 표현됨. 로고가 없는 배경 부분은 빈공간으로 표현함. 이런 이미지 비트 연산은 바이너리 이미지를 이용한 필터를 적용하는데 사용함. 틀린 그림 찾기에도 쓰임(차연산).

관심 영역 설정(RoI, Region of Interest. 흥미있는 부분)은 단어 자체가 중요함. 이걸 어떻게 설정한다고? RoI 공간만 어떻게 떼어내지? 직사각형이면 각 꼭짓점 좌표 abcd를 이용함. 어떤 프로세스로 동작하느냐? 가로를 [a의x좌표:b의x좌표] 를 구함. a[1:4][1:4] 이렇게 겹치는 부분만을 구한다. 직사각형 좌표를 바운딩 박스, bbox, bb라고 표현함.

벡터, 비트맵은 차이가 있음. 이 둘은 소프트웨어적인 처리를 말함. 모니터는 비트로 표현함.
비트맵은 픽셀, 즉 점(비트)들이 모여서 지도(맵)를 이룸. 곡선을 표현할 수 없음(네모라서). 픽셀을 매우 작게 만들면 곡선을 표현 할 수도 있음(완전하진 않지만). 픽셀의 수가 많아질수록 이미지가 선명해지고 용량도 커짐. 이미지를 확대하면 이미지가 깨진다거나 계단처럼 보이는 계단현상이 발생함. 비트맵을 픽스맵 혹은 래스터 라고 부름.
벡터맵은 ... 벡터는 방향과 크기. 벡터맵은 점들이 선들로 연결된 구조임. 점들이 많아질수록 곡선에 가까워짐. 이미지를 확대해도 깨지지 않는다는 장점이 있음. 벡터맵은 확대를 하면 그만큼 늘어남. PDF에서 벡터맵을 사용함. 이론상 무한히 확대해도 곡선이 선명히 보임. 그래서 PDF로 줘야 확대해도 안깨짐. 윈도우에서 PDF 열면 벡터맵-비트맵 변환이 이루어져야 되서 속도가 오래 걸림. 그래서 출판업계는 맥북을 써서 이미지 깨짐을 막고 벡터맵을 기본으로 표현하기에 변환이 없어 여는 속도가 빠름. 엄청 큰 사진이나 엄청 작은 사진은 벡터맵으로 만들어야 안깨짐. 확대를 계속하면 점의 갯수도 늘어나서 곡선이 표현됨. 그래서 너무 확대하면 점이 너무 많아져 버벅대기도함(그래서 확대 제한이 걸림). 참고로 일반적으로 딥러닝 기법들은 픽셀을 기반으로함. 그래프 뉴럴넷은 벡터맵 학습용임. 픽셀맵 이미지를 보는게 일반적이라 CNN같은 이미지 처리는 비트맵으로 이루어짐. JPG는 3 * 256 * 1920 * 1080 비트만큼 저장함. 용량이 엄청나게 커짐. 그래서 용량을 줄일려고 압축 기법이 생겨남. JPG,JPEG 같은 파일 형식이 생겨났지. Exif는 무손실 압축에 위치정보도 포함된 형식. TIFF는 무손실 압축. PNG는 투명도까지 해서 트루컬러 지원함. HDR은 색 공간 대역이 더 넓은 형식. 이미지를 압축하면 손실 방식(PNG, JPG), 압축하지않는 무압축은 무손실 방식(RAW, TIFF)이라고 함. 이 압축은 비트맵에서만 이루어짐. SVG, AI 같은 확장자는 뷰어에 따라서 벡터의 노드(벡터 시작점) 갯수를 조절함. 즉 벡터맵 형식이란 거지. 이런걸 왜 배우냐면, *딥러닝으로 쓸때 확장자에 따라서 성능차이가 크게 나기도 하기 때문임*. PNG는 RGB+a 로 트루컬러 지원하는 손실 방식이다. JPG는 RGB를 지원하는 손실 압축 방식이다. 압축을 어떻게 하는지는 생략한다. Raw, PNG 데이터를 AI에 넣으면 성능차이가 남. 압축형식으로 하면 데이터가 훼손됨. 중요한 데이터가 날라가 학습이 불가능해질 수 있음. 그래서 AI에서 데이터를 전달할 때 무손실로 전달하거나 pickle(데이터 배열 저장. 무압축)을 씀. npy,npz도 쓰는데 이는 이미지는 배열이기 때문에 배열을 저장할 수 있는 numpy로 저장해도 무방하다. 그러니까 JPG로 된 데이터셋은 걸러야한다(데이터 손실있음). 엠니스트도 데이터 훼손을 방지하기 위해 배열 형식으로 보내줌. JPG로 되어있으면 어쩔수 없기도함. 그러니 피클 혹은 npy로 데이터 저장하기. 실제로 직접 학습시킬땐 npy, pickle, TIFF, H5PF(대용량. I/O 속도가 빠름. 용량이 클뿐...) 를 이용할것. HDR(12bit), SDR(8bit)은 색 공간의 넓이 차이가 있음. HDR은 색표현이 더 세밀함. 계단현상=엘리어싱. 안티엘리어싱은 확대했을 때 보이는 흐릿한 부분을 없앰. 안티엘리어싱은 DLRR로 발전함(딥러닝을 이용). 그러니 웬만하면 JPG로 데이터 만들어도 화소많고 압축률 낮은 데이터를 쓸것. 얼리센싱이 핫하다. 고품질의 데이터를 통해 노이즈라고 생각했던 패턴들을 파악할 수 있기 때문임. 

회전 행렬은 이미지 회전을 말함. 옛날에 보던 그 사인 코사인 공식 써서 회전시킴. opencv에는 회전 함수가 있어서 공식은 안씀. 
Warping와핑은 도로주행에서 쓰이는 이미지 형태 변환 기법임. 차선 추출에 사용됨. 이거 내 폰 문서랑 텍스트 추출할 때 사용되는 기법임. v-flat에서도 사용되고 아마도. 어파인 변환은 3차원에서 이루어지는 기법으로 도형의 윗부분만 기울이는 변환 기법임. 그러니까 직사각형 밑에 붙여놓고 위를 흔들어 마름모같은 형태로 만드는거 그거임. 중요한건 warp, affine이고 변환에는 2D,3D가 있고 2D,3D 에서 
scaling은 가로축 세로축 등(축방향으로 배수), 
rotation은 축기 교차하는 중심의 기준으로 회전변환, 
sheer는 대각선 축으로 배수. 
warp(이미지 와핑)은 쉽게 말해 view를 바꾼다(탑뷰, 쿼터뷰 등으로 변환). 간략하게 설명하자면 어떠한 이미지에서 네 점을 잡아 만든 사각형을 기준으로 변환한다. 직접 눈으로 보는 차선이 기울어저 보이는데, 이걸 와핑하면 탑뷰 형식으로 바꿔줌. 자율주행에서 중요! 차선검출에 사용되는 변환 기법임. 
affine 변환은 쉽게 말하면 지면에 붙어있는 도형을 밀어서 윗부분을 변형시킨 모양으로 변환하는 기법이다. 카드더미 기울인거처럼 보이지. 2D,3D 전부 적용가능하다. 주로 CT에서 사용된다. 사람이 이상하게 누워도 똑바로 누운 것처럼 변환시켜줌. 왜곡의 보정에 자주 쓰인다. 어안렌즈의 보정에도 사용됨(FOV가 작아져 시야가 작아짐). 이러한 변환이 이미지 프로세싱의 꽃이다. 공식은 opencv에서 함수 형태로 제공하니까 그냥 그렇다고만 이해하고 적용만 할 줄 알면 된다. 
스케일링은 네모를 크게 확장시키는 것과 비슷하다. 없었던 걸 채우는 거라 보간(interpolation!)이라고 한다. 
기법들 중에서 bilinar라고 값은 값을 할당하는 기법도 있다. cubic이라고 주변 픽섹을 고려해 할당하는 기법도 있다. 그레이스케일을 RGB로 변환할 때는 바닐라 방식을 쓴다. 여기 기법은 다 행렬로 하기 때문에 넘파이가 중요하다. 
이동translation은 점 네개를 이동시키는 걸 말한다. 어파인 변환은 특징은 평행선은 유지한다. 즉슨 공간적 평행은 유지된다는 뜻이다. 
퍼스펙티브 변환은 마름모꼴이던 종이 찍은걸 펴주는 변환이다. 종이 스캔 뜰때 사용되는 변환이다. 원본 이미지의 모든 직석은 출력 이미지에서 직선으로 유지된다는 소리. 어쨌든 직선을 유지. 퍼스펙티브는 두 점을 이동해 이미지를 피는 변환이다. 이것도 도로선 인식에 쓰임.

컨볼루션은 유명한 개념임. 한마디로 필터로 쓰인다. 특징 추출기로 컨볼루션을 쓴다. CNN에 쓰지. 
블러는 노이즈(튀는값)를 제거하기 위해 사용함. 큰 값일수록 크게 줄어들어서 이미지값들의 차이를 적게 만들어 흐릿하게 만듬.
샤프니스는 대비를 크게함. 임계값 이상의 값에 배수를 곱해 명확하게 차이가 나도록 함. CHAHE(클레이)라고 굉장히 선명하게 만들어주는 필터가 샤프니스의 예임. 
평균 블러링은 이퀄라이제이션으로 블러 평균임
가우시간 블러링은 가우시안 분포처럼 블러를 먹임. 실제로도 픽셀의 분포도 가우시안을 띰.

에지 검출이 중요함. 선 검출임. 소벨을 알아야함. 에지는 픽셀값이 급격히 변하는 지점임. 미분했을 때 가장 큰 값(기울기가 가장 크다=변화랑이 제일 크다=대비가 크면 다른 영역이다=다른 영역을 구분하는 모서리다)이 나옴. 3 / 100 은 차이가 명확히 나서 이곳을 에지라고 한다.
캐니 에지 디텍터는 엣지 검출의 끝판왕으로 낮은 오차(선만 정확하게 검출), 정확한 에지 위치, 응답 최소화 의 장점이 있다. 함수가 있음. 
모폴로지는 형태란 뜻임. 어떠한 형태를 왜곡시켜 봔한시킨것. 
이로션은 침식이란 뜻으로, 가장자리를 침식함. 경계가 불분명한 객체(물체)를 분명하게 만듬. 안개낀날의 차선인식을 명확하게 만들어줌. 중심선 검출에 쓰임(사람 관절 찾기)
딜레이션은 팽창이란 뜻임. 경계를 흐리게 만듬. 즉 경계를 두껍게 만듬. 잔상을 없애거나 지워진 차선을 명확하게 만들어줌.
오프닝은 이로션 다음이 딜레이션 적용. 주변에 있던 노이즈나 불분명한 값들이 사라지기 때문에 사용함. 침식한 다음에 팽창시킴. 바깥을 깔끔하게 만듬 
클로징은 딜레이션 다음에 이로션 적용. 구멍 메꾸는데 효과적이다. 안을 깔끔하게 만듬. 
허프 변환은 다음 시간에

오늘을 정리하자면 개념들의 방법과 어떨때 서야하는가를 배움. 복습을 하면서 얘는 어떤 상황에서 쓰면 좋겠다고 생각해보면됨. 이용법은 opencv 코드 한줄이면 됨. 어떠한 원리로 돌아간다 정도는 알면 좋다. 그러므로 방법과 어디다 쓰는지 알아보기. 내일은 실습할 것임. 

OpenCV - CV = Computer Vision 약자. *데이터 전처리에 쓰이기에 사용함*. 전처리는 일관된 입력을 받기위해 사용함. 이거는 특징 추출에도 쓰이는 공짜 라이브러리임.

색공간 - RGB. Red Green Blue 3개 벡터가 모여서 생긴 3차원 공간을 표현함. 각각 0~255값을 8비트로 표현함. 한 사진을 RGB 3개의 사진으로 분해가능. RGB 외에도 greyscale(흑백 1차원), 바이너리(1백색,0흑색), HSV(색상,채도,명도), CMYK 등등이 있음. 이미지의 픽셀(이미지 최소 단위) 표현에 사용됨. *이미지가 greyscale일지, RGB일지 알 수 없을 때 이 이미지의 색공간은 어떤건지 알기위해 배움*

임계값 - 쓰레스홀드, threshold. 한계치. *greyscale을 바이너리 이미지로 표현하는 필터 혹은 원하는 부분만 보는 필터로 사용됨*. 

블렌딩 - 2개의 입력 이미지의 투명도를 조정해 2개의 이미지가 겹쳐보이도록 만드는 것. 투명도 기호는 a. 단순합침이 아니라 오버레이를 할 때 사용. 
차영상 - 같은 장소를 촬영한 2장 이상의 이미지를 사용해 새로 추가된 객체를 검충하는 방법. *새로 생긴 이미지를 검출하는데 사용함*

이미지 비트 연산 - 이미지를 합치는데 사용함. AND OR 사용. *바이너리 이미지를 이용한 필터를 적용하는데 사용함*

관심 영역 설정 - RoI, Region of Interest. 흥미있는 부분. 가로세로 자표의 겹치는 부분만을 구함. 

비트맵 - 픽셀로 지도를 이룸. 픽스맵, 래스터 라고도 부름. 픽셀이 만항질수록 이미지도 선명해지고 곡선도 명확해짐. 단, 이미지를 확대하면 이미지가 깨짐(=계단현상=엘리어싱). *이미지가 대부분 비트맵 이미지기에 배움*

벡터맵 - 노드를 있는 선들로 이미지를 표현함. 점들이 많을수록 이미지도 선명하지고 곡선도 명확해짐. 이미지를 확대해도 이미지가 깨지지 않음. *인공지능은 대체로 비트맵으로 학습을 하기 때문에 벡터맵은 잘 안써서 배움*

손실 압축 - 이미지 용량을 줄이는 과정에서 데이터 손실이 이루어짐. JPG, JPEG, PNG 등이 있음
무손실 압축 - 이미지 용량을 줄이는 과정에서 데이터 손실이 없음. TIFF Raw 등이 있음. 압축은 비트맵에서만 적용가능.
압축 형식은 왜 배우나면 *딥러닝 할 때 확장자에 따라 성능차이가 크게 날 수 있기 때문임*. 웬만하면 피클, npz 쓰자.

이미지 변환 기법들
회전 - lotation. 그냥 이미지 회전
와핑 - warping. 뷰를 바꿈. 이미지 네 점을 늘려 이미지의 형태를 직사각형으로 변환하는 기법임. *도로주행의 차선 검출에 사용됨*
어파인 - affine. 도형을 밀어서 윗부분을 변형시킨 모양으로 변환하는 기법. *왜곡의 보정에 쓰임*. 선의 평생성은 유지됨
스케일링 - scaling. 직사각형을 크게 확장시키는 기법. 보간이라도고 함.
이동 - translation. 그냥 점 네개를 이동시키는 기법.
퍼스펙티브 - perspective. 마름모꼴이던 네모를 지갓각형으로 펴부는 변환기법. *도로선 인식 혹은 종이 스캔에 쓰임*
컨볼루션 - convolution. 특징 추출기
블러 - *노이즈 제거에 사용*. 큰값일수록 크게 줄어서 이미지값들 간의 차이를 적게 만들어 이미지를 흐릿하게 만듬
샤프니스 - *이미지간를 선명하게 만드는데 사용*. 임계값 이상의 값에 배수를 곱해 명확한 차이를 만들어내는 기법.
평균 블러링, 가우시안 블러링은 각각 평균 혹은 가우시간 분포를 이용해 블러를 적용함.

에지 검출 - edge. 픽셀값이 급격히 변화하는 지점을 검출하는 기법. 미분해서 제일 큰 값이 에지. 캐니 에지 디텍터는 엣지 검출을 잘함.
모폴로지 - 형태를 왜곡시켜 반환하는 기법
이로션 - erosion. 침식. 가장자리를 침식하는 기법. 경계가 불분명한 객체를 분명하게 만드는 기법. *안개낀날의 불분명한 차선을 인식하는  성능을 좋게 만듬*
딜레이션 - 팽창. 경계를 흐리게 만듬. 경계를 두껍게 만드는 기법. *잔상을 없애거나 지워지거나 훼손된 차선을 명확하게 인식시키는데 사용됨*
오프닝 - 이로션 다음에 딜레이션을 적용하는 기법. *주변에 있던 노이즈나 불분명한 값들을 사라지게 만들어 차선인식 성능을 높임*. 바깥을 깔금하게 만듬
클로징 - 딜레이션 다음에 이로션을 적용하는 기법. *차선 구멍을 매꾸는데 효과적인 기법*. 바깥을 깔끔하게 만듬