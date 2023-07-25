# Rest란

#### HTTP 통신에서 어떤 자원에 대한 CRUD 요청을 URL과 Method로 표현하여 특정한 형태로 전달하는 방식

1. CRUD 연산에 대한 요청을 할 때, 요청을 위한 URL과 Method, 자원의 형태(JSON)을 사용하면 이를 REST라고 한다.

    => 이러한 규칙을 지켜 설계된 API를 RestAPI 혹은 Restful API라고 한다.


<br>

## 일반 JSON API와 REST API의 비교
* 일반 API는 전송방식에 상관 없이 개별적인 URL로 CRUD를 구분한다(즉, URL 주소가 같을 수 없음)
* Restful API는 하나의 URL에 HTTP 전송 방식으로 CRUD를 구분한다.(즉, URL 주소가 같아도 접속 방식이 다르다면 사용 가능하다.)

=> HTML과 웹 브라우저의 경우 POST, GET방식만을 지원하기 때문에 Restful은 스마트폰과 같은 웹 이외의 프로그램에 주로 사용

=> Ajax를 사용할 경우 PUT, DELETE 방식을 추가로 정의하여 개발 가능


<br>

## Restful API 역할
=> Restful의 경우 구성해야할 UI에 필요한 데이터를 제공하거나, CRUD의 요청을 수행한 결과만을 알려주기 때문에 직접 UI를 갖고 있는 페이지가 필요한 경우는 적다.


## 내가 사용한 Restful API 방법
1. Controller의 리턴 타입을 Map으로 설정한다.

    * Spring의 "@RestController" 어노테이션은 Map 객체를 리턴하면 알아서 Json으로 생성한다.

2. Webapp 폴더에 직접 html로 view를 작성한다.(WEB-INF 안에 존재하는 파일의 경우 URL 노출이 불가능 하기 때문이다.)

    * 자바스크립트로 작성한다.(Json이 javascript가 갖고 있는 문법 중 하나이기 때문이다.)


* 하나의 도메인에 대해서 CRUD를 수행할 수 있도록 만든 컨트롤러(Restful)

* 개발자가 호출할 수 있도록 만들어진 메서드(함수)들의 모음(API) 

=> 즉, CRUD 메서드를 수행할 수 있도록 만들어진 메서드들의 모음 컨트롤러를 Restful API라 부른다.