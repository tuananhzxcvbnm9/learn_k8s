# 01 - Kubernetes Architecture & Scheduling

## Mục tiêu
- Hiểu sâu control plane, kubelet, kube-proxy, CNI/CSI.
- Nắm cơ chế scheduler và cách ảnh hưởng tới placement workload.

## Kiến thức cốt lõi
- Scheduling cycle: filter → score → bind.
- `requests/limits`, QoS classes, eviction.
- `taints/tolerations`, `nodeSelector`, `nodeAffinity`, `podAffinity/antiAffinity`, `topologySpreadConstraints`.
- PriorityClass và preemption.

## Lab thực hành
1. Tạo 3 nhóm node (general, cpu-optimized, stateful).
2. Deploy 3 workload với affinity khác nhau.
3. Mô phỏng pressure (CPU/memory) để quan sát eviction.
4. Áp dụng `topologySpreadConstraints` để tăng HA.

## Lệnh quan trọng & khi nào dùng
- `kubectl get nodes -o wide`: dùng khi cần xem nhanh node nào sẵn sàng và zone/instance đang chạy.
- `kubectl describe pod <pod>`: dùng khi pod Pending/Failed để đọc scheduler events và nguyên nhân.
- `kubectl top node` / `kubectl top pod`: dùng khi cần kiểm tra pressure tài nguyên trước khi chỉnh requests/limits.
- `kubectl get pod -o custom-columns=NAME:.metadata.name,NODE:.spec.nodeName`: dùng để kiểm tra pod đã được schedule vào node nào.
- `kubectl drain <node> --ignore-daemonsets`: dùng khi bảo trì node, kết hợp quan sát PDB/eviction.

## Tiêu chí hoàn thành
- Giải thích được vì sao pod được schedule vào node cụ thể.
- Chứng minh được anti-affinity giảm rủi ro single point of failure.
