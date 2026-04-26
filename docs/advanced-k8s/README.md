# Lộ trình học Kubernetes nâng cao

Bộ tài liệu này giúp bạn học Kubernetes nâng cao theo từng chủ đề, có mục tiêu rõ ràng và bài lab thực hành.

## Cách học đề xuất
1. Học theo thứ tự các module từ `01` đến `08`.
2. Mỗi module có:
   - **Mục tiêu học tập**
   - **Kiến thức cốt lõi**
   - **Lab thực hành**
   - **Tiêu chí hoàn thành**
3. Ghi chú lại các lệnh `kubectl`, manifest, và lỗi gặp phải để xây "runbook" cá nhân.

## Danh sách module
- [01 - Kubernetes Architecture & Scheduling](./01-architecture-scheduling.md)
- [02 - Networking nâng cao](./02-advanced-networking.md)
- [03 - Storage & Data](./03-storage-data.md)
- [04 - Security nâng cao](./04-security.md)
- [05 - Observability](./05-observability.md)
- [06 - Workload Patterns & Reliability](./06-workloads-reliability.md)
- [07 - GitOps & Delivery](./07-gitops-delivery.md)
- [08 - Production Operations](./08-production-operations.md)

## Lab environment gợi ý
- **Local:** kind / k3d cho bài lab nhỏ.
- **Cloud:** EKS/GKE/AKS cho bài networking, storage, IAM, autoscaling.
- **Tooling nên có:** `kubectl`, `kustomize`, `helm`, `jq`, `stern`, `k9s`.

## Mốc đánh giá năng lực
- **Level 1:** Làm được deployment production-ready với probes, requests/limits, HPA.
- **Level 2:** Tự thiết kế network policy, RBAC, và pipeline GitOps.
- **Level 3:** Xử lý được incident thực tế: quá tải, mất node, latency cao, rollout lỗi.

## Gợi ý sử dụng lệnh kubectl khi học
- Mỗi module đã bổ sung mục **Lệnh quan trọng & khi nào dùng** để bạn biết lệnh nào dùng trong tình huống nào.
- Khi lab, nên chạy theo thứ tự: `get` → `describe` → `logs/events` để khoanh vùng lỗi nhanh.
- Luôn ghi lại lệnh đã chạy và kết quả vào runbook cá nhân để tái sử dụng khi xử lý incident.
