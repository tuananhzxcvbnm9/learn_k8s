# 08 - Production Operations

## Mục tiêu
- Nâng năng lực vận hành thực chiến trong môi trường production.
- Chuẩn hóa quy trình incident response và capacity planning.

## Kiến thức cốt lõi
- Incident management: detect, triage, mitigate, postmortem.
- Sự cố thường gặp: CrashLoopBackOff, OOMKilled, pending pods, network partition.
- Cost optimization: requests right-sizing, spot/preemptible strategy.
- Multi-cluster, multi-region, disaster recovery.
- Nâng cấp cluster và workload không gián đoạn.

## Lab thực hành
1. Diễn tập incident: tăng latency đột biến.
2. Viết timeline xử lý và quyết định kỹ thuật đã chọn.
3. Làm postmortem theo template (impact, root cause, action items).
4. Lập kế hoạch nâng cấp cluster theo từng phase.

## Lệnh quan trọng & khi nào dùng
- `kubectl get pods -A --field-selector=status.phase!=Running`: dùng khi cần quét nhanh pod bất thường toàn cluster.
- `kubectl describe pod <pod> -n <ns>`: dùng để xác định OOMKilled, probe fail, image pull lỗi.
- `kubectl get events -A --sort-by=.lastTimestamp`: dùng trong giai đoạn triage để dựng timeline.
- `kubectl cordon <node>`: dùng khi cần ngăn scheduler đặt pod mới lên node nghi lỗi.
- `kubectl uncordon <node>`: dùng sau khi xử lý xong để trả node về trạng thái phục vụ.

## Tiêu chí hoàn thành
- Có runbook cho ít nhất 5 loại sự cố phổ biến.
- Có checklist nâng cấp và rollback đã được rehearsal.
