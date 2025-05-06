# 목표 LLM
- 한국어 figurative language를 잘 이해하고 생성하는 LLM
- simile, metaphor, sarcasm, idiom 대상 

# 학습 계획 
- 학습 대상 모델: Qwen2.5 7B
- tuning 방법: 교재 참고 - 전체 fine-tuning, PEPT 튜닝
- 학습 데이터셋: 교재 내 KoAlpaca 데이터셋 참고

# 학습 데이터셋 설계 
- 데이터셋 구조: <https://huggingface.co/datasets/beomi/KoAlpaca-v1.1a>
- binary classification, categorical classification, cloze QA 스타일로 구성하여 다양한 학습이 가능하도록 함
  1) binary classification: figurative 표현인지 아닌지 구분하도록 함
     예) {input: "사촌이 땅을 사면 배가 아프다고, 동생이 로또에 당첨되니 몹시 심기가 좋지 않다.", output: "figurative"}
  2) categorical classicification: 해당 표현이 simile/metaphor/sarcasm/idiom 중에 어떤 표현인지 분류하도록 함
     예) {input: "다음 표현은 simile/metaphor/sarcasm/idiom 중 어떤 표현이 사용되었나요? <표현> 사촌이 땅을 사면 배가 ....", output: "idiom"}
  3) cloze QA: 주어진 짧은 대화에 대해 빈칸에 들어갈 표현으로 적절한 표현을 넣도록 함
     예) {input: "다음 대화의 빈칸에 들어갈 말로 알맞은 것은? <대화> ..... 그래서 사촌이 땅을 사면 ________. 1) 배가 아프다니까 2) 등이 아프다니까 3) 배꼽이 크다니까 4) 머리가 아프다니까." , output: " 1)"}


