# bpi-2011
본 연구는 경희대학교 ``프로세스마이닝`` 수업에서 진행되었습니다.

## Overview
BPI 2011 대회에서 제공된 네덜란드 산부인과 로그 데이터를 가공해 업무 프로세스를 파악하고 개선 방안을 제안하는 프로젝트를 수행했다.


### 데이터 설명
Dutch Academic Hospital에서 수집된 real-life log로, 산부인과 환자들이 진단 및 치료를 받은 기록에 대한 데이터이다. 환자들은 진단받고, 치료받는 과정을 각자의 상황에 따라 반복하는데 환자들의 이런 process에 대해 분석하기 위해 수집된 데이터이다.

### Attribute 설명
- 아래와 같은 기존 변수, 파생 변수를 활용해 분석을 진행했다.

1) Case
  a) CaseID, 즉 환자의 ID라고 할 수 있다.
  b) 0~1142의 값을 갖는다.
  c) 가장 많은 event가 수행된 case ID는 824로, 해당 환자에 대해 1814개의 event가 수행되었다.
2) Event
  a) 환자의 진단/치료/검사를 위해 어떤 activity가 수행되었는지에 대한 기록이다.
  b) 622개의 activity가 있다.
3) Time
  a) Timestamp, 시간이 기록되어 있지만 기본값을 가져 날짜만 의미가 있다고 볼 수 있다.
  b) 환자의 첫 event timestamp부터 마지막 event timestamp가 환자의 치료 duration이 된다. Duration이 가장 긴 경우에는 3년 이상, 짧은 경우에는 1-day (당일)이다.
4) Org
  a) Activity를 수행한 담당한 진료과이다.
  b) 총 43개의 부서가 존재하고, General Lab Clinical Chemistry가 전체 event log의 63% 이상을 수행했다.
5) Diagnosis
  a) 환자가 진단받은 병명의 집합이다.
  b) 관측된 진단 병명의 조합으로 구성된 집합 종류는 총 209개로 나타났다.
6) Diagnosis code
  a) 환자의질병들에해당하는질병코드의집합이다.어떤종류의병을앓는지알수있다.
  b) 관측된 진단 코드는 M11, M12, M13, M14, M15, M16, 106, 821, 822, 823, 839이다.
  c) 진단 코드의 조합으로 구성된 집합 종류는 총 51개로 나타났다.
7) Treatment code
  a) 환자에게 행해진 치료에 대한 코드의 집합이다.
  b) 치료 코드의 조합으로 구성된 집합 종류는 총 237개로 나타났다.

### 분석 방법
- Control flow model
  - 전체, 주요 진료과별, 주요 질병별, 내원 기간 별 work process를 살펴보았다.
  - 진료과: 영상의학과, 방사선치료과, 병리과, 산부인과, 진단검사의학과
  - 질병: M13 (자궁 경부), M16 (난소), M11 (외음부), M14 (자궁 )
- Social Network Model
  - dotted chart를 그려 진단 코드별로 어떤 순서로 어떤 부서를 거쳐가는지 파악했다.
  - 진료과간의 interaction 을 살펴보는 social network analysis를 진행했다. 병원 시스템상 환자는 다양한 진료과를 거쳐가고 진료과간에 업무가 전달되는 일이 잦기 때문이다. 진료과간의 handover가 잦은 경우, 두 부서에 해당 case를 담당하는 담당자를 새로 배치하거나, 인력을 조정할 수 있겠다.
  - 또한 두 부서간에 주로 어떤 질병에 관한 업무가 direct하게 handover되는지 파악, 환자의 진단명에 따라 다음 부서에 리소스요청을 해 환자가 원활하게 병원을 이용할 수 있도록 병원 시스템을 개선할 수 있다.

### 분석 결과
- [Youtube 발표 자료](https://www.youtube.com/watch?v=j4S5pLt1ob4&t=167s)
- [Report](/report.pdf)
