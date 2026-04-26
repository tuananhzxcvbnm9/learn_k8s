# 04 - Security nâng cao

## Mục tiêu
- Thiết lập baseline security cho cluster production.
- Giảm blast radius khi có sự cố bảo mật.

## Kiến thức cốt lõi
- RBAC theo role tách biệt: dev/ops/security.
- ServiceAccount và workload identity.
- Pod Security Standards (restricted profile).
- Secret management: External Secrets/CSI Secret Store.
- Image security: scan, sign, verify (Sigstore/Cosign).
- Admission control (OPA Gatekeeper/Kyverno).

## Lab thực hành
1. Viết RBAC chỉ cho phép team dev thao tác trong 1 namespace.
2. Bật policy cấm container chạy `privileged` và `root`.
3. Chặn image không có signature.
4. Audit các quyền cluster-admin hiện có.

## Lệnh quan trọng & khi nào dùng
- `kubectl auth can-i <verb> <resource> --as=<user> -n <ns>`: dùng để kiểm tra nhanh quyền RBAC trước khi cấp thêm role.
- `kubectl get role,rolebinding -n <ns>`: dùng để audit quyền trong namespace.
- `kubectl get clusterrole,clusterrolebinding`: dùng khi rà soát quyền cấp cluster.
- `kubectl get pod <pod> -o yaml -n <ns>`: dùng để kiểm tra `securityContext`, serviceAccount, và policy liên quan.
- `kubectl describe <policy-resource> <name>`: dùng khi policy engine từ chối pod để đọc lý do chi tiết.

## Tiêu chí hoàn thành
- Không còn quyền thừa trên namespace mục tiêu.
- Pod vi phạm policy bị từ chối tạo.
