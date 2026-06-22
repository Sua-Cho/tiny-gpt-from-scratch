

# tiny-gpt-from-scratch 
GPT 2.0을 구현한 프로젝트입니다. 

## Project Structure 
``` text
├── tiny_gpt            # chat gpt 2.0 구현
└── korean_novel.txt    # 한국 소설 txt 파일 
```


## Result 

```text
시작 문장을 입력하세요: 김
```

이라고 입력하면, 모델은 `김`이라는 첫 글자를 기준으로 다음 문자를 하나씩 예측하면서 새로운 문장을 생성합니다.

이 프로젝트에서는 기본적으로 최대 500개의 새로운 문자를 생성하도록 설정했습니다.

