책은 내일까지 땔수있음. 알고리즘 위주라 전부 이해는 못할 것임. 박찬호처럼 유용한 말을 많이 하시네. 기초는 해야됨. 코드를 이해하는 능력을 기르기 위함. 코딩은 그저 기초일 뿐임 이제. 남이 짜준 코드 활용할 줄 알아야지. 코딩에 너무 매몰되지는 말자. 그냥 코드 해석만 잘 해보자. 그리고 시스템의 흐름이 어떻게 되는지 알자. 어렵다 싶으면 인내하기. 그 어려움에 적응하는 신경 회로 구축이 천천히됨. 결국 문제 해결능력이 개발자에게 중요한 능력이다.

서포트 벡터 머신은 분류 모델임. 참고로 회귀 모델는 연속적 데이터를 학습해서 처리하는 알고리즘 모델임. 서포트 벡터 머신은 데이터를 분리하긴 하는데 벡터, 즉 직선을 이용해 분리(=분류)함. 그러니까 직선(=벡터) 하나로 범주(클래스)를 분류함.  그러니까 벡터 찾기지. 잘 나눠주는 벡터. 그 벡터는 y=wx+b 로 표현되. 벡터를 초평면이라고 부르는거지. 왜? 몰?루 마진은 그 점과 벡터 사이 최단거리(직각). 직선과 점 사이 거리를 찾을 수 있지. 서포트 벡터 머신은 간단하게 이게 끝. 두 클래스 사이를 잘 나누는, 두 클래스 사이 거리를 같게 나눠주는 직선이 필요하다. 3차원이면 평면으로 나누지. 선형문제는 직선으로 구분가능하다!

마진, 서포트 벡터, 커널 함수 개념 이해하기. 단어도.

커널 함수는 곡선으로 검출해야 할 때 쓰임.  XOR 같은거 말야. 커널 함수는 직선으로 분류가 불가능할 때 3차원으로 차원을 확장해 평면으로 구분하는 함수이다.

서포트 벡터 머신은 직선 or 평면 벡터로 분류하는 알고리즘. 선형 문제 해결에 쓰임
커널함수는 평면에서의 비선형 문제를 해결하기 위하 사용하는 함수. 2차원을 3차원으로 변환해 평면 벡터로 분류하여 비선형 문제를 해결함.

서포트 마진의 개념은 중요함. 약간의 오류를 직석이나 평면에 준다고 이해하기. 실제 데이터는 명확하게 구분이 안가기 때문에(노이즈있음) 소프트 마진을 줌. 그림에선 점선이지. 선에서 가장 가까운 요소까지의 거리를 마진으로 정의했음. 하드 마진은 선형 분리가 가능할 때 쓰이는 빡빡한 오차고 소프트 마진은 선형 분리가 불가능 할 때 약간의 오차를 감수하고 직선을 그어서 만들 때 사용한다.
결정경계는 직선을 의미하고 서포트 벡터를 말하는거지. 같은 단어다. 서포트는 그 점들을 기반으로 벡터를 그엇기 때문에 서포트 벡터란 이름이 지어진거지. 챗 gpt에게 물어봐도됨. 퍼플랙시티ai에게 물어봐도됨. 

베이지안 분류기는 분류모델임.  회귀모델은 연속적인거 예측하는거. 베이지안 결정 이론은 조건부 확률을 이용함. 어째든 조건부 확률을 기반으로 분류한다.

앙상블 학습은 어때까지 쓴 모델 다 합쳐서 학습시킨다는거임. 병렬로 학습기 연결해서 쓰거나(배깅) 직선으로 연결하는 방식(부스팅)도 있음. 약한 모델은 빠르고 부정확한데 강한 모델은 정확하고 느림. 선으로 공간을 나누는 학습기들을 여러개 겹처 두 클래스를 분류하는 방식은 직렬 연결로 학습기를 연결해서 쓰지. 앙상블 처럼 신경말 모델도 작은거 여러개 써서 큰 신경말 모델같은 성능을 낼 수 있다고도 함. 모델을 계속 거쳐서 최종 결과가 나옴. 틀린 포인트들에 가중치를 크게 줘서 그 포인트를 기준으로 분류를 하게 함을 계속 진행시켜서 잘 분류할 수 있도록 유도함. 직선을 여러개 이어서 구분하는 그림으로 나온다.

랜덤 포레스트는 배깅의 파생 모델임. 학습기 병렬 연결의 파생형. 병렬을 트리로 적용해서 만들지. 트리의 나뭇가지 끝에서 선택한 표본을 병렬 연결해서 학습시키지.


모르는 키워드는 나중에 메모해서 찾아보고 연계해보면 좋다. 실전에는 새로운걸 더 배워야 할 때가 많을  것임. 필요한 부분만 공부해서 쓰면 된다. 상사도 모르는 경우가 많아 직접 찾아써야되... 요즘 트랜드도 유튜브로 보기.

트랜드 민감해지기. 자료검색 직접 해보기(스스로 답찾기). 챗 gpt 클로드 ai로 **생산성 높이기**. 생산성이 회사에서 중요하다.

클러스터링은 데이터를 묶고 그룹을 찾는게 클러스터링. 비지도 학습(레이블=정답 없는 학습)에 썼음. 

냅킨ai 클로드ai 챗gpt, 등등...