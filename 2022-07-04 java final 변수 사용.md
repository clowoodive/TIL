# 2022-07-04 java final 변수 사용

final 변수는 초기화 전에 사용하면 컴파일 에러 발생

- 메서드 내부의 final
    - 선언시, 사용하기 전 초기화
- 객체 멤버 변수 final
    - 선언시, 생성자, 초기화 블럭으로 초기화
- static 변수
    - 선언시, static 초기화 블럭으로 초기화
    
    ```java
    class Person {
      private static final int DEFAULT_AGE;
      static {
        DEFAULT_AGE = 10;
      }
    }
    ```