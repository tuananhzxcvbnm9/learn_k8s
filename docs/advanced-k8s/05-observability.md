# 05 - Observability

## Mục tiêu
- Quan sát hệ thống đầy đủ metrics, logs, traces.
- Xây được cảnh báo sát ngữ cảnh vận hành.

## Kiến thức cốt lõi
- Golden signals: latency, traffic, errors, saturation.
- Metrics stack: Prometheus + Alertmanager + Grafana.
- Logs pipeline: Fluent Bit/Vector + Loki/ELK.
- Tracing: OpenTelemetry + Jaeger/Tempo.
- SLI/SLO và error budget.

## Lab thực hành
1. Instrument một service với OpenTelemetry.
2. Tạo dashboard cho CPU/memory/restart/p95 latency.
3. Định nghĩa cảnh báo cho crashloop và high error rate.
4. Viết runbook cho 2 alert quan trọng.

## Lệnh quan trọng & khi nào dùng
- `kubectl top pod -A --sort-by=cpu`: dùng khi truy vết nhanh pod gây tải CPU cao.
- `kubectl logs <pod> -n <ns> --since=10m`: dùng khi cần log gần thời điểm alert.
- `kubectl logs <pod> -n <ns> -c <container>`: dùng khi pod có nhiều container.
- `kubectl port-forward svc/<svc> 9090:9090 -n monitoring`: dùng để truy cập Prometheus cục bộ khi chưa public endpoint.
- `kubectl get events -A --sort-by=.lastTimestamp`: dùng để ghép timeline sự cố cùng metrics/logs.

## Tiêu chí hoàn thành
- Alert có ngưỡng rõ ràng, giảm false positive.
- Truy được request xuyên qua nhiều service.
