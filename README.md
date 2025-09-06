## BMaD x opencode Integration

Hệ thống này ánh xạ phương pháp BMaD (đang lưu trong `.bmad-core` và `.claude`) sang định dạng `agents/` và `commands/` của opencode để bạn có thể chạy quy trình thông qua các lệnh chuẩn và các sub‑agent chuyên trách.

### Cấu trúc

- `agents/`: Định nghĩa các agent BMaD (orchestrator, dev, qa, analyst, …)
- `commands/`: Nhiệm vụ (task) chính của BMaD khả dụng như command
- `rule/config.md`: Quy tắc ngôn ngữ (trao đổi với người dùng bằng tiếng Việt)
- `.bmad-core/`, `.claude/`: Nguồn logic gốc và tài liệu hỗ trợ

### Cách dùng nhanh

- Chạy một command (ví dụ tạo story tiếp theo): chọn command `create-next-story` trong opencode và thực thi. Command này mặc định dùng agent `bmad-orchestrator` để điều phối.
- Review story: dùng command `review-story` (agent `qa`) – có quyền refactor và cập nhật kết quả vào phần “QA Results”.
- Thực thi checklist: dùng `execute-checklist` (agent `bmad-master`) để chạy checklist trong `.bmad-core/checklists`.
- Tạo tài liệu từ template: dùng `create-doc` (agent `analyst`) – workflow có elicitation (bắt buộc dạng lựa chọn 1–9).

### Ghi chú quan trọng

- Nhiều command/agent sẽ tham chiếu file trong `.bmad-core`/`.claude`. Các agent đã bật `tools.edit: true` (và với `dev`, `qa` bật cả `bash: true`) để có thể đọc/chỉnh sửa tệp khi cần.
- Tránh “tắt tắt bước”: các command BMaD thường có checkpoint/elicitation. Hãy làm tuần tự và đợi phản hồi người dùng khi có yêu cầu.
- Có thể điều chỉnh model trong frontmatter nếu bạn muốn dùng provider khác.

### Tham khảo

- Docs opencode: https://opencode.ai/docs/agents/ và https://opencode.ai/docs/commands/
- Ví dụ: `opencode-agent-example.md`, `opencode-command-example.md`

