# GET방식
    
#### -> URL에 변수의 이름과 값을 포함시키는 HTTP GET 방식의 데이터 전송
#### -> 주로 데이터를 읽거나 검색할 때 사용되는 메소드(수정할 때는 사용하지 않는다.)
    
* 웹 페이지가 이동되는 과정(예; 링크 클릭)에서 변수 값이나 사용자의 입력값을 다른 페이지에서도 인식할 수 있도록 하는 처리 기법

* 사용방법
    
    * 페이지의 URL 뒤에 "?"를 명시하고, "변수이름=값"의 형태로 데이터를 추가한다.
    * 두 개 이상의 값을 포함시켜야할 경우 "&"로 구분할 수 있다.

    <hr>
    
    **페이지URL?변수명=값&변수명=값&...&변수명=값**

    <hr>

    * 사용 예시
        
        * https://comic.naver.com/webtoon?tab=mon
        * 네이버 웹툰의 경우 요일별 만화를 Get방식을 사용하여 tab="날짜"로 페이지가 이동되도록 하고 있다.
        * 위와 같이 하나의 웹페이지에 변수 값만 다르게 전송하도록 링크를 걸어둔다면 하나의 웹 페이지가 여러 웹 페이지처럼 보이는 효과를 나타낼 수 있다. 
        * 이를 통해 요일별로 웹 페이지를 모두 만드는 비효율적인 작업을 줄일 수 있다.

    * 단점

        * GET방식 파라미터의 경우 변수 이름, 값이 URL에 그대로 노출되기 때문에 사용자가 임의로 내용 변경 및 삭제가 가능하다.

        * JSP 페이지는 변수의 내용이 잘못 전달되 경우를 대비하여 프로그램의 오작동을 방지해야 한다.
            
            -> 예외상황
            
            1. NULL인 경우 (파라미터 변수 이름이 명시되지 않는 경우)
                
                -> 예; https://comic.naver.com/webtoon
            
            2. ""(공백)인 경우 (파라미터 이름만 있고, 값이 명시되지 않는 경우)

                -> 예; https://comic.naver.com/webtoon?tab=

<br>
<br>

# POST 방식

#### -> html의 **"form"** 요소를 통해 사용자의 입력 값을 전달하도록 하는 방식
#### -> 데이터를 새로 생성할 때 주로 사용한다.

```html
<form>태그의 methdo 속성에서 POST 방식임을 명시하고, action 속성에서 입력값을 전송받을 JSP페이지를 지정한다.

<input>태그의 name 속성값이 입력값을 받는 JSP 페이지에게넌 POST 파라미터의 이름이 된다.

예;

login.jsp 
    <form name="login" method="post" action="loginOK.jsp">
        <fieldset>
            <input type="text" name="user_id" />
            <input type="password" name="user_pw" />
            <input type="submit" />
        </fieldset>
    </form>

loginOK.jsp
    <%
        request.setCharacterEncoding("UTF-8");
        String user_id = request.getParameter("user_id");
        String user_pw = request.getParameter("user_pw");        
    %>
```

#### -> 단일 입력값의 경우는 String 타입으로 전송되지만, 체크박스와 같이 name 속성이 동일 요소가 여러개 존재하는 경우 String 배열로 전송된다.

```html
-> HTML의 name속성에서는 배열임을 JSP에게 알리기 위해 "[]"를 표기한다.

hobby.jsp
    <form name="hobby" method="post" action="hobbyOK.jsp">
        <input type="checkbox" name="hobby[]" value="운동" />
        <input type="checkbox" name="hobby[]" value="독서" />
        <input type="checkbox" name="hobby[]" value="음악감상" />
    </form>

hobbyOK.jsp
    <%
        String hobby[] = request.getParameterValues("hobby[]");
    %>
```

### GET 방식 VS POST 방식

* FrontEnd 측면
    * 전송 방식:
        
        #### GET : 모든 데이터가 URL에 노출, 보안이 필요한 경우 사용 불가

        #### POST : HTML의 FORM 요소를 통해 데이터를 전달, URL에 데이터가 노출되지 않음

    * 사용 용도:

        #### GET : 목록에서 상세페이지로 이동시, 링크를 통한 데이터 전송시 사용

        #### POST : 회원가입, 로그인등 사용자가 입력한 값을 저장/수정하기 위한 데이터 전송시 사용

* BackEnd 측면

    #### -> 화면에서 전송된 값을 수신하기 위한 데이터 처리방식에서 Get방식과 Post방식에서 차이는 없다.

<br>
<br>

# PUT 방식
#### -> 데이터를 새로 생성 혹은 수정할 때 주로 사용한다.

<br>

### POST 방식 VS PUT 방식
* POST 방식의 경우 데이터가 들어올 때마다 새로운 데이터를 생성하지만, PUT은 사용자가 데이터를 지정하고 수정하기 때문에 같은 요청이 반복되더라도 같은 데이터가 추가적으로 계속 생성되지는 않는다.

<br>
<br>

# DELETE 방식
#### -> 지정된 데이터 삭제시에만 사용한다.

<br>
<br>

# CRUD(Create Read Upadate Delete)

#### 정의
    -> 대부분의 컴퓨터 소프트웨어가 가지는 기본적인 데이터처리 기능인 Create(생성), Read(읽기), Update(갱신),Delete(삭제)를 묶어서 일컫는 말. (출처: 위키 백과)

|이름|조작|HTTP Method|SQL문|
|------|---|---|---|
|Create|생성|POST|INSERT|
|Read|읽기 |GET|SELECT|
|UPDATE|갱신|PUT|UPDATE|
|DELETE|삭제|DELETE|DELETE|
