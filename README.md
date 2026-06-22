

# tiny-gpt-from-scratch 
GPT-2의 핵심 구조인 Decoder-only Transformer를 PyTorch로 구현했습니다. 
사용자는 임의의 txt 파일을 입력할 수 있으며, 모델은 해당 텍스트를 학습한 뒤 시작 문장을 기반으로 새로운 문장을 생성합니다. 

이를 통해 Transformer 기반 언어 모델의 동작 원리를 직접 구현하고 실험하였다.

## Project Structure 
``` text
├── tiny_gpt            # GPT style Decoder-only Transformer
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

input : "시작 문장을 입력하세요: 이년!"

위와 같이 입력하면, 모델은 `이년!`이라는 첫 글자를 기준으로 다음 문자를 하나씩 예측하면서 새로운 문장을 생성합니다.
기본적으로 최대 200개의 새로운 문자를 생성하도록 설정했습니다.

```

## Limitations 
``` text

- Limited Context Window

모델의 Block Size는 64로 설정되어 있습니다.
즉, 다음 문자를 예측할 때 최대 64개의 이전 문자만 참고할 수 있습니다.
학습 시간이 늘어나는 것을 방지하고, 메모리 사용량을 고려하여 더 긴 문맥을 참고하지 않았습니다. 

- Generation Length

생성 길이(max_new_tokens)는 200으로 제한했습니다.
더 긴 문장을 생성할 수 있지만, 작은 데이터셋과 작은 모델에서는 생성 과정에서 오류가 누적되어 문장이 부자연스러워지는 현상이 발생했습니다.
따라서 비교적 안정적인 결과를 얻기 위해 생성 길이를 200자로 제한했습니다.

- Training Epochs

학습 Epoch 수는 20으로 설정했습니다.
Epoch를 증가시키면 학습 데이터에 더 잘 적합될 수 있지만, 데이터 규모가 작기 때문에 과적합(Overfitting)이 발생할 가능성이 있습니다.
따라서, 모델 일반화 성능을 고려하여 20 Epoch를 사용했습니다.


```



