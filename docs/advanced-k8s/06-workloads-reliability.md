# 06 - Workload Patterns & Reliability

## Mục tiêu
- Tăng độ tin cậy khi triển khai và vận hành.
- Giảm downtime khi rollout.

## Kiến thức cốt lõi
- Readiness/Liveness/Startup probes đúng ngữ cảnh.
- HPA/VPA/Cluster Autoscaler và trade-offs.
- PodDisruptionBudget, graceful termination.
- Chiến lược rollout: rolling, blue/green, canary.
- Batch workloads: Job/CronJob và retry strategy.

## Lab thực hành
1. Thêm probes chuẩn cho API service.
2. Tạo HPA theo CPU và custom metrics.
3. Áp dụng PDB cho workload critical.
4. Thực hiện canary rollout với phân tách traffic.

## Lệnh quan trọng & khi nào dùng
- `kubectl rollout status deploy/<name> -n <ns>`: dùng để theo dõi rollout và phát hiện treo rollout sớm.
- `kubectl rollout history deploy/<name> -n <ns>`: dùng để kiểm tra revision trước khi rollback.
- `kubectl rollout undo deploy/<name> -n <ns>`: dùng khi phiên bản mới lỗi cần quay lại nhanh.
- `kubectl get hpa -n <ns>`: dùng khi xác minh autoscaling có hoạt động đúng ngưỡng.
- `kubectl describe pdb <name> -n <ns>`: dùng trước khi drain node để tránh vi phạm availability.

## Tiêu chí hoàn thành
- Rollout lỗi có thể rollback nhanh và an toàn.
- Khi drain node, dịch vụ vẫn đảm bảo availability mục tiêu.
