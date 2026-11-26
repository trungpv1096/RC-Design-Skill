# RC-Design-Skill

Claude Code skill **`rc-design-tcvn`**: tính toán / kiểm tra cấu kiện bê tông cốt thép **cột, dầm (tiết diện chữ nhật), sàn, đài cọc** theo
TCVN 5574:2018 (bản v3), TCVN 10304:2025 và cột kháng chấn theo TCVN 9386-1:2025.

| File | Nội dung |
|---|---|
| `rc-design-tcvn/SKILL.md` | Quy trình chung, nguồn tiêu chuẩn, quy ước đơn vị / trục ETABS |
| `rc-design-tcvn/vat-lieu.md` | Vật liệu (Bảng 7, 10, 13, 14), γb1, γb3, biến dạng, ξR |
| `rc-design-tcvn/cot.md` | Cột: L0, ea, η, mô hình phi tuyến 8.1.2.7, cắt (φn), cấu tạo, so sánh với ETABS |
| `rc-design-tcvn/dam.md` | Dầm chữ nhật: tổng hợp kết quả ETABS, uốn, cắt, xoắn 8.1.4 |
| `rc-design-tcvn/san.md` | Sàn theo dải (Strip Forces), As dải 1 m, cấu tạo bản |
| `rc-design-tcvn/khang-chan.md` | Cột kháng chấn TCVN 9386-1:2025 (DCL / DCM / DCH), cột khỏe – dầm yếu (4.29) |
| `rc-design-tcvn/dai-coc.md` | Đài cọc đơn: phản lực cọc TCVN 10304:2025, chọc thủng / cắt / uốn đài, cấu tạo |

## Cài đặt
Chép thư mục `rc-design-tcvn` vào `%USERPROFILE%\.claude\skills\` (Windows) hoặc `~/.claude/skills/`.

> Kết quả chỉ mang tính tham khảo; người ký duyệt cần kiểm tra lại trước khi sử dụng.
