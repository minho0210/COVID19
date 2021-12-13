# COVID19 Visualization
본 프로젝트는 2020년 3월 이후의 대한민국에서의 PCR검사를 통한 COVID19 확진자와 그에 따른 사망자에 대한 현황, 백신 접종 현황에 대한 시각화를 목표로 하고 이를 통해 현재 COVID19에 관한 대한민국의 현 주소를 탐구하는 것을 목표로 한다.
## 팀원 구성
- 조민호 (www.github.com/minho0210)
- 김민형
- 박경빈
- 최원희

## 흐름도
![image](https://user-images.githubusercontent.com/85331657/130828187-2c897175-7917-4a83-87c8-b09a464d68aa.png)
1. open API를 통한 COVID19 관련 데이터 수집
2. Python Pandas를 사용한 전처리
3. AWS 내 MySQL DB에 전처리한 데이터 table 형태로 저장
4. MySQL과 tableau 연동
5. tableau 시각화

## ERD
![image](https://user-images.githubusercontent.com/85331657/145345101-5f3e12ea-7e36-4857-9307-a5e62e19b432.png)
- Population : 대한민국 행정구역별 인구 현황
- Decide : 일자별 PCR 검진 및 확진 관련 데이터
- DistrictRaw : 각 행정구역별 일일 확진자
- District : 지역별 신규 확진자
- VaccineSeoul : 서울특별시 백신 접종 현황
- VaccineKorea : 대한민국 행정구역별 백신 접종 현황

> District - DistrctRaw를 각 행정구역을 column으로 설정하여 재구성한 전처리가 진행된 table 데이터

## Code

### `corona.py`
- line 1 ~ 13 : 필요한 패키지 import
  -  `request` : URL을 통해 데이터 통신을 하기위한 패키지
  -  `xmltodict` : xml형태의 데이터를 dict 변수로 저장하기 위한 패키지
  -  `pymysql`,`sqlalchemy` : AWS내 MySQL DB에 데이터를 저장하기 위한 패키지
- line 15 ~ 17 : AWS 서버 IP address 및 DB 설정
- line 20 ~ 31 : 데이터 수집을 위한 URL 주소 및 serviceKey 설정
- line 37 ~ 62 : 일자별 검진 및 확진 관련 데이터 ETL (Dicide)
- line 67 ~ 104 : 행정구역별 일일 확진자 데이터 ETL (District)
- line 109 ~ 133 : 행정구역별 신규 확진자 데이터 ETL (DistrictRaw)
- line 138 ~ 154 : 서울특별시 백신 접종 현황 데이터 ETL (VaccineSeoul)
- line 158 ~ 190 : 대한민국 행정구역별 백신 접종 현황 데이터 ETL (VaccineKorea)

## tableau

- 날짜 및 지역별 검사 및 확진자 세부 대시보드

![image](https://user-images.githubusercontent.com/85331657/145747001-9dc1fe71-8e2c-41f2-9dc7-075dc9f151b8.png)

- 특정 기간 내 광범위 자치단위 별 확진자 비교

![image](https://user-images.githubusercontent.com/85331657/145747031-37ab3127-9541-4fe6-a1c5-0dc2be8d3062.png)

- 검사자 수 대비 확진자 수 비교 및 확진자 수 대비 사망자 수 비교

![image](https://user-images.githubusercontent.com/85331657/145747046-a6a1fabb-30c2-4451-bad9-4989dec38621.png)

- 서울시 접종 대상자 접종률 및 전체 인구 대비 접종률

![image](https://user-images.githubusercontent.com/85331657/145747050-81e9544b-70e4-4ef2-ac0f-70ccab36145e.png)

- 전국 자치단위 별 백신 접종률 비교

![image](https://user-images.githubusercontent.com/85331657/145747059-d4c955eb-5bcf-48c9-a53a-4dbd4aee11e4.png)


## 결론

![image](https://user-images.githubusercontent.com/85331657/145747470-ef8dfbb2-7d6c-44d8-81d3-1d9094ff4a5e.png)
> 해당 결론은 프로젝트가 진행된 2021년 8월 중순까지의 데이터를 통해 내린 결론이다.

## 데이터 출처
- 공공데이터포털 : https://www.data.go.kr/
- 서울 열린데이터 광장 : https://data.seoul.go.kr/
- 행정안전부 : https://www.mois.go.kr/frt/sub/a02/openInfoList/screen.do
