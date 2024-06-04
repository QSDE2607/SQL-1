# SQL-1
Thiết kế cơ sở dữ liệu báo điện tử

Tên dự án: Thiết kế cơ sở dữ liệu báo điện tử

Tổng quan dự án

Trong bài ASM này, sẽ cần đi xây dựng cơ sở dữ liệu của một hãng báo điện tử. Các bạn sẽ cần thiết kế ERD theo mô tả, sau đó thiết kế lược đồ CSDL và thực hiện các truy vấn nghiệp vụ đối với cơ sở dữ liệu. Các bạn đã được cung cấp sẵn dữ liệu để thực hiện thao tác insert trong phần tài nguyên.

1. Thiết kế ERD

Cơ sở dữ liệu báo điện tử sẽ có 6 đối tượng chính:

Quản trị viên trang web sẽ quản lý bài đăng của các reposter (duyệt hay không duyệt).
Reposter (phóng viên) sẽ thực hiện viết bài và đăng bài( chờ quản trị viên duyệt).
Người sử dụng xem thông tin trên các bài viết, có thể tìm bài viết qua các tiêu đề, ...
POST (bài viết) được viết bởi các reposter và được quản lý bởi quản trị viên website.
SHARE - hành động này là của người dùng, đối tượng share là bài viết (POST). 
COMMENT - hành động này là của người dùng, đối tượng bình luận là bài viết (POST). Một người dùng có thể bình luận nhiều bài viết và một bài viết cũng có thể được bình luận bởi nhiều người dùng.     
 6 đối tượng trên sẽ có các thông tin tương ứng như dưới đây:

MANAGERS(ID_MNG, TEN, NAM_SINH)
REPOSTER(ID_REPOSTER, TEN ,NAM_SINH, TO_CHUC)
USER(ID_USER , ACCOUNT_NAME, PASSWORD , FACEBOOK_USER, EMAIL_USER )
POST(ID_POST , TIEU_DE , NOI_DUNG , IMAGE , TAC_GIA ,LUOT_XEM,  XET_DUYET, NGUOI_DUYET, THOI_GIAN_DANG )
SHARE(ID_SHARE, TIME_SHARE)
COMMENT(ID_COMMENT , TIME_COMMENT, NOI_DUNG)
 Nhiệm vụ của các bạn là thiết kế ERD để thể hiện được thông tin và mối quan hệ của 6 đối tượng trên.

2. Thiết kế lược đồ CSDL

Từ sơ đồ ERD đã thiết kế ở yêu cầu 1, các bạn hãy thiết kế lược đồ CSDL ở mức vật lý (tất cả các đối tượng các bạn sẽ để id là tự động tăng). Từ file lược đồ CSDL trong MySQL Workbench, các bạn có thể tạo các bảng tương ứng. Các bạn có thể tham khảo tại đây.
Sau khi thiết kết xong lược đồ CSDL, các bạn hãy chỉ ra các cặp quan hệ có tồn tại ràng buộc toàn vẹn tham chiếu.
3. Thực hiện insert dữ liệu

Từ file dữ liệu được cung cấp sẵn, các bạn hãy thực hiện insert dữ liệu vào các bảng đã tạo.

4. Thực hiện các truy vấn 

Các bạn cần viết câu truy vấn SQL để thực hiện các yêu cầu sau:

Truy vấn tất cả bảng POST và MANAGERS
Trong bảng POST, truy vấn những bài viết có LUOT_XEM lớn hơn 20.


Trong bảng POST, viết truy vấn những bài viết đã được xét duyệt và sắp xếp kết quả theo thứ tự bảng chữ cái của cột tiêu đề.


Viết truy vấn để lấy tên các acount_name của user comment vào POST: 


Viết truy vấn để tìm nội dung bài viết bắt đầu bằng chữ ‘n’


Tạo VIEW để lấy ra những bài viết đã được duyệt bởi những người quản lý.
Tạo VIEW để lấy ra các comment của user.
5. Thực hiện tạo Thủ tục và Function

Tạo thủ tục để lấy được những bài viết đã được duyệt

Tạo thủ tục để lấy những bài viết chưa được duyệt trước ngày 01-02-2018.

Tạo function để lấy được số tháng lớn nhất mà các bài viết đã đăng kể từ thời điểm được đăng đến thời điểm 01-01-2019 trong bảng POST.
- Số tháng sẽ không được làm tròn, ví dụ như sau

+ ví dụ 1:  từ 01-01-2019 đến 01-02-2019 sẽ coi là 1 tháng

+ ví dụ 2:  từ 01-01-2019 đến 02-02-2019 sẽ coi là 1 tháng (lấy 2 tháng sẽ không đúng do phải đến ngày 01-03-2019 với coi là 2 tháng)

+ ví dụ 3:  từ 01-01-2019 đến 05-03-2019 sẽ coi là 2 tháng

+ ví dụ 4:  từ 01-01-2019 đến 31-01-2019 sẽ coi là 0 tháng (do chưa đủ 1 tháng)

Gợi ý: Sử dụng hàm TIMESTAMPDIFF



6. Tạo trigger (Không bắt buộc) và INDEX

Bạn hãy tạo một trigger để lưu lại mỗi user đã thực hiện comment bao nhiêu lần theo từng ngày.
Lựa chọn một hoặc nhiều cột trong số các bảng đã tạo để tiến hành tạo INDEX. Sau khi tạo INDEX, các bạn hãy chỉ ra lý do chọn một hoặc nhiều cột đó để đánh INDEX.
