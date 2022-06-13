# 2022-06-10 lombok을 이용한 slf4j
lombok을 통해 @Slf4j 애너테이션을 사용하는 경우 lombok.config파일의 속성들에 의해 영향을 받는데 특히 lombok.log.fieldName 구성키 값은 기본이 log인 로거 필드를 변경해 준다.
이걸 변경한 것을 잊고 컴파일 하다보면 cannot find symbol 컴파일 에러가 발생하며, 검색하면 lombok dependency, annotation processors, plugin 등 세팅의 문제가 주된 원인이기에 삽질하게 될수도 있으니 잊지말것.

