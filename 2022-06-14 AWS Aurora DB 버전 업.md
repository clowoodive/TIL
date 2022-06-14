# 2022-06-14 AWS Aurora DB 버전 업
AWS Aurora DB(1.버전대 MySQL 5.6)가 2023년에 지원 종료 예정이어서 2.버전대 MySQL 5.7로 버전업 검토.

변경해서 사용하던 파라미터그룹, 클러스터파라미터그룹이 5.7에 그대로 적용 가능한지 확인되어 미리 파라미터 그룹 만들어 놓음.

MySQL 5.7에서도 performance_schema 사용 가능한 것으로 확인되어 파라미터그룹, 클러스터파라미터그룹 세팅 함.

5.7부터는 성능개선 도우미(Performance Insights)라는 서비스로 DB performace_schema 내용을 볼수 있게 해줌.