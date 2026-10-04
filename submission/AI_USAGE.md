# Khai báo sử dụng AI

Công cụ: **Claude Code** (Anthropic), dùng trong VS Code.

Phạm vi:

- Chạy các lệnh kiểm tra (smoke, pytest, run_all) và thực thi 8 notebook bằng `jupyter nbconvert --execute`.
- Viết thêm 2 cell bằng chứng (NB1: in commit JSON + kiểm tra version sau bad write; NB4: kiểm tra đầy đủ điều kiện Gold).
- Soạn nháp các Markdown cell "Giải thích kết quả", `INFO.md`, `REFLECTION.md` dựa trên **output thật** của notebook.
- Viết script render output của các cell chính thành ảnh PNG trong `screenshots/`.

Không có số liệu nào được sửa tay hoặc bịa; mọi số trong phần giải thích lấy từ output đã lưu trong notebook.
Mã nguồn notebook (`notebooks/*.py`), scripts và tests của đề bài không bị thay đổi.
Tôi đã đọc lại, đối chiếu từng số với output và chịu trách nhiệm về nội dung giải thích.
