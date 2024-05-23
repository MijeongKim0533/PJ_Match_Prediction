# 프리미어리그 경기 승무패 예측 프로젝트

## 1. 프로젝트 주제
프리어리그 경기 승무패 예측하기

## 2. 프젝트 목적
- 프미어리그 경기, 선수, 클럽  데터를 바탕으로 트렌드 분석 및 대시보드 구축
- 데이터 기반 승무패 예측모델 개발

## 3. 분석과정
1. Data Flow<br>

 <p align="center"><img width="380" alt="image" src="https://github.com/MijeongKim0533/PJ_Match_Prediction/assets/152786534/fee62433-da98-41f8-8cc8-ad76494c8d63">

2. 동적 페이지(Football Manager)크롤링 : 선수 능력치 데이터 수집
3. 파생변수 생성 : 각 팀의 누적 경기 수, 누적 승률 등 누적기록 관련 6개 파생변수 생성
4. Moving Average : 경기내용 관련 변수는 이전 한 경기가 아닌 3경기 평균 값을 사용하여 모델링
  
  <p align="center"><img width="500" alt="image" src="https://github.com/MijeongKim0533/PJ_Match_Prediction/assets/152786534/96464445-a56e-4741-93bf-5a115632a3ec">
  
## 4. 대시보드
  <p align="center"><img width="500" alt="image" src="https://github.com/MijeongKim0533/PJ_Match_Prediction/assets/152786534/0d846b55-3336-4989-9d18-12655e414605">

## 5. 모델링
- Feature Selection : feature importance와 RFECV를 사용하여 영향을 주지 않는 변수는 제외하고 8개의 변수를 선택하여 모델링
- 시간변수를 고려해 최근을 기준으로 validation set 설정
- 최종선택모델 : GradientBoostingClassifier<br>
    정확도 0.56 -> 0.62로 향상 (validation set 기준)
    (참고논문 정확도: 0.44~0.6, 2022년도 기사 AI 예측률 65%)
    - 라벨인코딩으로 숫자의 크기에 영향을 받지 않는 트리계열 모델 선택
    - 변수 선택 전에 많은 변수들로 모델링을 해서 다양한 특성을 고려하여 예측을 수행하는 앙상블 모델 선택
    - 앙상블 모델 중에서 성능이 좋았던 Random Foreset, Gradient Boosting, XGBoost 모델 선택
  
  <p align="center"><img width="450" alt="image" src="https://github.com/MijeongKim0533/PJ_Match_Prediction/assets/152786534/e24450a3-8f55-410d-8255-7a88dfe5174a">

## 6. 결과
- 최근 경기(2024-04-13 ~ 2024-04-24) 예측 정확도 0.54
- 역할 : 선수 능력치 데이터 수집, 모델링, 선수 및 클럽 대시보드 구축