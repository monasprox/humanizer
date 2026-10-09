# Humanizer

Agent skill giúp viết và trả lời tự nhiên hơn mà không biến “giống người” thành
một lớp slang, emoji, lỗi chính tả hay các câu mẫu được rải lên bề mặt.

Skill này mở rộng ý tưởng từ
[`blader/humanizer`](https://github.com/blader/humanizer) sang hội thoại có ngữ
cảnh, đặc biệt là tiếng Việt: xưng hô, quan hệ, tâm thế, diễn tiến nhiều lượt,
phương ngữ và văn phong nhắn tin.

## Điểm chính

- Đọc cả chuỗi trao đổi thay vì phản ứng máy móc với tin nhắn cuối.
- Giữ một lập trường và bản sắc nhất quán, không tự nhận mọi điều người dùng gán.
- Phân biệt câu hỏi lấy thông tin với câu hỏi dùng để trêu, thử, phản bác hoặc
  chuyển lượt.
- Chỉ hỏi lại khi câu trả lời thật sự phụ thuộc vào thông tin còn thiếu.
- Không suy ra vùng miền, tính cách hay quan hệ từ một từ địa phương hoặc một
  dấu hiệu bề mặt.
- Dùng dataset và công cụ NLP đúng vai trò; tần suất trong corpus không quyết
  định một người nên nói thế nào.
- Khi sửa văn bản, giữ nguyên dữ kiện, số liệu, trích dẫn, thuật ngữ, đường dẫn
  và mức độ chắc chắn.
- Không phục vụ mục tiêu qua mặt công cụ phát hiện AI hay giả làm một người có
  thật.

## Cấu trúc

```text
humanizer/
├── SKILL.md
├── LICENSE
├── agents/
│   └── openai.yaml
├── evals/
│   └── behavior-cases.md
└── references/
    ├── conversation-grounding.md
    ├── regional-digital-variation.md
    ├── research-basis.md
    ├── vietnamese-data-notes.md
    ├── vietnamese-register.md
    └── writing-patterns.md
```

`SKILL.md` là entrypoint. Agent chỉ cần đọc thêm reference phù hợp với loại công
việc đang làm; các ghi chú nghiên cứu không phải tài liệu phải nạp cho mọi lượt.

## Cài đặt

Repo nên được đẩy với `SKILL.md` nằm ngay ở thư mục gốc. Sau đó có thể đưa URL
repo cho EpisClaw hoặc một agent có khả năng cài skill và yêu cầu cài `humanizer`
từ repo đó.

Cài thủ công cho Codex trên Windows:

```powershell
git clone <repo-url> "$env:USERPROFILE\.codex\skills\humanizer"
```

Trên macOS hoặc Linux:

```bash
git clone <repo-url> ~/.codex/skills/humanizer
```

Không có dependency runtime hay dịch vụ bên ngoài bắt buộc.

## Cách gọi

Skill có thể được chọn tự động cho việc sửa văn phong và hội thoại, hoặc gọi rõ:

```text
Use $humanizer to rewrite this passage for its actual reader.
```

```text
Dùng $humanizer để trả lời đoạn hội thoại này theo đúng quan hệ và diễn tiến.
```

## Kiểm tra

Repo hiện có 67 ca hành vi trong `evals/behavior-cases.md`. Các ca kiểm tra quyết
định và thuộc tính đầu ra, không ép agent học thuộc một câu trả lời.

Với Codex SDK đã cài, có thể chạy validator đi kèm `skill-creator`:

```text
quick_validate.py <đường-dẫn-tới-repo>
```

Phiên bản hiện tại: **0.6.0**.

## Giấy phép

MIT. Xem [LICENSE](LICENSE).
