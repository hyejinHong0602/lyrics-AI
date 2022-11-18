# lyrics-AI
### LINC+ 사업단 산학공동기술개발과제 참여(2021.09 - 2021.12)
***
   

### 목적
가수의 작사스타일이 반영된 가사를 생성하고, 생성된 문장에 어휘나 표현에 차이가 있는지를 비교
***
### 베이스모델
#### KoGPT-2  
Open-AI 사의 GPT-2를 약 20GB의 한국어 데이터셋으로 사전학습한 모델. SKT-AI에서 한국어 성능 한계 개선을 위해 개발하였음. 
***
### 데이터셋
현재 활동하는 가수 중에서 가사의 어휘나 분위기가 독특해 스타일이 분명하게 드러나는 가수 10팀을 임의로 선정.

  
***
### 실험
앞서 구축한 한국어 노래 가사 데이터셋을 이용하여 KoGPT-2모델에 finetuning을 시행함.
```
fine-tuning
python main.py --epoch=200 --data_file_path=dataset/~~~.tsv --save_path=./checkpoint/ --batch_size=1

generator
python generator.py --temperature=1.0 --load_path=./checkpoint/~~~.tar --tmp_sent='시작'
```
***
### 결과 예시

|시작 단어|생성 가사|
|------|---|
|너를|너를 부르고 싶었어 그래 불러줘줘 정말 예뻐지자고 불렀던 그 목소리 널 불러줘 정말 예뻐지자고 불러줘 정말 예뻐지자고 불러줬던 그 목소리 잊고 살다 보니까 이렇게 아름다운날만 있다면 참 좋겠습니다 좋은 꿈 꾸시고 안녕히 계세요|

***
### 평가
1. BLEU SCORE<br>
<p align="left"><img src="https://user-images.githubusercontent.com/60168680/148738737-855f4d93-396b-49ff-b8e3-45a6ca661ef7.png"></p><br>


2. BERT SCORE
<p align="left"><img src="https://user-images.githubusercontent.com/60168680/148739417-0dbc7dc5-d6fe-4ec5-aeac-7adff63303ff.png"></p><br>


***
### 참고
https://github.com/gyunggyung/KoGPT2-FineTuning <br>
https://github.com/sohyeon98720/NLP
