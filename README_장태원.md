# 09_pjt

## 주제 : <Vue를 활용한 SPA구성>


## 팀원 : 이명인,장태원,황수아

## 기능

-router link를 활용하여 SPA 구성하기
-api키를 통해 최고 평점 영화 받아 오기
-최고 평점 영화중 랜덤으로 영화 한개 출력하기
-보고싶은 영화를 등록하고 삭제할 수 있는 페이지 만들기

페이지 구성
Movie/ Random /Random 세개의 View페이지로 이루어져 있음.
App.vue페이지에 세개의 링크를 연결하여 각 각 
전체 영화 목록,
전체 영화 출력,
영화 검색 페이지
를 출력할 수 있도록 한다,

## 페이지별 기능

Movie

부트스트랩의 card를 활용해 세개씩 영화를 출력함
-부트스트랩의 그리드 시스템을 활용하여 반응형으로 
영화를 출력할 수 있도록 하였음

Random

-버튼을 누르면 날씨정보를 받아오고 날씨정보에 따라 최고 평점 영화중 하나를 랜덤으로 출력할수 있게 했음.
넘겨 받은 영화 데이터들 중 첫번째 데이터를 출력하도록 함

날씨정보를 받아서 날씨가 맑을때와/ 구름이 낀 날 /그리고 이외의 날로 분류하여  
날씨가 맑을때는 액션영화를 
구름이 낀날은 드라마를 추천할 수 있는 
recommendMovieBasedOnWeather 함수를 만들었습니다.


## WatchList
-WatchList를 클릭하면 보고 싶은 영화를 입력할 수 있는 출력창을 띄움
-보고 싶은 영화를 입력하고 add버튼을 누르면 
-삭제버튼을 누르면 줄을 그어 삭제표시를 해줌
-텍스트를 자르는 기능을 수행하는  truncate 메서드 만듬

## truncate의 로직

truncate 메서드는 주어진 텍스트를 제한된 길이로 자르고, 필요한 경우 "..."을 추가하여 반환합니다.
text와 limit 두 개의 매개변수를 받습니다.
만약 text의 길이가 limit의 30배보다 크다면, text를 limit의 30배 길이까지 자르고 "..."을 추가하여 반환합니다.

## 프로젝트에서 얻은 교훈 및 개선점

이 프로젝트를 통해 팀원들과 협업하는 경험을 했습니다. 각자의 역할을 분담하고 서로의 의견을 조율하여 프로젝트를 진행하는 과정에서 효과적인 협업 방법을 배웠습니다. 코드 리뷰를 통해 서로의 코드를 검토하고 피드백을 주고받는 과정에서 개선점을 찾고 발전시킬 수 있었습니다.

프로젝트를 진행하면서 발생한 문제들을 해결하면서 문제 해결능력과 디버깅 스킬을 향상시킬 수 있었습니다. 오류 메시지를 분석하고 로그를 확인하여 원인을 파악하고 수정하는 과정에서 실력이 향상되었습니다.

Vue.js를 사용하여 SPA를 구성하고 Vue Router를 활용한 네비게이션을 구현하는 경험을 했습니다. 이를 통해 단일 페이지 애플리케이션의 장점과 동작 원리를 이해할 수 있었습니다.

API 통신을 통해 영화 데이터를 받아오고, 받아온 데이터를 활용하여 동적으로 화면에 출력하는 경험을 했습니다. API 통신을 통해 외부 데이터를 가져오는 방법과 데이터를 가공하여 화면에 표시하는 방법을 익힐 수 있었습니다.

Vue 컴포넌트 간의 통신 방식인 props와 이벤트를 활용하여 데이터를 전달하고 상호작용하는 방법을 배웠습니다. 컴포넌트 간의 데이터 흐름을 관리하고 컴포넌트의 재사용성을 높일 수 있었습니다.

프로젝트를 통해 Vue와 관련된 다양한 기능과 개념들을 학습하고 적용해보는 경험을 했습니다. 이를 통해 Vue에 대한 이해도와 활용 능력이 향상되었습니다.