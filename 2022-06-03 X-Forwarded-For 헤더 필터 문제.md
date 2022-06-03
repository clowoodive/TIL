# 2022-06-03 X-Forwarded-For 헤더 필터 문제

서버 업데이트 후 특정 요청에서 허용한 ip가 아니라는 메시지가 출력되고 있었다.

사내에서만 요청 가능하게 해놓은 기능인데 X-Forwarded-For 헤더에 기록된 ip중 로드밸런서 ip를 필터하지 못해서 로드 밸런서 ip가 서버의 remoteip로 인식되고 있었다.

Spring Boot 2.4.12에서 2.5.12로 올린 것 밖에 변경사항이 없었고, 잠시 검색해 봤지만 관련된 사항이 변경 되었는지는 찾지 못했다.

application.properties 설정은 아래와 같았고

```bash
# server.forward-headers-strategy = FRAMEWORK

server.tomcat.remoteip.remote-ip-header = X-Forwarded-For
server.tomcat.internal-proxies = 35\\.111\\.222\\.33|35\\.22\\.33\\.44
```

그동안은 internal-proxies에 세팅된 ip들(로드밸런서, 결재, google ip)이 잘 필터되어 실제 remoteip로 처리되었지만 마지막에 거친 ip가 인식되는걸로 봐서는 필터가 동작하지 않았다.

검색을 좀 해보니 server.forward-headers-strategy 라는 옵션이 생긴지가 꽤 되었는데 우린 그동안 세팅하지 않았고 설명을 보면 NONE으로 동작했을 것으로 추측된다.

그리고 설명을 읽어보면 NATIVE로 세팅해야 할 것 같은데 NATIVE로 세팅 하더라도 internal-proxies의 ip들이 필터되지 않는다.

결국 strategy를 FRAMEWORK로 세팅하고 나서야 ip가 필터되어서 우선은 이렇게 서비스를 구동했다.

해당 옵션을 그동안 세팅하지 않았고, 그로인해 default로 추정되는 NONE이나 NATIVE로 동작했다면 왜 세팅 후에 동작하지 않는 것일까?

Spring Boot 버전별로 릴리즈 노트부터 다시 찾아보는걸로.

로컬 서버 띄워서 curl로 확인 방법

curl [http://127.0.0.1:8080/info](http://127.0.0.1:10025/admin/maintenance/info) -X POST -d "{}" -H "Content-type:application/json" -H "X-Forwarded-For: 1.2.3.4, 35.111.222.33"

참고 : [https://sg-choi.tistory.com/540](https://sg-choi.tistory.com/540)