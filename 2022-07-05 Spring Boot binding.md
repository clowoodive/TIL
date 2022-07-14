# 2022-07-05 Spring Boot binding

Externalized Configuration에서 본 내용으로 다른 곳에서도 동일하게 @DefaultValue("val")를 사용해서 파라미터의 기본 값 바인딩 가능.
argument가 null이어서 바인딩 된 파라미터가 null이 되는 것을 피하고 싶으면 @DefaultValue 만 사용하면 됨.
단 컴파일러에 의한 default 값은 좋은 프로그래밍 방식이 아니므로 정말 필요할 때만 사용할 것!
@ConfigurationProperties와 함께 Optional을 사용하는 것은 비추천 되는데, 특히 Optional property로 선언한 필드가 값이 없을 경우 다른 property들과 일관성을 위해 Optional이 아니라 null이 바인딩 된다.