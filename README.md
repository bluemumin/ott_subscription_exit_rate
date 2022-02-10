# 1. OTT 신규 가입 후, 이탈자 파악을 위한 재 구독 여부 분류 모델

- Member: 김경록
- Status: Complete
- Tag: Competition
- 사용언어 / 핵심 라이브러리
  python(3.8) / Pandas, LightGBM

# 2. Why
OTT 플랫폼에 신규 가입한 구독자의 3주간의 시청 기록을 활용하여, 1개월 뒤 OTT 서비스를 다시 결제를 할 것인지를 사전 분류함.

# 3. Data

[그룹사 경진대회 데이터 제공] (데이터 외부 유출 금지 -> 미 업로드, 관련 결과 삭제)

# 4. 분석 방법
(a). Data Preprocessing 
  - EDA : 고객 결제 사항 + 시청 기록 데이터

  - 변수 내 항목 간소화 : 결제 코드, 결제 등록 기기, 컨텐츠별 시청 기기

  - 파생변수 생성 : 최신 컨텐츠 시청 기간 그룹화, 유저 컨텐츠 시청 퍼센트, 결제 후, 마지막 시청일자 gap 계산

  - Data Reduction : 유저별 과도한 컨텐츠 시청 수, 최신 컨텐츠 과다 시청 수 절삭

	<p>(3). Model & Algorithms <br/>
		- LightGBM 1차, 2차 수행 --> 최적의 parameter 확인(gridsearch + 5-fold) --> 최적의 threshold 확인(5-fold)  <br/>
		- Xgboost, Randomforest 모델링 후, ensemble 수행 --> 결과 차이 x로 최종 제외 <br/>
	<p>(4). Report <br/>
		- LightGBM 결과 기반, 재구독 여부에 효과적인 변수 list 작성 <br/>
	        - 최종 등수 27/248(팀) 기록 (1등과 f1-score 0.01 차이) <br/>
		- 두 평가 기준인 f1-score와 accuracy의 차이가 없는 균형적 모델 작성</p>
	<p>(5). Review <br/>
		- 긍정적 사항 : 유저의 컨텐츠 시청 퍼센트(시청 시간/컨텐츠 길이) 파생 변수가 모델 개선에 효과적 <br/>
	        - 피드백 : 결제 후, 마지막 시청일자 gap보다, 1주차별 시청 시간의 증가/감소 여부가 더 효과적임을 예상함 <br/>
		- Futher Research : 해당 주차 드라마/영화 순위(외부 데이터) 활용한 인기 콘텐츠 선호도, <br/>
		&nbsp;+ (ott 내 영화 추가 구매 여부, 코인 추가 거래 내역 등) 플랫폼 적극적 이용 수치 인사이트 개발 가능 예상 </p>
		
*보러가기: [ott 재구독 여부 분류 코드](https://github.com/bluemumin/ott_subscription_exit_rate/blob/main/ott_%EC%9E%AC%EA%B5%AC%EB%8F%85%EC%97%AC%EB%B6%80_%EB%B6%84%EB%A5%98.ipynb)*

*문의 후, 보기 가능(private): [ott 재구독 여부 실제 코드](https://github.com/bluemumin/wavve_subscription_exit_rate_private)*
