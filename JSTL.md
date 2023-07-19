# JSTL란

* ### JSP Standard Tag Library
    -> JSP 표준 태그 라이브러리

    -> HTML 태그와 비슷한 문법을 통해 Java의 프로그래밍적 문법, 변수, 객체 등에 접근할 수 있는 기능을 제공한다.

    -> MVC 패턴의 View에서 사용할 경우 JSP 파일에서 Java 문법을 완전히 제거할 수 있다.(Java 문법에 존재하는 반복문, 조건문 등이 모두 존재함.)


* ### JSP 사용 방법

    -> 기본 문법 구성
    ```java
    <%@ taglib prefix="c" uri="http://java.sun.com/jsp/jstl/core" %>
    ```
    -> 확장 함수 지원
    ```java
    <%@ taglib prefix="fn" uri="http://java.sun.com/jsp/jstl/functions" %>
    ```
    -> 포멧터 지원
    ```java
    <%@ taglib prefix="fmt" uri="http://java.sun.com/jsp/jstl/fmt" %>
    ```