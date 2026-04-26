# 07 - GitOps & Delivery

## Mục tiêu
- Chuẩn hóa triển khai bằng GitOps.
- Tăng tính kiểm soát và khả năng audit thay đổi.

## Kiến thức cốt lõi
- Mô hình GitOps với Argo CD hoặc Flux.
- Cấu trúc repo: app-of-apps, environment overlays.
- Helm/Kustomize strategy.
- Progressive delivery (Argo Rollouts/Flagger).
- Chính sách promotion dev → staging → prod.

## Lab thực hành
1. Tạo repo manifests theo môi trường.
2. Đồng bộ cluster bằng Argo CD/Flux.
3. Thiết lập chính sách approve trước khi lên prod.
4. Thử drift ngoài cluster và xác nhận tự reconcile.

## Lệnh quan trọng & khi nào dùng
- `kubectl apply -k <path>`: dùng khi kiểm tra nhanh overlay Kustomize trước khi push Git.
- `kubectl diff -k <path>`: dùng để xem thay đổi dự kiến trước khi apply.
- `helm template <release> <chart>`: dùng để render manifest và review policy/label trước deploy.
- `kubectl get applications -n argocd` (nếu dùng Argo CD): dùng để xem trạng thái sync/health.
- `kubectl describe application <app> -n argocd`: dùng khi app OutOfSync/Degraded để đọc nguyên nhân.

## Tiêu chí hoàn thành
- Có lịch sử thay đổi rõ ràng, rollback theo commit.
- Drift được phát hiện và khôi phục tự động.
