Tệp MEMZ.txt nằm trong thư mục "Toàn bộ dữ liệu của MEMZ trojan" kia là toàn bộ dữ liệu của MEMZ trojan.
⚠️ MEMZ Trojan - Educational Analysis
MEMZ là một loại mã độc (Trojan) cực kỳ nổi tiếng, ban đầu được tạo ra bởi Leurak cho series "Malware Watch" trên YouTube. Nó được thiết kế để phô diễn các khả năng phá hoại hệ thống Windows theo cách hài hước nhưng cực kỳ nguy hiểm.
Link quét của virustotal: https://www.virustotal.com/gui/file/5e2cd213ff47b7657abd9167c38ffd8b53c13261fe22adddea92b5a2d9e320ad

CẢNH BÁO: Đây là một mã độc thực sự. Không bao giờ chạy tệp tin thực thi của MEMZ trên máy tính thật. Chỉ nên thử nghiệm trong môi trường máy ảo (Virtual Machine) hoàn toàn cách ly.

🚀 Các giai đoạn tấn công (Payloads)
MEMZ không phá hủy dữ liệu ngay lập tức mà đi qua nhiều giai đoạn khiến người dùng "khốn đốn":

1. Giai đoạn nhẹ (Tâm lý)
Mở trang web tự động: Tự động mở các tìm kiếm vô nghĩa trên Google hoặc các trang web meme (như Nyan Cat).

Chạy ứng dụng: Mở ngẫu nhiên các phần mềm hệ thống như calc.exe, notepad.exe.

2. Giai đoạn can thiệp hệ thống
Lỗi con trỏ chuột: Chuột sẽ tự nhảy loạn xạ hoặc để lại "dấu vết" trên màn hình.

Đảo ngược màu sắc: Toàn bộ màn hình sẽ bị đảo ngược màu liên tục (Invert colors).

Chụp ảnh màn hình (Tunnel effect): Tạo hiệu ứng lồng hình ảnh liên tiếp, khiến màn hình trông như một đường hầm.

3. Giai đoạn cuối (Sát thủ)
Ghi đè MBR (Master Boot Record): Đây là phần nguy hiểm nhất. MEMZ sẽ ghi đè lên phân vùng khởi động của ổ cứng.

Màn hình xanh (BSOD): Nếu người dùng cố gắng tắt MEMZ qua Task Manager, hệ thống sẽ bị treo và hiện màn hình xanh ngay lập tức.

Nyan Cat Bootloader: Khi khởi động lại máy, hệ điều hành sẽ không thể load được. Thay vào đó, một đoạn hoạt họa Nyan Cat sẽ xuất hiện trên nền DOS cùng bản nhạc kinh điển.

🛠 Cách thức hoạt động
MEMZ được viết chủ yếu bằng ngôn ngữ C++. Nó sử dụng các Windows API để:

CreateThread để chạy nhiều payload cùng lúc.

BitBlt để thao tác trực tiếp với đồ họa của màn hình (GDI payloads).

CreateFile và WriteFile để truy cập trực tiếp vào \\.\PhysicalDrive0 nhằm ghi đè MBR.

🛡️ Cách phòng chống và xử lý
Môi trường thử nghiệm: Luôn sử dụng VMware hoặc VirtualBox và tắt tính năng Shared Folders.

Khôi phục MBR: Nếu máy bị nhiễm, bạn cần dùng đĩa cài đặt Windows, vào chế độ Command Prompt và sử dụng lệnh:

bootrec /fixmbr

bootrec /fixboot

Công cụ an toàn: Có một phiên bản "Clean" của MEMZ được cộng đồng tạo ra, chỉ bao gồm các hiệu ứng hình ảnh mà không phá hủy MBR.

📜 Giấy phép & Tuyên bố miễn trừ trách nhiệm
Tác giả gốc: Leurak.

Mục đích: Chỉ dành cho nghiên cứu giáo dục và an ninh mạng.

Lưu ý: Tôi (người tạo file này) không chịu trách nhiệm cho bất kỳ thiệt hại nào do việc sử dụng sai mục đích mã nguồn hoặc tệp tin liên quan đến MEMZ.📁 Cấu trúc tệp tin
MEMZ.txt: Đây là tệp quan trọng nhất, chứa toàn bộ dữ liệu và mã nguồn gốc của MEMZ Trojan.

.bat scripts: Các tệp thực thi batch file được sử dụng để kích hoạt các tiến trình hoặc payload của virus trên môi trường Windows.

🔍 Chi tiết về tệp MEMZ.txt
Tệp MEMZ.txt chứa logic cốt lõi của Trojan, bao gồm:

Dữ liệu Hex/Binary: Các mã máy được sử dụng để ghi đè vào phân vùng MBR (Master Boot Record).

Payload Logic: Các hàm điều khiển đồ họa GDI (gây nhiễu màn hình, đảo ngược màu sắc).

Nyan Cat Animation: Dữ liệu hình ảnh và âm thanh được nạp vào trình khởi động sau khi hệ thống bị phá hủy.

⚙️ Cơ chế hoạt động của phiên bản Batch (.bat)
Các tệp .bat trong thư mục này thường được thiết kế để:

Tự động sao chép mã độc vào các thư mục hệ thống.

Vô hiệu hóa các công cụ bảo vệ như Task Manager hoặc Registry Editor.

Tạo các vòng lặp vô tận để mở hàng loạt trang web và ứng dụng, làm cạn kiệt tài nguyên CPU/RAM.

🚫 CẢNH BÁO AN TOÀN
[!CAUTION] TUYỆT ĐỐI KHÔNG đổi đuôi tệp MEMZ.txt thành .exe hoặc chạy các tệp .bat trực tiếp trên máy tính cá nhân.

Hậu quả: Mất khả năng khởi động Windows, mất dữ liệu phân vùng ổ cứng.

Khuyến nghị: Chỉ mở mã nguồn bằng các trình soạn thảo văn bản (Notepad, VS Code) để đọc và học tập.
