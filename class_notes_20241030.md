어제 OpenCV 이미지 변형 방법을 배웠음. 이미지 변환 방법들이 컴퓨터 비전들의 끝판왕이라 배운거 진짜로 사용함. 데이터에 따라 이미지를 잘 변형할 줄 알아야됨. 우리는 쓰면 됨. 허프 변환이 끝판왕이라 이걸 오늘 배울것임. 

허프 변환은 허프 선형변환이라고 함. 직선을 찾기위해 사용되는 알고리즘임. y=mx+b 란 식을 만족하는 설들을 검출하는 알고리즘. 
캐니 엣지 변환을 통해 선의 정보를 얻어냄(y=mx+b). 우리가 지정한 m기울기 범위를 만족하는 선만 통과시킴. 
그냥 선형방정식을 만족시키면 선을 검출함. 위 일차식을 a,b 좌표계로 살짝 변형해서 선을 구하지. a와 b의 범위를 지정하면 그 범위를 통과하는 선들을 구할 수 있음. xy좌표계의 직선이 ab좌표계에서 점으로 맵핑됨. 그 점들이 모여 만든 직선이 해당 범위를 만족하는 직선들의 모임임.  점들이 겹치면 기울기와 절편이 같은 선이 여러개있다는 소리. 즉슨 ab좌표에서 한 곳에서 점의 숫자가 많다면 같은 직선이 여러개 있다는 소리고 한 직선으로 연결할 수 있다는 소리다. 그렇기에 ab좌표계에서 큰 값이 나오는 곳만 집어내면 그 공간에 있는 좌표로 직선을 만들어낼 수 있다는 소리. - - - 이런 선들을 -----로 이어 직선으로 만들 수 있다는 의미다. 이렇게 이어진 선들을 검출하는 변환이 허프 변환이다. ab좌표계에서 큰 값이 있는 곳의 값으로 직선을 만들어 낸다. 캐니엣지변환으로 선을 검출하고 허프변환 먹이는 식임. 확률적 허프 변환만 해도 좋음. 잘 검출함. 리소스 절약과 시간 절약을 동시에 가능함. RoI와 궁합이 좋다. ab범위 지정이 필수임. 탑뷰 변환- 전처리 - RoI 지정 - 캐니엣지 - 원하는 범위 지정해서 허프 변환. 참고로 소실점(공간이 한점으로 모이는 점. 눈에 보이는 그거 있잔아 그거) 찾는데도 쓰임.

허프 원 변환도 있음. 우너 검출하는데 쓰이는 알고리즘임. (x-cx)^2+(y-cy)^2=r^2 을 역시 공간변환해서 원을 검출함. 선변환이랑 비슷한 원리로 검출함. 동그란 원 검출하는데 좋음. 근데 다른건 못해서 성능이 영 그렇데

히스토그램은 막대그래프란 뜻으로 그... 막대드래프여러개 엄청 모여서 그림처럼 나타난거 그거. 그러니까 이미지를 구성하는 픽셀값 분포에 대한 그래프임. 히스토그램의 분포를 이용해 빛의 노출량을 조사함. 0에 가까우면 어둡다는뜻. 우린 벨 커브(종처럼 분포해서 적당한 빛 분포)로 만드는 알고리즘을 알아볼것임. 그게 바로 히스토그램 평활화(이퀄라이저)라고 전처리에 쓰임. 너무 어둡거나 밝은 사진의 대비를 줄일 때 사용함. clahe와 같이 써서 선명한 사진을 만듬. 클레이는 부분을 나눠 평활화해서 복원이 불가능함(크기 알아야 복원가능). 원본이 사라짐. 평활화는 복원이 가능함. 좁은 범위를 잡아 늘리는거지. 막대그래프 사이에 간격을 삽입해 늘림. 그 간격은 비어있는데, 이전에 있던 그래프를 잘게 쪼개서 간격을 채우는 보간작업도 해줄 수 있음. 그래서 히스토그램 높이가 낮아진 예시가 보인 거지. 주변 픽셀 조사해서 비슷한 값을 넣어도 되. 경계같은경우 그 경계가 부드러워져 샤프니스가 떨어지는 경우도 있음. 샤프니스 먹여서 선명도를 높이기도함. 가금 너무 보정이 되서 안보이는 사례도 있어서 CLAHE로 부분적으로 사진을 나눠서 보정을 먹이고 보간해서 잘보이게 만들음. 대신 용량이 커짐.

템플릿 매칭은 템플릿 이미지와 일치하는 영역을 입력 이미지에서 찾는 방법. 대충 6가지 알고리즘이 존재함. 컨볼루션처럼 이미지에서 한칸씩 이동해서 찾음. 물론 회전도 하면서. 비효율적이지만 그럴수밖에 없음. 

이진화에서 알아야 할 것은 영상 분할.세그맨테이션. 특정 물체, 영역을 분할. 굉장히 많이씀. 중요함. 딥러닝으로 분할함. 입력 이미지에서 관심있는 부분을 분리하는 방법. 분리하는 방법이 엄청 다양함에 유의할 것. 요즘엔 고전적인 방법으론 정확도가 매우 낮아 딥러닝을 이용해 잘 찾아냄. 특히 위장색 가진 동물들.
인스턴스라고 객체만 분할하는 방법(인물만)
시맨틱이라고 전체 사진을 분할하는 방법(단체사진의 사람들과 배경 분할)
판토닉은 위 두개를 섞인 방법임.

백그라운드 서브스트랙션은 '뒷배경 빼다.' 란 뜻임. 겹친 물건을 빼는 방법이지. 겹친 부분 때문에 빼면 빈공간이 생겨버리는데, 이것도 보정해준다. 보통 엑스레이나 ct처럼 통과하는거에 이용하고. 오버레이는 해당 물체를 제거 후 그 부분을 주변 픽셀들로 채운다. 주로 포토샵 사람 지워주세요 의뢰같은거에 쓰임. 이런 것도 있다! 정도만 기억하기. 뺀공간을 채우는 방법이 이런게 있다고 기억하기. 음성 추출도 서브스트랙션임. 

컨투어? contour. 모서리 란 뜻임. 특정 영역의 경계를 따라 같은 픽셀값을 갖는 지점을 연결하는 선. 특정 물체의 모서리를 출력하는데 사용됨. 이것도 고전적 방법보다는 딥러닝으로 모서리를 검출함. 엣지 검출은 모든 모서리를 검출해버림. 컨투어는 엣지 검출 한 후에 허프 변환으로 선을 이어버림. 

캠쉬프트는 소실점을 이용해 상대적 거리 정보를 뽑아낸느 방식임. 소실점을 먼저 구할 필요가 있음. 민쉬프트 업글버전이란거지.

어제배운 알고리즘을 다 쓰고 오늘 배운 내용은 테스크일 뿐. 

아무사진이나 구해서 직접 해볼거임.