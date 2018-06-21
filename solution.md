Đáp án chương 14 | Java
======

**14.1** *Trong thừa kế, ý nghĩa của việc khai báo constuctor là private là gì ?*

**Giải pháp**
Việc khai báo constuctor là private đảm bảo rằng có bất kỳ ai ngoài class có thể khởi tạo trực tiếp class. Tr
ong trường hợp này, cách duy nhất để tạo class là cung cấp hàm static public, tương tự như khi sử dụng mẫu thiết kế Factory Method.

**14.2** *Trong Java, khối lệnh trong finally có được thực thi nếu chúng ta thêm câu lệnh return trong khối lệnh try trong cấu trúc try-catch-finally hay không ?*

**Giải pháp**
Đúng khối lệnh sẽ được thực hiện. Khối lệnh trong *finally* vẫn sẽ được thực hiện khi khối lệnh *try* đã kết thúc hàm. Ngay cả khi chúng ta cố gắng thoát khỏi hàm trong khối lệnh *try* (bằng lệnh return, lệnh continue, lệnh break hoặc các exception), khối lệnh *finally* vẫn sẽ được thực hiện.

Tuy nhiên trong một số trường hợp khối lệnh *block* sẽ không được thực hiện như :
Máy ảo Java thoát trong khi khối lệnh *try/catch* đang thực hiện
Thread thực hiện khối lệnh *try/catch* kết thúc

**14.3** *Phân biệt các từ khóa final, finally, finalize ?*

**Giải pháp**
Các từ khóa có vẻ giống nhau nhưng final, finally và finallize có các mục đích khác nhau hoàn toàn. Về cơ bản, từ khóa *final* dùng để điều khiển biến, hàm hoặc class "có thể thay đổi". Từ khóa *finally* dùng trong khối lệnh *try/catch* để đảm bảo một nhóm lệnh luôn luôn thực hiện. Phương thức `finalize()` được gọi 1 lần bởi garbage collector khi xác định không còn tham chiếu nào của object tồn tại

Chi tiết về final, finally và finally như sau.

**final**  
* Khi thêm vào biến (primitive): Gía trị của biến không thể thay đổi.
* Khi thêm vào biến (reference): Gía trị của biến không thể trỏ tới đối tượng khác trong heap.
* Khi thêm vào hàm: hàm không thể bị overwrite.
* Khi thêm vào class: class không thể kế thừa.

**finally**

Khối lệnh *finally* (có thể có hoặc không) sẽ được thực hiện sau khi khối lệnh *try* hoặc khối lệnh *catch* kết thúc. Các câu lệnh trong khối lệnh *finally* sẽ luôn luôn được thực hiện (ngoại trừ máy ảo Java bị thoát trong khi thực hiện khối lệnh *try*). Khối lệnh *finally* dùng để viết đoạn code có chức năng dọn dẹp.

**finalize**

Hàm finallize() được gọi bởi garbage collector khi xác định được không còn tham chiếu nào tới object còn tồn tại. Nó thường được dùng để dọn dẹp tài nguyên như đóng file.

**14.4** *So sánh sự khác biệt giữa templates trong C++ và generics trong Java ?*

**Giải pháp**

Nhiều lập trình viên cho rằng khái niệm của templates và generics là giống nhau bởi vì chúng cho phép thực hiện một số việc với List<String>. Nhưng, cách mà mỗi ngôn ngữ thực hiện và tại sao lại thực hiện như vậy có sự khác biệt tương đối lớn.

Cách cài đặt của Java generics dựa trên ý tưởng "type erasure" (xóa kiểu dữ liệu). Kỹ thuật này loại bỏ kiểu dữ liệu khi source code được chuyển sang 
byte code máy ảo Java.

Ví dụ, có 1 đoạn code ở dưới
```java
Vector<string> vector = pew Vector<String>();
vector.add(new String("hello"));
String str = vector.get(0);
```
Sau khi biên dịch, nó sẽ được viết lại thành

```java
Vector vector = newVector()j
vector.add(new String("hello"));
String str = (String) vector.get(0)j
```

