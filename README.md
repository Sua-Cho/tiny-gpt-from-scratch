

# tiny-gpt-from-scratch 
GPT-2의 핵심 구조인 Decoder-only Transformer를 PyTorch로 직접 구현하고, 한국어 텍스트를 이용해 학습 및 생성 실험을 수행했습니다. 

## Project Structure 
``` text
├── tiny_gpt            # chat gpt 2.0 구현
└── korean_novel.txt    # 한국 소설 txt 파일 
```

## Model Architecture 
``` text
이 프로젝트는 GPT-style decoder-only Transformer 구조를 따르며, 구성 요소는 다음과 같습니다.

- Token Embedding: 문자를 숫자 벡터로 변환
- Positional Embedding: 문자의 위치 정보를 추가
- Causal Multi-Head Self-Attention: 이전 문자들만 참고하여 다음 문자를 예측
- Feed Forward Network: Attention 결과를 추가적으로 처리
- Residual Connection: 안정적인 학습을 위한 연결 구조
- Layer Normalization: 학습 안정화
- Linear Head: 다음 문자 확률 출력

Result :

"시작 문장을 입력하세요: 김" 

위와 같이 입력하면, 모델은 `김`이라는 첫 글자를 기준으로 다음 문자를 하나씩 예측하면서 새로운 문장을 생성합니다.
기본적으로 최대 200개의 새로운 문자를 생성하도록 설정했습니다. 

```

## Limitations 
``` text

- Generation Length

생성 길이(max_new_tokens)는 200으로 제한했습니다.

더 긴 문장을 생성할 수 있지만, 작은 데이터셋과 작은 모델에서는 생성 과정에서 오류가 누적되어 문장이 부자연스러워지는 현상이 발생했습니다.

따라서 비교적 안정적인 결과를 얻기 위해 생성 길이를 200자로 제한했습니다.

- Training Epochs

학습 Epoch 수는 20으로 설정했습니다.

Epoch를 증가시키면 학습 데이터에 더 잘 적합될 수 있지만, 데이터 규모가 작기 때문에 과적합(Overfitting)이 발생할 가능성이 있습니다.

따라서 학습 시간과 모델 일반화 성능을 고려하여 20 Epoch를 사용했습니다.

```



