# 2023-02-22 AWS Aurora MySQL 마이너 버전 업그레이드(2.10.2 → 2.11.1)

- MySQL 5.7을 유지하면서 업그레이드 가능한 엔진(클러스터 수정)
    - Aurora MySQL 2.11.0
    - Aurora MySQL 2.11.1(default)
- 글로벌 데이터베이스의 쓰기전달 옵션을 사용하는 경우 보조 클러스터 먼저 업그레이드 - 해당없음.
- 2.11.1 버전 이후가 노출되지 않으므로 다음 지원 종료에 따른 업그레이드 시 메이저 버전 업그레이드 해야 할 가능성이 높음.
- 2.11 버전부터 새로운 운영체제 사용 가능
    - 약 10분 소요.
    - 인스턴스의 maintenance → Pending maintenance 확인.
    - 마이너 버전 업그레이드 후 점검 시간 고려해서 적용 검토.

- [https://docs.aws.amazon.com/AmazonRDS/latest/AuroraMySQLReleaseNotes/AuroraMySQL.Updates.2110.html](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraMySQLReleaseNotes/AuroraMySQL.Updates.2110.html)
- [https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Updates.Patching.html](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/AuroraMySQL.Updates.Patching.html)
- [https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_UpgradeDBInstance.Maintenance.html#OS_Updates](https://docs.aws.amazon.com/AmazonRDS/latest/AuroraUserGuide/USER_UpgradeDBInstance.Maintenance.html#OS_Updates)