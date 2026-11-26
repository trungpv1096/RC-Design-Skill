# Cột BTCT kháng chấn – TCVN 9386-1:2025 (trang in = PDF + 4)

## Nguyên tắc
- Nội lực động đất lấy từ **mô hình động đất riêng** (độ cứng đã giảm) – không trộn với mô hình tính gió. Ghép cột giữa
  2 mô hình theo **Label + Story**; cảnh báo nếu lệch tiết diện / chiều dài.
- Tạo mô hình động đất bằng cách **sao chép file .EDB trong Explorer**, không *Save As* từ mô hình gió đã phân tích
  (đã gặp: mô hình gốc mất file kết quả .Y00–.Y05 → ETABS báo "Cannot read frame force results"; nguyên nhân là suy luận).
- Thông số cột (thép, đai) lấy từ phần tính thường; không đạt thì sửa ở phần thường rồi kiểm tra lại.
- Khả năng chịu lực: TCVN 9386 dẫn EN 1992-1-1 (5.4.3.2.1(1), tr.91); thực hành của người dùng dùng **TCVN 5574:2018**
  với quy đổi fcd ≈ Rb, fyd ≈ Rs, εsy,d = Rs/Es (ghi rõ trong thuyết minh).
- Cấp dẻo: **DCL** (5.3, tr.82) – chỉ thép loại B/C (CB400-V, CB500-V), q ≤ 1,5, không yêu cầu thêm. **DCM / DCH** – các mục dưới.

## A. Chịu lực
| Điều | Nội dung | DCM | DCH |
|---|---|---|---|
| 4.4.2.2 (tr.67–68) | θ = Ptot·dr/(Vtot·h): ≤ 0,1 bỏ qua P-Δ; 0,1–0,2 nhân 1/(1−θ); ≤ 0,3 | ✓ | ✓ |
| 4.4.2.3(4)–(6), (4.29) (tr.68–69) | Cột khỏe – dầm yếu ΣMRc ≥ 1,3·ΣMRb tại nút, 2 phương, 2 chiều; không áp cho tầng trên cùng (chi tiết mục C) | ✓ | ✓ |
| 5.4.2.3, (5.9) (tr.85–86); 5.5.2.2 (tr.100) | Lực cắt theo khả năng VEd = γRd·(MRc,1 + MRc,2)/Lcl·min(1; ΣMRb/ΣMRc), MRc tại N động đất; γRd | 1,1 | 1,3 |
| 5.4.3.2.1(3) / 5.5.3.2.1(3) | νd = NEd/(Ac·fcd) ≤ | 0,65 | 0,55 |
| 5.4.3.2.1(2) | Uốn hai phương: cho phép kiểm riêng từng phương với MRd giảm 30 % (không cần nếu dùng mặt tương tác 3D) | | |
- Lcl = L − hb (hb chiều cao dầm tại đầu cột). Chưa có thép dầm → lấy min(...) = 1 (thiên an toàn) và ghi "(4.29) chưa
  kiểm tra". (4.29) tính riêng – xem mục C; kết quả min(1; ΣMRb/ΣMRc) theo từng đầu cột đưa vào (5.9).

## C. Cột khỏe – dầm yếu (4.29) tại nút
- ΣMRc ≥ 1,3·ΣMRb tại mọi nút dầm – cột kháng chấn, nhà khung ≥ 2 tầng (4.4.2.3(4), tr.68); 2 phương X / Y tổng thể
  (dung sai 15°), cả hai chiều (+/−), mô men cột ngược chiều mô men dầm (4.4.2.3(5)); không áp dụng tầng trên cùng
  (4.4.2.3(6)) – nút không có cột phía trên (kể cả mái bậc thụt) coi như tầng trên cùng (**suy luận**).
- ΣMRc (tr.69): MRc nhỏ nhất trong khoảng biến thiên lực dọc do động đất; cho phép dùng MR tại mặt nút. Cột dùng mặt tương
  tác N–M của `cot.md` (Rb·γb3).
- ΣMRb: dầm tính theo TCVN 5574 (fcd ≈ Rb, fyd ≈ Rs – quy đổi, **suy luận**), Rb với γb1 = 1,0, Rsc giá trị trong ngoặc:
  - Mô men âm: thép chịu kéo = thép trên dầm + **thép sàn trong beff** (5.2.3.3(3), người dùng chốt **luôn kể**); vùng
    nén ở sườn b, thép nén = thép dưới dầm. (34)–(35) tr.57; x > ξR·h0 → x = ξR·h0 (8.1.2.3.5).
  - Mô men dương: chữ T cánh nén beff × hf ((36)–(38) tr.57–58, beff dùng cho cả cánh nén – **suy luận**); x < 2a' →
    (39) tr.59 với a' thay bằng min(a'; x0/2) (**suy luận**, mở rộng cho tiết diện không đối xứng).
- beff (5.4.3.1.1(3), Hình 5.5, tr.89): cột biên – bc (không có dầm ngang) / bc + 2hf mỗi bên (có dầm ngang); cột trong –
  thêm 2hf mỗi bên. Dầm ngang bất kể chiều cao coi như "cùng chiều cao" (beff lớn hơn – thiên an toàn, **suy luận**).
- Nguồn thép dầm theo ưu tiên: nhập tay tại nút > thép bố trí tab Thép dầm > As yêu cầu ETABS (sơ bộ, giả thiết Ø20).
  a = c + Øđai + Ømax/2 (1 lớp).
- Ngoại lệ 5.2.3.3(2) tr.79: a) khung phẳng ≥ 4 cột tiết diện gần giống nhau → cho phép 1/4 số cột không thỏa (chỉ ghi
  chú, không tự miễn); b) tầng dưới nhà 2 tầng nếu νd ≤ 0,3 ở mọi cột.
- Không thỏa → ETABS Tool có chức năng đề xuất thép cột cho nhóm.
- N–M với tổ hợp động đất: như cột thường (`cot.md`), tổ hợp ngắn hạn.

## B. Cấu tạo
| Điều | Yêu cầu | DCM | DCH |
|---|---|---|---|
| 5.4.1.1 (tr.83) | Bê tông ≥ C16/20 (tương đương B20); thép có gờ loại B/C trong vùng tới hạn | ✓ | ✓ |
| 5.4.1.2.2 | Cạnh cột ≥ 1/10 khoảng cách lớn nhất từ điểm uốn đến đầu cột (trừ θ ≤ 0,1) | ✓ | ✓ |
| 5.5.1.2.2(1) (tr.100) | Cạnh cột ≥ 250 mm | – | ✓ |
| 5.4.3.2.2(1),(2) (tr.91) | 1 % ≤ ρ ≤ 4 %; đối xứng nếu tiết diện đối xứng; mỗi mặt ≥ 1 thanh trung gian | ✓ | ✓ |
| (5.14) tr.91 / (5.30) tr.104 | Lcr = max(hc; Lcl/6; 0,45 m) / max(1,5hc; Lcl/6; 0,6 m) tính từ **hai đầu cột** (sát nút); Lcl/hc < 3 → cả cột | ✓ | ✓ |
| (5.18) tr.93 / (5.32) tr.105 | Bước đai vùng tới hạn s ≤ min(b0/2; 175; 8dbL) [b0 tới tâm đai] / min(b0/3; 125; 6dbL) [b0 tới mặt trong đai] | ✓ | ✓ |
| 5.4.3.2.2(10) / (5.31) | Ø đai ≥ 6 mm / ≥ 0,4·dbL,max·√(fydL/fydw) | ✓ | ✓ |
| 5.4.3.2.2(11b) / 5.5.3.2.2(12c) | Khoảng cách các thanh dọc được giữ bởi góc đai / đai móc ≤ 200 / 150 mm (1 đai ôm 3 thanh/mặt C300 → 216 mm, không đạt → thêm đai C) | ✓ | ✓ |
| (5.15)–(5.17a) tr.91–93 | Bó lõi: α·ωwd ≥ 30·μφ·νd·εsy,d·bc/b0 − 0,035; ωwd = (V đai/V lõi)·fyd/fcd; α = αn·αs, αn = 1 − Σbi²/(6b0h0), αs = (1 − s/2b0)(1 − s/2h0) | chân cột | mọi vùng tới hạn |
| 5.4.3.2.2(9) / 5.5.3.2.2(10) | ωwd ≥ 0,08 (chân) / 0,12 chân, 0,08 phía trên | ✓ | ✓ |
| 5.4.3.2.2(12) | νd < 0,2 và q ≤ 2 → đai chân cột theo EN 1992-1-1 | ✓ | – |
| 5.5.3.2.2(13),(14) | Hai tầng dưới: đai vùng tới hạn kéo thêm 0,5Lcr; thép chân cột tầng 1 ≥ đỉnh cột cùng tầng | – | ✓ |
| 5.4.3.3 (tr.94) | Đai trong nút ≥ đai vùng tới hạn cột (dầm 4 phía rộng ≥ 3/4 cạnh cột → bước ×2, ≤ 150 mm); mỗi mặt nút ≥ 1 thanh trung gian | ✓ | ✓ |
- μφ (5.2.3.4(3), tr.79–80): 2q0 − 1 khi T1 ≥ TC (5.4); 1 + 2(q0 − 1)·TC/T1 khi T1 < TC (5.5); thép loại B × 1,5 (5.2.3.4(4)).
  q0, T1, TC lấy theo phổ / Modal của mô hình động đất – người dùng tự nhập. Chỉ ảnh hưởng (5.15).

## Trình bày thuyết minh (mẫu đã duyệt)
Mục "6. Kiểm tra kháng chấn (TCVN 9386-1:2025)": dòng thông số (cấp dẻo, q0, T1, TC, tổ hợp động đất, hb, chân móng,
quy đổi vật liệu) → 6.1 Chịu lực → 6.2 Cấu tạo → ghi chú (uốn hai phương, μφ, nút). Không ghi nguồn file nội lực, không
đưa cảnh báo phần mềm vào thuyết minh. Nhóm không kiểm tra: "Không kiểm tra kháng chấn". Kết luận ở mục 7.
