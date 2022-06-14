# 2022-06-14 GCP VM Instance received bytes
GCP 모니터링에서 VM Instance의 received bytes(MAX)가 600MiB 이상 튀는 경우는 집계 단위가 1분이어서 1초간 10MiB 수신 했을 때 10x60초=600MiB로 표시되는 것으로 추측됨.

근거는 

3분 단위, 5분 단위로 늘렸을 때 600MiB를 유지하면서 3분, 5분으로 그래프가 늘어나는 점.

그리고 다른 시간대에 튀는 그래프도 대시보드의 VM Instances 에서 보면 1초에 해당하는 수치로

“VM/외부/Google에서 수신됨” 항목과 “네트워크 트래픽 합계 항목”에서 확인 됨.