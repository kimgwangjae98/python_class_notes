은닉층 없어도 다차함수. 호라성화 함수가 출력층에 있기 때문임. 활성화 함수가 다차함수인지를 결정함
물론 은닉층이 없으면 사실 일차든, 다차 함수든 뭘 쓰든 별다른 성능차이가 나지 않기 때문에.

MNIST 지금 쓰는 신경망에 층을 더 늘리면 성능이 향상될까? 아닐까?
LOSS함수가 0에 가까워져야 되는데, 그래프가 일직선으로ㅗ 나오면 오버피팅이 된것. 
이는 가중치 변화가 없는것. 가중치 변화가 0에 가깝다는것. 
가중치의 정의는 대충 우리가 생각하는 이 데이터들의 특성을 담기위한 그릇임. 

2차원 다차그래프로 예시를 들어봄. 데이터 특징(픽셀이 가지는 숫자같은거)이 여러 분포가 있다고 함. 
오버피팅이란 데이터의 특성에 따라 맞추거나 특정값으로 가는것. 파라미터 수가 적었을 때 억지로 맞추면 오차의 변화가 없음. 그게 오버피팅
W는 특징을 담는 특성임. 어떤 숫자가 들어왔을 때 특징을 담을 수 있음. 특징이 많으면 가중치를 늘린다. 즉 모델을 키운다(W를 늘린다). 특징 다 담을 수 있어진다! 특징이 적으면 1차식도 가능
데이터가 복잡한지에 따라 신경망의 모델을 판단할 수 있다. 
복잡한지는 어떻게 판단하는지? 사람이 한눈에 구분할수 있으면 특징이 명확한것. 구분못하면 특징이 희미한것.
모델 크기를 늘리면 좋다는게 이렇기 때문.
특징이 산발되어있는 경우 어떤 그래프를 써도 안되는 경우엔. 포기한다(X). 특징을 뽑아내야됨.
특징은 컴퓨터가 뽑아내야됨. 그게 특징 추출기가 하는 역할. 컴퓨터가 특징을 인식하도록 하는거. 특징들을 분해해서(잘게 쪼개서) 특징들을 뽑아냄.
이런 특징들을 컴퓨터가 잘 구분해낸다고함. 왜그럴가? 
ABC 특징이 엄청 흩어져있음. 알고보니 ABC가 서로 특징이 약간 겹쳐졌다는 사실을 분해해서 알게됨. 특징이 겹쳐져있음. 특징이 혼합된걸 분해해서(고양이 인식같은거) 사람의 특징과 비슷하다고 판단하는거지. 가장 효과적인 방식이 콘볼루션. 너무 잘게 쪼개면 형채를 알기 어려움. 즉, 특징을 잘게 자르게 되면 오히려 특징이 겹치지 않는 경우가 발생해서 학습이 어려울수 있음. 적당히 분해하는것이 중요함. 자신이 직접 실험해봐야됨. 특징 추출기를 여러개 넣어서 확인해봐야됨.

은닉층의 노드를 늘리는 거랑 은닉층 갯수를 늘리는 거는 가중치를 늘리는 것이지 않느냐?
은닉층의 노드를 늘리면 가중치를 담는 그릇을 늘리는 것임. 너무 늘리면 특징 다 담고도 남은 노드에 똑같은 특징이나 이상한 특징이 담겨서 성능이 안좋아질수있음. 은닉층 갯수를 늘리는 것은 레이어(다차함수)를 늘리는 것. 약간 다른 개념임. 은닉층의 노드 갯수는 처음에 점점 늘려가다가 나중에 점점 줄이는 방식임. 특징을 점점 분해해 갔다가 특징을 점점 합쳐가는거지. 은닉층 갯수가 줄어들면 담긴 특징들을 판단할 수 없다는 의미겠네. 
일부러 일반화 성능 시험할려고 노드 중 일부를 없애기도함.
아니면 입력 데이터에 약간의 변형을 시켜 넣어보기도 함. 정상이랑 변형시킨거 다 때려박아서 학습시킴.
특징 추출기는 입력 데이터를 신경망을 돌리기 전에 쓰이는가, 아니면 신경망 속에 포함되어있는가. 
그럼 그 노드와 은닉층의 갯수도 어떻게 판단하는거지? 특징 추출기가 좋으면 노드랑 은닉층 갯수를 줄일 수 있지 않을까? -> 그렇데 이전에 있던거에 추출기 쓰면 줄일 수 있데.
일단  노드몇개 은닉층 몇개써야하는지는 일단 무작정 실험해봐야 알수있음. 그걸 지금 하고있는거고.

우리의 목표 : 일반화 성능을 높게 신경망을 구성하는 것. 

로스펑션은 실측값과 예측값의 차이를 나타내는 함수. 역전파할때 미분을 하게되는데 미분을 했을 때 함수의 형태는 미분 가능해야됨(중요!) 그리고 컴백스드해야됨. 그게뭐야? '컴백스드 하다는 얘기'는 손실함수 그래프에 선을 2개 그엇을 때 선이 교차하는 점이 2개여야 한다. 왜 그래야 하나? 손실함수를 미분을 해버리면 미니멈이 여러개 생김. 컴백스드하면 미니멈이 하나임. 컴백스드 하지 않으면 미분해서 0인 값이 여러개라 학습이 안될수 있음. 손실함수는 그냥 연구 잘된거 쓰면됨. 손실함수를 적재적소에 쓰는 것도 중요함.

교차엔트로피 오차(로그쓰는함수 있잔아)를 픽셀 하나하나에 다 적용하면 컴백스드함.
일단 손실함수를 적절한 걸로 서야한다. MSE도 컴백스드함. 
MSE는 왜 썼느냐? MSE는 다차함수이고 미분가능하다. MSE를 미분하면 최솟값이 하나 존재하고 컴백스드하다. 그렇기 때문에 MSE로 학습이 돌리면 학습이 잘된다.

제일 중요한것 : 모델이 복잡한거, 손실함수가 얼마나 중요한가. 

모델을 크게 만들수록 좋은가? 뭐가 좋다는거지? 안좋은건 시간하고 인력이랑 비용. 그러나 우린 시간인력비용이 한정적이지. 
모델쪽으로 중점을 두고 생각해보자. 모델 복잡해지면 어떨까? 계산량이 많아짐. 특징도 잘 추출해낼 것. 
너무 많이 학습해버러셔 이상한 답을 도출해 낼 수 있기에 모델을 크게 만들수록 좋은건 아닐것이야.
아니야 좋다! 왜냐? 오비피팅 문제가 있을 수 있지만 드롭아웃이라던가 레귤레이션으로 오버피팅 문제를 방지할 수 있기 때뮨. 
물론 일정 수준이상 복잡해지면 처음에 입력한 데이터의 특징이 희미해짐. 즉, 모든 데이터에 대해 처음 넣은 데이터를 기억하지 못하는 문제가 발생함. 즉 그래디언트 소실 문제가 발생함. 
그걸 트랜스포머가 그 문제를 깨버림. 그래서 프랜스포머가 중요함. 어탠션맵에 특징들을 싹다 담을 수 있어서 그럼. 관계도를 특징마다 연결시켰기 때문.
일단 우리가 지금 배우고 있는 것은 트랜스포머 이전임. 일단 우린 적절한 모델을 선택을 해야됨. 트랜스포머 이전이니까.



