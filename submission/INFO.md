# Thông tin bài nộp

| Mục | Giá trị |
|---|---|
| Họ tên | Nguyễn Như Tài |
| MSSV | 2A202602976 |
| Repo | `K4-Track02-Day18-NguyenNhuTai-2A202602976-Lakehouse-Lab` |
| Mã bài | K4-Track02-Day18 — Data Lakehouse Architecture |
| Đường chạy | **Lightweight** cho cả 8 notebook (`deltalake` 1.6.6 + `pyiceberg` + DuckDB + Polars); NB1–NB4 **không** dùng Spark |
| Python | 3.13.15 (venv `.venv`) |
| Hệ điều hành | Windows 11 Home Single Language (10.0.26300), PowerShell / Git Bash |

## Kết quả kiểm tra (chạy ngày 04/10/2026)

| Lệnh (PowerShell-equivalent trong README) | Kết quả |
|---|---|
| `scripts/verify_lite.py` (smoke) | 9/9 PASS |
| `python -m pytest` | 24/24 PASS |
| `scripts/run_all.py` | 8/8 notebook PASS (~25 s) |

`PYTHONUTF8=1` được đặt khi chạy để tránh lỗi encoding Unicode trên console Windows.

## Nội dung bài nộp

- `notebooks/` — 8 notebook `.ipynb` đã thực thi (`jupyter nbconvert --execute`), giữ nguyên output.
  Cuối mỗi notebook có Markdown cell **"Giải thích kết quả"**.
  NB1 có thêm cell in nội dung commit JSON và xác nhận bad write không tạo version mới;
  NB4 có thêm cell kiểm tra đầy đủ điều kiện Gold (p50 ≤ p95, cost > 0, error_rate ∈ [0,1], 3 model/ngày).
  Các file nguồn `notebooks/*.py` không bị sửa.
- `screenshots/` — 1 ảnh/notebook (`nb01_delta_log.png` … `nb08_agents.png`), render từ output thật của các cell chính
  trong notebook đã thực thi.
- `REFLECTION.md` — reflection ≤ 200 từ.
- `AI_USAGE.md` — khai báo phạm vi sử dụng AI.
