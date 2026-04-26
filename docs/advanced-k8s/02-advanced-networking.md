# 02 - Networking nâng cao

## Mục tiêu
- Hiểu luồng traffic trong cluster và từ ngoài vào.
- Thiết kế network policy theo nguyên tắc least privilege.

## Kiến thức cốt lõi
- Service internals: ClusterIP, NodePort, LoadBalancer, Headless.
- Ingress vs Gateway API (khái niệm & use case).
- DNS nội bộ, service discovery, session affinity.
- NetworkPolicy ingress/egress, default deny.
- CNI nâng cao (Calico/Cilium) và observability mạng.

## Lab thực hành
1. Tạo namespace `frontend`, `backend`, `data`.
2. Áp dụng default deny toàn cluster theo namespace mẫu.
3. Mở đúng luồng: frontend → backend (HTTP), backend → data (TCP).
4. Kiểm tra bằng `kubectl exec` + `curl`/`nc`.

## Lệnh quan trọng & khi nào dùng
- `kubectl get svc,ep,endpointslice -n <ns>`: dùng khi service không route đúng để đối chiếu selector và endpoint.
- `kubectl describe svc <name> -n <ns>`: dùng khi nghi mismatch port/targetPort.
- `kubectl get networkpolicy -n <ns>`: dùng khi nghi traffic bị chặn do policy.
- `kubectl exec -it <pod> -n <ns> -- curl http://<svc>:<port>`: dùng để test luồng L7 giữa các pod.
- `kubectl exec -it <pod> -n <ns> -- nc -vz <svc> <port>`: dùng để test nhanh kết nối TCP.

## Tiêu chí hoàn thành
- Mọi kết nối không khai báo đều bị chặn.
- Có sơ đồ traffic giữa các service quan trọng.
