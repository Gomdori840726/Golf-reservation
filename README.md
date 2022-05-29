# 골프장 실시간 직접 부킹 정보제공 프로그램(프로그램명 : 직골(다이렉트골프)) - 직장인이 직접 골프장 부킹한다는 의미의 뜻
> "골프장은 많은데 골프장 예약은 왜 부킹앱과 부킹 딜러를 통해서만 예약해야되는 걸까?" 내가 직접 예약하는 방법은 없을까?"
> "직접 예약하려고하니 골프장을 하나하나 방문해서 가능한 날짜에 예약이 가능한지 확인해야되니 시간도 오려걸리고 검색하다 지치는데 쉽게 예약할 수 있는 방법을 없을까?"
> "부킹앱의 딜러들이 올려놓은 골프장은 허위정보가 늘고 있고, 가격도 같은 장소, 같은 시간인데도 앱과 딜러별로 차이가 나는데 신뢰성 있는 골프장 정보는 왜 없을까?"
위 질문에서 시작한 실험 프로젝트입니다. 실제로 골프장을 검색 및 예약을하고 그 날짜의 골프장 가격과 부킹 앱들에 올라온 가격들을 찾아보고 해결 방안을 찾으려 합니다.
골퍼가 쉽게 골프장을 예약하는 골프장 부킹 정보를 제공 하는 **골프장 직접 부킹 정보제공 프로그램**을 개발하고 있습니다.

## 스크린 샷
![screenshot](https://user-images.githubusercontent.com/106417384/170849814-67f2d660-916e-491d-a1fd-e18c6f84497e.png)
골프장 직접 부킹 프로그램을 설치 한뒤 실행하면 네이버에 예약 가능한 골프장과 골프장 위치를 정보가 표시됩니다.

## 합리화                                                                                    
코로나로 인해 골프하는 골퍼들이 늘어나고 있고, 취미 생활로 시작하는 골퍼들은 골프장 라운딩을 위해 부킹앱과 매니저를 통해 예약하거나 일부의 사람들이 직접 골프장 사이트를 방문하여
예약하나 쉽지가 않습니다. 만약 전국에 있는 골프장 사이트의 남는 티업 시간을 하나의 프로그램으로 정보를 제공한다면, 골퍼들의 라운딩비 지출 감소, 손쉬운 예약에 따라 골프가 더 많이 
대중화 되지 않을까 하는 생각에서 이 골프장 직접 부킹 정보제공 프로그램을 시작하게 되었습니다. 과연 정보제공을 통해서 더 편한지, 그래서 정말로 유용한지 실험해 보도록 하겠습니다.

## 정보제공 방안들
1. 네이버의 예약 가능한 골프장 정보를 지원 : 네이버 검색창에 cc로 검색하면 전국에 있는 골프장이 나오고 네이버와 제휴되어 예약 가능한 골프장이 있으나 필터가 없어 스크롤바를 내려서  하나하나 확인해야는 불편함이 있습니다. [네이버 사이트](https://www.naver.com)
2. 기존 부킹앱들이 순수하게 골프장 정보를 제공하는 방법이 가장 확실한 방법이지만, 이는 골프장과 부킹앱 회사, 딜러들의 이익이 달려있어 쉽지 않습니다.   
3. 네이버에서 제공하는 API를 이용해서, 별도의 골프장 웹사이트 껍데기를 만들고, 내부적으로 네이버 서비스를 이용하는 방법도 생각해 보았습니다. 실현 가능성이 있다고 하더라도, 이용자가 naver.com이 아닌 별도의 URL을 치고 들어와야 한다는 제한사항이 있습니다. 
4. **골프장 직접 부킹 정보제공 프로그램** - 이 프로젝트에서 공략하고자 하는 방법입니다. 네이버 정보를 활용해, 검색창에 제시된 골프장 중 예약가능한 골프장만을 필터하는 방법입니다. 검색에 대한 수고가 매우 적게 들고, 현실성이 있습니다.
5. 몇가지 단점이 있으나 골프장 정보 제공에는 충분하다고 여겨 (4)의 방법으로 진행하겠습니다.

## 목표와 현황
* 1차 목표 - 네이버 사이트에 예약 가능한 골프장 데이터 제공

## 이용 방법
파일을 다운로드 및 설치하고 사용하시면 됩니다.
![screenshot2](https://user-images.githubusercontent.com/106417384/170850157-9f53be01-037c-4c03-8355-0be9039eaf95.png)
위 압축파일을 다운로드하여 해체 후 설치 및 실행하면 실행 창에 예약 가능한 골프장 현황이 표시되고, 해당 폴더안에 csv파일로도 자료가 생성됩니다.

## 어떻게 동작하는가?
프로그램을 실행하면, 브라우저가 로드되면서, 실시간으로 예약 가능한 네이버에 등록된 골프장을 검색하여 생성해줍니다.또 실행된 결과가 csv 파일 생성되어 csv 파일을 보면서     실시간으로 이용하고 싶은 골프장을 찾아가 예약할 수 있습니다.

```browser = webdriver.Chrome("./chromedriver", options=option)
browser.get(
    "https://map.naver.com/v5/?c=14188320.3206238,4344490.5447925,15,0,0,0,dh")
```
구체적인 코드는 조금 더 복잡하지만 아이디어 설명을 위해 간단히 적었으며, 실제 코드도 동작 원리는 같습니다. 번역하고자 하는 문구를 담고 있는 DOM 노드를 CSS 셀렉터로 찾아서, 해당 노드가 담고 있는 텍스트 노드의 문자열을 정규식으로 검사하여, 일치하는 부분을 한국어로 변환하는 일을 합니다. 다소 부정확한 방식이지만, 원하는 목적을 달성하기에는 충분하고 간단한 방법이라고 생각합니다.

## 추가 골프장 요청 방법
프로그램을 이용하던 중, 추가로 골프장 정보가 보강 되었으면 하는 부분이 있다면, [이슈](https://github.com/chosunggeun/tast/issues/new)로 등록합니다.

## 한계
네이버 사이트에 보이는 내용을 주먹구구식으로 사용하고 있기에, (1) 사용자가 원하는 모든 골프장을 찾기가 어렵습니다. (2) 프로그램 실행 값을 가지고 별도로 사용자가 다시 해당 골프장 사이트를 방문하여 예약해야하는 번거로움이 있습니다. (3) 예약 가능한 골프장 사이트를 참고하여 해당 골프장을 각각 방문하여 라운딩비용을 계산해야되는 번거로움이 있습니다.이러한 명백한 기능적 한계점들을 안고 시작하지만, 실험 목적을 달성하는 데에는 충분하리라 기대합니다.

## 프로젝트 종료 조건
다음의 조건 중 하나 이상 만족되면 프로젝트 소유자의 판단으로 종료합니다.
1. 프로젝트가 무의미하다는 결론이 난 경우
2. 프로젝트에 주도자의 의욕이 현저히 떨어진 경우

## 프로젝트 현재 상태

* [생각] 네이버에 등록된 약 250개의 골프장 중 예약 가능한 골프장만을 필터해주지만 이정도만으로도 사용자의 라운딩을 위한 준비시간, 금액 등을 감소시킬거 같습니다.
* [생각] 골프를 하는 일반 직장인들의 스트레스가 줄고, 프로를 준비하는 학생들과 학부모의 지원 비용과 부담이 감소될거 같습니다.

## 프로젝트 공동개발자
* [조성근(whtjdrms84@naver.com)] https://github.com/Chosunggun

## 참조 : 외부 오픈소스 및 참고자료
1. 과학기술대학교 비정규과목 “실무역량 향상을 위한 파이썬 기초 1~3”
  (a)실무역량 향상을 위한 파이썬 기초 1 https://eclass.seoultech.ac.kr/ilos/st/course/online_list_form.acl?WEEK_NO=1 
  (b)실무역량 향상을 위한 파이썬 기초 2 https://eclass.seoultech.ac.kr/ilos/st/course/online_list_form.acl?WEEK_NO=2
  (c)실무역량 향상을 위한 파이썬 기초 3 https://eclass.seoultech.ac.kr/ilos/st/course/online_list_form.acl?WEEK_NO=3
2. 낯코딩 [Python] Selenium을 활용한 웹 크롤링 https://velog.io/@changhtun1/Python-%EB%8F%99%EC%A0%81-%EC%9B%B9-%ED%81%AC%EB%A1%A4%EB%A7%81
3. 코딩유치원 웹 크롤링                                                                                                                                    https://codingkindergarten.tistory.com/category/%ED%8C%8C%EC%9D%B4%EC%8D%AC%20%ED%8C%A8%ED%82%A4%EC%A7%80/%EC%9B%B9%20%ED%81%AC%EB%A1%A4%EB%A7%81
4. 비전공자를 위한 파이썬 자동화 완벽 가이드 https://wikidocs.net/85737

감사합니다.
