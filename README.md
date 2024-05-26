# Shakespeare

• shakespeare_train.txt 

셰익스피어의 대사들로 구성된 텍스트 데이터셋 
<br>
• dataset.py
  
텍스트 데이터셋을 불러와 분석 및 처리

<br>
• main.py

1) 데이터셋 로드: dataset.py 파일의 Shakespeare 클래스를 사용하여 shakespeare_train.txt 파일을 불러옴
 
2) 모델 선택: RNN과 LSTM 모델을 선택
 
3) 훈련 및 검증: 모델을 학습하고 각 epoch마다 훈련 손실과 검증 손실을 출력
 
4) 결과 저장: 훈련 및 검증 손실을 그래프로 저장하고, 학습된 모델을 저장

(RNN)
![RNN](https://github.com/jimmynkim/Shakespeare/assets/75557016/320d97b9-c405-4876-9821-2cb2d653362f)

Epoch 값이 1일 때, Train Loss 값은 2.546, Validation Loss 값은 2.342

Epoch 값이 30일 때, Train Loss 값은 1.414, Validation Loss 값은 1.426

(LSTM)
![LSTM](https://github.com/jimmynkim/Shakespeare/assets/75557016/09cf75bc-bc29-4108-92af-451c17745bf7)

Epoch 값이 1일 때, Train Loss 값은 2.301, Validation Loss 값은 2.285

Epoch 값이 30일 때, Train Loss 값은 1.045, Validation Loss 값은 1.123
<br>
• model.py

RNN과 LSTM의 신경망이 정의되며 텍스트 데이터셋을 학습시키기 위해 사용

RNN :
- RNN 기반의 문자 레벨 신경망 모델
- 임베딩 레이어, RNN 레이어, 완전 연결(FC) 레이어로 구성
- forward 메서드는 입력 데이터를 임베딩하고 RNN을 통해 출력을 생성
- init_hidden 메서드는 초기 은닉 상태를 생성

LSTM :
- LSTM 기반의 문자 레벨 신경망 모델
- 임베딩 레이어, LSTM 레이어, 완전 연결(FC) 레이어로 구성
- forward 메서드는 입력 데이터를 임베딩하고 LSTM을 통해 출력을 생성
- init_hidden 메서드는 초기 은닉 상태를 생성
<br>
• generate.py

학습된 모델을 사용하여 새로운 텍스트를 생성
1) 라이브러리 임포트: argparse, os, torch, numpy, device와 datasets, RNN, LSTM 등 필요한 라이브러리를 임포트
 
2) 텍스트 생성: generate 함수를 이용해 학습된 모델과 시작 문자열, 온도, 생성할 문자 수를 받아서 새로운 텍스트를 생성
 
3) 스크립트 실행: argparse를 사용하여 명령줄 인수를 파싱하고 주어진 인수에 따라 모델을 로드하고 텍스트를 생성

temperature는 모델에서 생성된 텍스트의 다양성을 제어하는 역할을 함

- temperature가 낮으면, 텍스트가 일관되고 구조화되게 작성되어 문법 규칙을 잘 따르며, 이해하기 쉬운 문장 생성 

- temperature가 높으면, 텍스트는 무작위성이 높아져 이해하기 어려운 단어와 문장이지만 다양하고 창의적인 문장 생성
