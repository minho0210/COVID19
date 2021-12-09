# COVID19 Visualization
본 프로젝트는 2020년 3월 이후의 대한민국에서의 PCR검사를 통한 COVID19 확진자와 그에 따른 사망자에 대한 현황과 백신 접종 현황에 대한 시각화를 목표로 한다.
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
- VaccineSeoul : 서울특별시 백진 접종 현황
- VaccineKorea : 대한민국 행정구역별 백신 접종 현황

> District - DistrctRaw를 각 행정구역을 column으로 설정하여 재구성한 전처리가 진행된 table

## Code

### `corona.py`

## 데이터 출처
- 공공데이터포털 : https://www.data.go.kr/
- 서울 열린데이터 광장 : https://data.seoul.go.kr/
- 행정안전부 : https://www.mois.go.kr/frt/sub/a02/openInfoList/screen.do
