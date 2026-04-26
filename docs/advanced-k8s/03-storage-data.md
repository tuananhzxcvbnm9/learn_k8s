# 03 - Storage & Data

## Mục tiêu
- Vận hành workload stateful an toàn.
- Chọn đúng chiến lược lưu trữ theo RPO/RTO.

## Kiến thức cốt lõi
- PV/PVC/StorageClass, dynamic provisioning.
- StatefulSet, volumeClaimTemplates.
- Access modes (RWO, RWX) và giới hạn thực tế.
- Backup/restore (Velero hoặc giải pháp cloud-native).
- Data migration và rolling update cho workload stateful.

## Lab thực hành
1. Deploy PostgreSQL bằng StatefulSet + PVC.
2. Thử pod reschedule và xác nhận dữ liệu còn nguyên.
3. Thực hiện backup và restore vào namespace khác.
4. Thực hiện upgrade phiên bản có kiểm thử dữ liệu.

## Lệnh quan trọng & khi nào dùng
- `kubectl get pv,pvc -A`: dùng khi cần xác nhận trạng thái bind của volume toàn cluster.
- `kubectl describe pvc <name> -n <ns>`: dùng khi PVC Pending để xem lỗi provisioner/storageclass.
- `kubectl get storageclass`: dùng khi chọn class mặc định hoặc class theo workload.
- `kubectl rollout status statefulset/<name> -n <ns>`: dùng khi nâng cấp StatefulSet để theo dõi rollout.
- `kubectl exec -it <pod> -n <ns> -- <db-client-cmd>`: dùng để kiểm tra dữ liệu trước/sau reschedule hoặc restore.

## Tiêu chí hoàn thành
- Có quy trình backup/restore đã kiểm chứng.
- Chỉ ra rủi ro khi dùng Deployment cho database.
