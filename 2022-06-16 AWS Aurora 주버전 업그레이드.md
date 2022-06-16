# 2022-06-16 AWS Aurora 주버전 업그레이드

5.6.mysql_aurora.1.22.4 → 5.7.mysql_aurora.2.10.2

Aurora MySQL 주버전 업그레이드 시 완료 후 재부팅 해야 파라미터 그룹, 클러스터 파라미터 그룹이 적용 됨.

업그레이드 실패 한 db instance는 로그 및 이벤트 항목에서 로그를 보고 원인 파악.

아래 원인으로 추측되므로 스냅샷으로 5.7 인스턴스 만들어서 성공하는지 확인함.

```java
[ERROR] Can't open shared library '/rdsdbbin/oscar-5.7.mysql_aurora.2.10.2.0.4.0/lib/plugin/aws_auth.so' (errno: 0 /rdsdbbin/oscar-5.7.mysql_aurora.2.10.2.0.4.0/lib/plugin/aws_auth.so: cannot open shared object file: No such file or directory)
[ERROR] Can't open plugin library: /rdsdbbin/oscar-5.7.mysql_aurora.2.10.2.0.4.0/lib/plugin/aws_auth.so: cannot open shared object file: No such file or directory
[Warning] Couldn't load plugin named 'AWSAuthenticationPlugin' with soname 'aws_auth.so'.
```

Cloud Trail 서비스로 당시 이벤트 확인했으나 정상 업그레이드 되는 db와 실패한 db 내용이 같음.