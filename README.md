# Bài tập 06 (SELECT) của SV: Nguyễn Mạnh Hiếu -  K225480106020 - Môn Hệ quản trị CSDL

Chủ đề: Câu lệnh Select
Yêu cầu bài tập:
Cho file sv_tnut.sql (1.6MB)
1. Hãy nêu các bước để import được dữ liệu trong sv_tnut.sql vào sql server của em
2. dữ liệu đầu vào là tên của sv; sđt; ngày, tháng, năm sinh của sinh viên (của sv đang làm bài tập này)
3. nhập sql để tìm xem có những sv nào trùng hoàn toàn ngày/tháng/năm với em?
4. nhập sql để tìm xem có những sv nào trùng ngày và tháng sinh với em?
5. nhập sql để tìm xem có những sv nào trùng tháng và năm sinh với em?
6. nhập sql để tìm xem có những sv nào trùng tên với em?
7. nhập sql để tìm xem có những sv nào trùng họ và tên đệm với em.
8. nhập sql để tìm xem có những sv nào có sđt sai khác chỉ 1 số so với sđt của em.
9. BẢNG SV CÓ HƠN 9000 ROWS, HÃY LIỆT KÊ TẤT CẢ CÁC SV NGÀNH KMT, SẮP XẾP THEO TÊN VÀ HỌ ĐỆM, KIỂU TIẾNG  VIỆT, GIẢI THÍCH.
10. HÃY NHẬP SQL ĐỂ LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)

DEADLINE: 23H59:59 NGÀY 25/4/2025

1. Các bước để import được dữ liệu trong sv_tnut.sql

- Tạo DB mới trong Sql có tên là TNUT

![Screenshot 2025-04-25 155457](https://github.com/user-attachments/assets/86accf34-47b3-4ec5-810b-7e59bd7cb4ad)

- Vào File chọn Open rồi chọn File

![Screenshot 2025-04-25 155949](https://github.com/user-attachments/assets/3d4cbb1b-0746-4a64-ad3f-d7f3643bcf20)

- Chọn File sv_tnut.sql

![Screenshot 2025-04-25 160119](https://github.com/user-attachments/assets/b2bafd80-7d09-4b6b-b37e-f9f93a9d0c7c)

- Copy toàn bộ dữ liệu sv_tnut.sql

![Screenshot 2025-04-25 160323](https://github.com/user-attachments/assets/8b02a5af-1bc2-4f8f-bc84-02f9910874f7)

- Tạo 1 query mới trong db TNUT

![Screenshot 2025-04-25 160521](https://github.com/user-attachments/assets/927b1eb0-5cc0-417d-ad99-940bd32e86ca)

- Dán dữ liệu đã copy vào và sửa đổi tên sv_tnut thành tên DB đã tạo là TNUT và chạy

![Screenshot 2025-04-25 160610](https://github.com/user-attachments/assets/f6e4966b-3d80-45e9-916e-70e30ada202b)

2. Dữ liệu của sinh viên đang làm BT này:

Truy vấn theo mã sinh viên bởi vì mỗi sinh viên đều có 1 mã sinh viên riêng
```sql
SELECT * FROM SV
WHERE masv = 'K225480106020'
```
![Screenshot 2025-04-25 161851](https://github.com/user-attachments/assets/66bcc875-394d-49ac-9656-a39e2f31e5b2)

3. Tìm kiếm sinh viên có trùng ngày/tháng/năm sinh với em:

Truy vấn theo ngày/tháng/năm sinh ta sẽ có được kết quả

```sql
SELECT * FROM SV
WHERE ns = '2004-06-20'
```
![image](https://github.com/user-attachments/assets/e8126cb1-f3d7-45fc-91b7-8d3de939de87)

4. Tìm kiếm sinh viên có trùng ngày và tháng sinh với em:

Truy vấn theo ngày và tháng sinh ta sẽ có được kết quả

```sql
SELECT * FROM SV
WHERE MONTH(ns) = 06 AND DAY(ns) = 20;
```
![Screenshot 2025-04-25 162702](https://github.com/user-attachments/assets/74d812a0-014f-43db-856c-1c6581e15184)

5. Tìm kiếm sinh viên có trùng tháng và năm sinh với em:

Truy vấn theo tháng và năm sinh ta sẽ có được kết quả

```sql
SELECT * FROM SV
WHERE MONTH(ns) = 06 AND YEAR(ns) = 2004;
```
![Screenshot 2025-04-25 163014](https://github.com/user-attachments/assets/80d50c89-4d0f-426c-8146-fbb9bda07084)

6. Tìm kiếm sinh viên có trùng tên với em:

Truy vấn theo tên ta sẽ có được kết quả

```sql
SELECT * FROM SV
WHERE ten = N'Hiếu';
```
![Screenshot 2025-04-25 163415](https://github.com/user-attachments/assets/d45bc9e9-6382-430d-a814-2e62fb1633e5)

7. Tìm kiếm sinh viên có trùng họ và tên đệm với em:

Truy vấn theo họ và tên đệm ta sẽ có được kết quả

```sql
SELECT * FROM SV
WHERE hodem = N'Nguyễn Mạnh';
```

![Screenshot 2025-04-25 163642](https://github.com/user-attachments/assets/f72edbb6-d067-457c-8d75-1871426b1f68)

8. Tìm kiếm những sv có sđt sai khác chỉ 1 số so với sđt của em.

Vì có thể không có số điện thoại chỉ khác 1 số, chỉ có khác từ 2 hoặc 3 số trở lên so với sđt của em nên

Em dùng SUBSTRING để lấy từng ký tự trong sđt và dùng CASE WHEN...THEN 0 ELSE 1 END + để so sáng và

nếu giá trị mà trùng thì ghi 0(đúng) ngược lại ghi 1(sai) rồi cộng vào tổng CASE

```sql
SELECT masv, hodem, ten, sdt,
   (CASE WHEN SUBSTRING(sdt, 1, 1) = '3' THEN 0 ELSE 1 END +
    CASE WHEN SUBSTRING(sdt, 2, 1) = '7' THEN 0 ELSE 1 END +
    CASE WHEN SUBSTRING(sdt, 3, 1) = '4' THEN 0 ELSE 1 END +
    CASE WHEN SUBSTRING(sdt, 4, 1) = '9' THEN 0 ELSE 1 END +
    CASE WHEN SUBSTRING(sdt, 5, 1) = '8' THEN 0 ELSE 1 END +
    CASE WHEN SUBSTRING(sdt, 6, 1) = '1' THEN 0 ELSE 1 END +
    CASE WHEN SUBSTRING(sdt, 7, 1) = '3' THEN 0 ELSE 1 END +
    CASE WHEN SUBSTRING(sdt, 8, 1) = '3' THEN 0 ELSE 1 END +
    CASE WHEN SUBSTRING(sdt, 9, 1) = '2' THEN 0 ELSE 1 END)
AS SoLgSaiKhac
FROM SV
WHERE LEN(sdt) = 9
ORDER BY SoLgSaiKhac;
```
![Screenshot 2025-04-25 165837](https://github.com/user-attachments/assets/716606de-1871-42b8-97a0-c9e4dce8ef98)

9. Liệt kê tất cả các SV ngành KMT, sắp xếp theo tên, họ đêm, bằng tiếng việt

Em dùng SUBSTRING(lop, 4, 3) lấy ra 3 kí tự từ vị trí thứ 4 trong chuỗi lop rồi lưu vào cột mới là Nganh

dùng WHERE lop LIKE '%KMT%' để lọc ra những SV có mã lop chứa KMT

sau đó sắp xếp theo tên trước, họ đệm sau theo chuẩn tiếng việt: ORDER BY ten COLLATE Vietnamese_CI_AS, hodem COLLATE Vietnamese_CI_AS

CI để không phân biệt chữ hoa, chữ thường và AS để phân biệt dấu

```sql
SELECT *, SUBSTRING(lop, 4, 3) AS Nganh
FROM SV
WHERE lop like '%KMT%'
ORDER BY 
    ten COLLATE Vietnamese_CI_AS,
    hodem COLLATE Vietnamese_CI_AS;
```
![Screenshot 2025-04-25 173410](https://github.com/user-attachments/assets/38558c3f-0c8a-4cd2-ba94-3714d4090df7)

10. LIỆT KÊ CÁC SV NỮ NGÀNH KMT CÓ TRONG BẢNG SV (TRÌNH BÀY QUÁ TRÌNH SUY NGHĨ VÀ GIẢI NHỮNG VỨNG MẮC)

Vì trong bảng SV không có trường giới tính cho nên:

Ý tưởng tốt nhất mà em nghĩ là truy vấn theo tên và họ đệm, ở đây em dùng điều kiên là OR nghĩa là

chỉ cần 1 trong 2 trường hợp đúng đều được lấy. Tuy nhiên trường hợp này em nghĩ vẫn có sai sót

VD như có 1 bạn là nam nhưng có tên giống con gái thì vẫn truy vấn ra. Mặc dù vậy nhưng đây là cách tốt nhất em có thể nghĩ ra được

```sql
SELECT *, SUBSTRING(lop, 4, 3) AS Nganh
FROM SV
WHERE lop like '%KMT%'
  AND(
      hodem COLLATE Vietnamese_CI_AS LIKE '%Thị%'
      OR ten COLLATE Vietnamese_CI_AS IN (N'Diễm', N'Hương', N'Ngọc', N'Linh', N'Thảo',
		                                  N'Vân', N'Mai', N'Huyền', N'Trang', N'Vy', N'Lan')
     )
ORDER BY 
    ten COLLATE Vietnamese_CI_AS,
    hodem COLLATE Vietnamese_CI_AS;
```
![image](https://github.com/user-attachments/assets/e50e0e4b-94a9-4507-8a65-c4c251962847)
