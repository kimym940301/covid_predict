# 경제와 코로나 데이터를 통한 코로나19 동향 예측

## 개발동기
  - 미래에 또 다른 전염성 유행병이 발병하면 코로나19의 경험을 통해 국가적 방역 대책이 시행될 것이고 방역 대책이나 다양한 우발상 황에 따른 확진자의 변화가 코로나19와 유사하게 진행될 것이라고 생각한다
  - [한국정보통신학회논문지 “시계열 데이터를 활용한 코로나19 동향 예측”(수원대학교 논문)] (https://www.kci.go.kr/kciportal/ci/sereArticleSearch/ciSereArtiView.kci?sereArticleSearchBean.artiId=ART002741446)이 라는 코로나 데이터를 시계열 데이터를 통한 확진자 예측 모델를 기반

## 분석목표
  - 코로나와 경제 데이터를 통해 다음날 코로나 확진자를 예측하는 모델 생성 
  - 초기 예측이 어려운 시계열 데이터를 통한 모델이 아닌 다양한 데이터를 통한 모델 생성
  
## 모델 소개
  - 코로나 전날 확진자와 관련 데이터를 통해 다음날 확진자 예측
  - 

## 분석방법
  - 정부 발표자료를 통한 데이터 수집 
    - 일일 확진자 : today_confirmed (https://ncov.kdca.go.kr/)
    - 일일 사망자 : today_dead (https://ncov.kdca.go.kr/)
    - 1차 백신접종자 : first_shot (https://ncv.kdca.go.kr/)
    - 2차 백신접종자 : second_shot (https://ncv.kdca.go.kr/)
    - 3차 백신접종자 : third_shot (https://kdx.kr/data/view/30239)
    - 동절기 백신접종자 : winter_shot (https://ncv.kdca.go.kr/)
  - 경제 및 국가 통제 데이터 수집
    - 코스 : kospi (https://finance.yahoo.com)
    - 
  - 시각화를 통한 데이터 분석
  - 코로나 데이터를 적용한 모델 생성
    → 회귀분석을 통한 예측(OLS모델을 통한 최적화로 Decision Tree 모델 적용)
  - 코로나 + 경제 데이터를 적용한 모델 생성
    → 회귀분석을 통한 예측(OLS모델을 통한 최적화로 Decision Tree 모델 적용)
  - 하이퍼파라미터 튜닝, 앙상블 기법을 통해 최적화 시도
  
## 사용기술 및 개발환경
  - 데이터 출처: 코로나 정부 사이트, 정부 발표자료 참고, 야후(경제)
  - 수집방법: csv 파일 다운로드
  - 개발도구 : pandas, numpy, seaborn, sklearn
  - 개발언어 및 프레임워크 : python
  
## 분석 결과
  - 코로나 데이터 적용 예측 모델
     → OLS R-Squared : 0.937 / Tree R-Squared : 0.994, MAE : 2599
  - 코로나 + 경제 데이터 적용 예측 모델
     → OLS R-Squared : 0.938 / Tree R-Squared : 0.994, MAE : 2378.657
  - 하이퍼파라미터 튜닝 / Voting 적용
     → R-Squared : 0.99385, MAE : 3063.053 / 0.99301, MAE : 2971.491
  - 최종 모델(코로나 + 경제 데이터에 p-value 높은 컬럼 제거한 모델)
    → OLS R-Squared : 0.938 / Tree R-Squared : 0.994, MAE : 2378.657
