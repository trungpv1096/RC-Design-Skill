# Vật liệu – TCVN 5574:2018 bản v3 (trang in)

## Bê tông nặng – cường độ tính toán (Bảng 7, tr.35) và mô đun (Bảng 10, tr.38), MPa
| Cấp | Rb | Rbt | Eb |
|---|---|---|---|
| B15 | 8,5 | 0,75 | 24 000 |
| B20 | 11,5 | 0,90 | 27 500 |
| B22,5 | 13,0 | 1,00 | 29 000 ← **người dùng quy định** (Bảng 7, 10 không có B22,5; không nội suy) |
| B25 | 14,5 | 1,05 | 30 000 |
| B30 | 17,0 | 1,15 | 32 500 |
| B35 | 19,5 | 1,30 | 34 500 |
| B40 | 22,0 | 1,40 | 36 000 |
| B45 | 25,0 | 1,50 | 37 000 |
| B50 | 27,5 | 1,60 | 38 000 |
| B55 | 30,0 | 1,70 | 39 000 |
| B60 | 33,0 | 1,80 | 39 500 |

Cường độ tiêu chuẩn (Bảng 6) đã đối chiếu: B20 Rb,n = 15, B25 Rb,n = 18,5; Rbt,n = 1,35 / 1,55 MPa. Cấp khác: tra bảng.

### Hệ số điều kiện làm việc
- **γb1** (6.1.2.3a, tr.33): 1,0 khi tổ hợp gồm cả tải tạm thời ngắn hạn; **0,9** khi chỉ gồm tải thường xuyên +
  tạm thời dài hạn. Nhân cho Rb và Rbt.
- **γb3 = 0,85** (6.1.2.3c): đổ bê tông theo phương đứng, mỗi lớp đổ > 1,5 m (cột). **Chỉ nhân Rb**, áp dụng đồng thời
  với γb1. Ví dụ B25 cột: Rb = 14,5 × 0,85 = 12,33 MPa (ngắn hạn); 14,5 × 0,9 × 0,85 = 11,09 MPa (dài hạn).

### Biến dạng (dùng cho mô hình phi tuyến)
- εb0 = 0,002 (6.1.3.2); εb2 = 0,0035 (6.1.4.2, ≤ B60, ngắn hạn); biểu đồ 2 đoạn thẳng εb1,red = 0,0015 (6.1.4.3).
- Thép: biểu đồ 2 đoạn thẳng (6.2.4.2), Es = 2,0·10⁵ MPa (6.2.3.3, tr.48), εs2 = 0,025.

## Cốt thép (Bảng 13 tr.47 – Rs, Rsc; Bảng 14 tr.48 – Rsw), MPa
| Nhóm | Rs | Rsc (ngoài ngoặc) | Rsc (trong ngoặc) | Rsw |
|---|---|---|---|---|
| CB240-T | 210 | 210 | 210 | 170 |
| CB300-T | 260 | 260 | 260 | 210 |
| CB300-V | 260 | 260 | 260 | 210 |
| CB400-V | 350 | 350 | 350 | 280 |
| CB500-V | 435 | 435 | 400 | 300 |

- **Rsc** (Bảng 13 CHÚ THÍCH 1): giá trị **trong ngoặc** dùng khi tổ hợp có tải ngắn hạn; giá trị ngoài ngoặc khi
  tổ hợp dài hạn (người dùng chốt áp dụng đúng chữ: CB500-V → 400 MPa tổ hợp thường, 435 MPa tổ hợp dài hạn).
- Sàn: thép d < 10 mm thường là nhóm nhỏ (CB240-T), d ≥ 10 mm nhóm lớn (CB400-V) – theo nhập của người dùng.

## Chiều cao vùng nén giới hạn (8.1.2.2.3, (31)–(32), tr.56)
ξR = 0,8 / (1 + εs,el/εb2), εs,el = Rs/Es; αR = ξR·(1 − 0,5ξR).
Ví dụ CB400-V: εs,el = 350/2·10⁵ = 0,00175 → ξR = 0,8/(1 + 0,5) = 0,533; αR = 0,391.

## Quy đổi sang ký hiệu Eurocode (khi dùng TCVN 9386)
- C16/20: cường độ mẫu trụ 16 MPa / lập phương 20 MPa → tương đương **B20** (người dùng xác nhận).
- fcd ≈ Rb (đã nhân γb3), fyd ≈ Rs, εsy,d = Rs/Es – **suy luận** quy đổi để dùng TCVN 5574 tính khả năng chịu lực.
