# 2023-1-PSAT-team-timeseries
2023년 1학기 통계분석학회 P-SAT 시계열자료분석팀 주제분석


## 💻 프로젝트 소개
<주식 초보자의 리스크 관리를 위한 매수/매도 추천 서비스>📈

주식 관련 정보 및 흐름을 이해하기 어려운 '주린이'😢를 위해, 주가에 영향을 줄 수 있는 요인에 대한 데이터로부터 모델이 매수/유지/매도를 학습하여 그 결과를 추천 -> 투자에 대한 쉽고 간단한 인사이트를 제공!😊

활용 데이터: 주식 시세 추이, 투자자별 거래 실적, 외국인 보유량, 공매도량, 국내 기사, 영문 기사, 네이버 증권 토론방 게시글, 네이버 검색량, 코스피, 비트코인 거래, 경제심리지수, 뉴스심리지수, 산업생산지수, 소비자물가지수, 소비자신뢰지수, 소비자심리지수, 실업률, 한국은행 기준금리, 환율

데이터 출처: 한국거래소, 한국은행 경제통계시스템, KOSIS, invest.com, 네이버 증권, 네이버 데이터랩, 빅카인즈, CNN

개발 기간: 23.04.16 ~ 23.05.19


## ❤️ 팀 구성 및 역할
- 김민(팀장): 데이터 수집, 데이터 전처리, Y~X EDA, 변수선택(KS검정), XGB, LSTM-CNN, LGBM
- 김동환: 등락률 라벨링, 데이터 전처리, Y~X EDA, 변수선택(인과관계검정), VAR, LGBM, SVM, log reg
- 서유진: 데이터 수집(+크롤링), 데이터 전처리, X변수 EDA, LSTM회귀(threshold자동화)
- 이수린: X변수 EDA, 변수선택(PCA, 요인분석, VIF, importance), XGB, NaiveBayes
- 장다연: 데이터 전처리, 한글/영문 기사 감성분석, randomforest, XGB, LGBM


## 🔍 분석 흐름
1. 데이터 수집
2. 데이터 전처리 (기사 데이터 감성분석, 데이터 병합, 결측치 보간, 자료형 수치형으로 통일, 시간 순 정렬)
3. EDA (X변수간 EDA, Y~X변수간 EDA)
4. 등락률(continuous) -> 매수/유지/매도(categorical) 라벨링
5. 변수 선택 (인과관계 검정, VIF, PCA, 요인분석, feature importance, KS검정 시도)
6. labeled y변수 예측 모델링 (with imbalanced class problem)
7. 예측 결과 시각화 및 결과 분석


## 🚨 difficulty
매수/매도에 비해 예측 라벨의 수가 많아서 클래스 불균형이 심각했음

💡 solutions
- 노력1. 단순 정확도나 f1-score가 아닌 평가지표 커스텀을 통해 프로젝트 목적에 적합한 모델 선택 (ex. 매수, 매도의 정확도, 정밀도의 평균 / 매수, 매도, 유지 정확도의 평균 etc)
- 노력2. 모델 학습 시 클래스별 샘플 가중치 반영
- 노력3. 라벨 회귀 예측 -> 검증 set으로 분류 threshold 결정 -> 최종 분류
