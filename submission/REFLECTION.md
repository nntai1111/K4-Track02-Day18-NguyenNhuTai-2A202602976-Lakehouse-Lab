# Reflection — Anti-pattern: Small files (streaming ghi quá vụn)

Hệ thống tôi quan tâm là log LLM observability: mỗi request sinh một event, ingest gần real-time.
Writer streaming commit vài giây một lần nên dễ vướng nhất anti-pattern **small files**.

Lab đo rõ cái giá: NB6 với 200 commit tạo 200 file trung bình 51.5 KB (mục tiêu production 128–512 MB),
log 200 JSON phải replay. NB5 cho thấy metadata lớn gấp ~2.8 lần data khi file quá nhỏ — bị phạt hai lần.
NB2: 200 file nhỏ, query một user mất 135 ms; sau compaction + Z-order còn 55 file, 14.9 ms,
chỉ mở 1/55 file.

Phòng tránh:
1. Tăng trigger interval / micro-batch ở writer thay vì dựa vào dọn dẹp sau.
2. Lên lịch compaction + clustering theo cột hay lọc (`model`, `user_id`), kèm checkpoint.
3. Ghép expiry/vacuum với orphan sweep, vì NB6 cho thấy expiry một mình không giảm bytes.
4. Theo dõi metric "số file / partition" và "kích thước file trung bình" như một SLO.

Sử dụng AI: xem [AI_USAGE.md](AI_USAGE.md).
