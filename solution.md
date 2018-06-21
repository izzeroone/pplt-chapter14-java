Đáp án chương 14 | Java
======
Mục lục
---
- [Đáp án chương 14 | Java](#ap-an-chng-14-java)
    - [Mục lục](#mc-lc)
    - [Câu hỏi và giải pháp](#cau-hi-va-gii-phap)
        - [**14.1** *Trong thừa kế, ý nghĩa của việc khai báo constuctor là private là gì ?*](#141-trong-tha-k---ngha-ca-vic-khai-bao-constuctor-la-private-la-gi)
        - [**14.2** *Trong Java, khối lệnh trong finally có được thực thi nếu chúng ta thêm câu lệnh return trong khối lệnh try trong cấu trúc try-catch-finally hay không ?*](#142-trong-java--khi-lnh-trong-finally-co-c-thc-thi-nu-chung-ta-them-cau-lnh-return-trong-khi-lnh-try-trong-cu-truc-try-catch-finally-hay-khong)
        - [**14.3** *Phân biệt các từ khóa final, finally, finalize ?*](#143-phan-bit-cac-t-khoa-final--finally--finalize)
        - [**14.4** *So sánh sự khác biệt giữa templates trong C++ và generics trong Java ?*](#144-so-sanh-s-khac-bit-gia-templates-trong-c-va-generics-trong-java)
        - [**14.5** *Giải thích object reflection trong Java là gì và tại sao nó lại hữu ích ?*](#145-gii-thich-object-reflection-trong-java-la-gi-va-ti-sao-no-li-hu-ich)
        - [**14.6** *Cài đặt lớp CircularArray hỗ trợ cấu trúc dữ liệu giống mãng mà có thể xoay một cách hữu hiệu. Class này nên là kiểu generic, và hỗ trợ con trỏ duyệt bằng cú pháp `(Obj o : circularArray)` ?*](#146-cai-t-lp-circulararray-h-tr-cu-truc-d-liu-ging-mang-ma-co-th-xoay-mt-cach-hu-hiu-class-nay-nen-la-kiu-generic--va-h-tr-con-tr-duyt-bng-cu-phap-obj-o---circulararray)

Câu hỏi và giải pháp
---

### **14.1** *Trong thừa kế, ý nghĩa của việc khai báo constuctor là private là gì ?*

**Giải pháp**
Việc khai báo constuctor là private đảm bảo rằng có bất kỳ ai ngoài class có thể khởi tạo trực tiếp class. Tr
ong trường hợp này, cách duy nhất để tạo class là cung cấp hàm static public, tương tự như khi sử dụng mẫu thiết kế Factory Method.

### **14.2** *Trong Java, khối lệnh trong finally có được thực thi nếu chúng ta thêm câu lệnh return trong khối lệnh try trong cấu trúc try-catch-finally hay không ?*

**Giải pháp**
Đúng khối lệnh sẽ được thực hiện. Khối lệnh trong *finally* vẫn sẽ được thực hiện khi khối lệnh *try* đã kết thúc hàm. Ngay cả khi chúng ta cố gắng thoát khỏi hàm trong khối lệnh *try* (bằng lệnh return, lệnh continue, lệnh break hoặc các exception), khối lệnh *finally* vẫn sẽ được thực hiện.

Tuy nhiên trong một số trường hợp khối lệnh *block* sẽ không được thực hiện như :
Máy ảo Java thoát trong khi khối lệnh *try/catch* đang thực hiện
Thread thực hiện khối lệnh *try/catch* kết thúc

### **14.3** *Phân biệt các từ khóa final, finally, finalize ?*

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

### **14.4** *So sánh sự khác biệt giữa templates trong C++ và generics trong Java ?*

**Giải pháp**

Nhiều lập trình viên cho rằng khái niệm của templates và generics là giống nhau bởi vì chúng cho phép thực hiện một số việc với List<String>. Nhưng, cách mà mỗi ngôn ngữ thực hiện và tại sao lại thực hiện như vậy có sự khác biệt tương đối lớn.

Cách cài đặt của Java generics dựa trên ý tưởng "type erasure" (xóa kiểu dữ liệu). Kỹ thuật này loại bỏ kiểu dữ liệu khi source code được chuyển sang 
byte code máy ảo Java.

Ví dụ, có 1 đoạn code ở dưới:
```java
Vector<string> vector = pew Vector<String>();
vector.add(new String("hello"));
String str = vector.get(0);
```
Sau khi biên dịch, nó sẽ được viết lại thành:

```java
Vector vector = newVector();
vector.add(new String("hello"));
String str = (String) vector.get(0);
```

Java generiscs không làm thay đổi gì nhiều khả năng của chúng ta, nó đơn giản chỉ làm cho mọi thứ trở nên đẹp hơn. Vì lí do này, Java generics thỉnh thoảng cũng được gọi là "syntactic sugar".

Điều này là khác biệt đối với C++. Trong C++, `templates` là một tập macro, và trịch biên dịch sẽ tạo ra một bản sao của template code cho mỗi kiểu dữ liệu. Bằng chứng là thể hiện của `MyClass<Foo>` sẽ không chia sẽ các biến `static` với `MyClass<Bar>`. Tuy nhiên 2 thể hiện của `MyClass<Foo>` sẽ có chung biến `static`.

Để biểu diễn, xem xét đoạn code sau: 
```c++
/*** MyClass.h ***/
template<class T> class MyClass {
    public:
        static int val;
        MyClass(int v) { val = v; }
};

/*** MyClass.cpp ***/
template<typename T>
int MyClass<T>::bar;

template class MyClass<Foo>;
template class MyClass<Bar>;

/*** main.cpp ***/
MyClass<Foo> * fool = new MyClass<Foo>(10);
MyClass<Foo> * foo2 = new MyClass<Foo>(15);
MyClass<Bar> * barl = new MyClass<Bar>(20);
MyClass<Bar> * bar2 = new MyClass<Bar>(35);

int fl = fool->val; //sẽ bằng 15
int f2 = foo2->val; //sẽ bằng 15
int bl = barl->val; //sẽ bằng 35
int b2 = bar2->val; //sẽ bằng 35
```

Trong Java, các biến static được chia sẽ cho mọi thể hiện của MyClass, mặc cho cho sự khác nhau về kiểu dữ liệu đầu vào.

Bởi vì khác nhau về kiến trúc, Java generics và C++ templates có một số điểm khác biệt bao gồm:
* C++ templates có thể dùng kiểu dữ liệu primitive như `int`. Java thì không thể và phải dùng kiểu `Integer`.
* Trong Java, bạn có thể giới hạn kiểu dữ liệu đàu vào của template chỉ cho một số kiểu dữ liệu nhất định. Ví dụ, bạn có thể sử dụng generics để cài đặt `CardDeck` và chỉ rõ kiểu dữ liệu đàu vào phải kế thừa từ `CardGame`.
* Trong C ++, tham số kiểu dữ liệu có thể được khởi tạo, trong khi Java không hỗ trợ
* Trong Java, tham số kiểu dữ liệu (tức là, Foo trong MyClass <Foo>) không thể được sử dụng cho
các phương thức và biến static, vì chúng sẽ được chia sẻ giữa MyClass <Foo> và
MyClass <Bar>. Trong C ++, các lớp này khác nhau, vì vậy tham số kiểu dữ liệu có thể là
được sử dụng cho các phương thức và biến tĩnh.
* Trong Java, tất cả các thể hiện của MyClass, bất kể tham số kiểu dữ liệu của chúng,chúng đều giống nhau về kiểu dữ liệu. Các tham số kiểu dữ liệu được xóa khi chạy. Trong C ++, các thể hiện với các tham số kiểu dữ liệu khác nhau là khác kiểu dữ liệu.

Hãy nhớ rằng mặc dù Java generics và C++ templates  trông giống nhau trong nhiều cách, nó rất khác nhau.

### **14.5** *Giải thích object reflection trong Java là gì và tại sao nó lại hữu ích ?*

**Giải pháp**

Object reflection là một đặc tính của Java cho phép duyệt thông tin về Java class và objects, và thực hiện một số thao tác như:

1. Lấy thông tin về các phương thức và trường dữ liệu hiện hữu của class lúc chạy.
2. Tạo thể hiện mới của class
3. Lấy hoặc đặc các trường dữ liệu của đối tượng thông qua tham chiếu của 

Đoạn code sau cung cấp ví dụ về object reflection.
```java
 /* Parameters */
Object[] doubleArgs = new Object[] { 4.2, 3.9 };

/* Get class */
Class rectangleDefinition = Class.forName("MyProj.Rectangle");

/* Equivalent: Rectangle rectangle = newRectangle(4.2, 3.9); */
Class[] doubleArgsClass = new Classf] {double.class, double.class};
1Constructor doubleArgsConstructor =
rectangleDefinition.getConstructor(doubleArgsClass);
Rectangle rectangle =
(Rectangle) doubleArgsConstructor.newInstance(doubleArgs);

/* Equivalent: Double area = rectangle.area(); */
Method m = rectangleDefinition.getDeclaredMethod("area");
Double area = (Double) m.invoke(rectangle);
```
Đoạn code này tương đương với
```java
Rectangle rectangle = new Rectangle(4.2, 3.9);
Double area = rectangle.area();
```

**Tại sao object reflection lại hữu ích**
Ví dụ trên có vẻ không hữu dụng cho lắm nhưng reflection có thể rất hữu ích cho một số ví dụ cụ thể.

Object reflection hữu ích vì ba lí do chính sau:
1. Nó cho phép quan sát và thay đổi cách thức hoạt động của chương trình lúc chạy
2. Nó giúp ích cho việc debug va test phần mềm, vì ta có thể truy cập thực tiếp vào càm hàm, constructor và trường dữ liệu.
3. Ta có thể gọi hàm bởi tên trong khi ta không biết gì về hàm. Ví dụ, ta có thể cho người dùng nhập vào tên class, tham số cho constuctor và tên hàm. Ta có thể dùng thông tin này để tạo một object và gọi hàm. Làm việc tương tự mà không sử dụng reflection sẽ yêu cầu sử dụng một đống câu lệnh if (nếu có thể)

### **14.6** *Cài đặt lớp CircularArray hỗ trợ cấu trúc dữ liệu giống mãng mà có thể xoay một cách hữu hiệu. Class này nên là kiểu generic, và hỗ trợ con trỏ duyệt bằng cú pháp `(Obj o : circularArray)` ?*

**Giải pháp**

Vấn đề này có hai phần. Thứ nhất ta cần cài đặt lớp CircularArray. Thứ hai, ta cần hỗ trợ con trỏ duyệt. Ta sẽ đề cập đến 2 vấn đề này 1 cách riêng biệt

**Cài đặt lớp CircularArray**

Một cách để cài đặt lớp CircularArray là dịch các phần tử mỗi khi ta gọi hàm `rotate(int shiftRight)`. Làm như vậy sẽ không hiệu quả.

Thay vì vậy, ta chỉ cần tạo biến `head` trỏ về điểm mà ta quan niệm rằng nó là điểm bắt đầu của mảng vòng. Thay thế cho việc dịch các phần tử trong mảng, ta chỉ cần tăng `head` bằng `shiftRight`.

Đoạn code sau này cài đặt theo cách tiếp cận trên
```java
public class CircularArray<T> {
    private T[] items;
    private int head = 0;

    public CircularArray(int size) {
        items = (T[]> new Object[size];
    }

    private int convert(int index) {
        if (index < 0) {
            index += items.length;
        }
        return (head + index) % items.length;
    }

    public void rotate(int shiftRight) {
        head = convert(shiftRight);
    }

    public T get(int i) {
        if (i < 0 | | i >= items.length) {
            throw new java.lang.lndexOutOfBoundsException("...");
        }
        return items[convert(i)];
    }

    public void set(int i, T item) {
        items[convert(i)] = item;
    }
}
```

Có số lưu ý mà có thể dễ dàng mắt lỗi như:
* Ta không thể tạo mảng kiểu `generic`. Thay vào đó ta chuyển kiểu dữ liệu của mảng hoặc định nghĩa `items` thuộc kiểu `List<T>`. Để đơn giản, chúng ta đã thực hiện cách sau.
* Thao tác `%` sẽ trả về giá trị âm khi `giaTriAm % viTri`. Ví dụ, `-8 % 3 = -2` - khác biệt với cách nhà toán học định nghĩa hàm chia lấy dư. Ta phải cộng `items.length` vào chỉ số âm để có được kết quả đúng.
* Ta cần phải chắc chắn chuyển đổi một cách nhất quán chỉ mục thô sang chỉ mục được xoay. Đối với lý do này, ta đã thực hiện hàm `convert` được sử dụng bởi các hàm khác. Ngay cả hàm `rotate` cũng sử dụng `convert`.Đây là ví dụ tốt về tái sử dụng code. 

Ta đã cài đặt xong CircularArray, giờ là đến lúc cài đặt con trỏ duyệt.

**Cài đặt con trỏ duyệt**
Phần thứ hai của câu hỏi yêu cầu cài đặt lớp CircularArray sao cho ta có thể thực hiện được như sau:
```java
CircularArray<String> array = ...
for (String s : array) { ... }
```
Cài đặt chức năng này yêu cầu phải cài đặt interface `Iterator`.

Để cài đặt interface `Iterator`, ta cần làm các việc sau:
* Thay đổi định nghĩa `CircularArray<T>` để thêm `implements Iterable<T>`. Điều này cũng có nghĩa là hàm `iterator()` sẽ được thêm vào `CircularArray<T>`.
* Tạo lớp `CircularArrayIterator<T>` cài đặt interface `Iterator<T>`. Điều này yêu cầu ta cần phải cài đặt hàm `hasNext()`, `next()` và `remove()` trong `CircularArrayIterator`

Sau khi đã thực hiện những điều trên, cấu trục `for loop` sẽ hoạt động một cách diệu kì.

Trong đoạn mà dưới đây, ta đã các phần cài đặt `CircularArray` giống như phần cài đặt ở trên.

```java
public class CircularArray<T> implements Iterable<T>{
    ...
    public Iterator<T> iterator() {
        return new CircularArrayIterator<T>(this);
    }

    private class CircularArrayIterator<TI> implements lterator<TI>{
    /* current reflects the offset from the rotated head, not
    * from the actual start of the raw array. */
        private int _current = -1;
        private TI[] _items;

        public CircularArrayIterator(CircularArray<TI> array){
            _items = array.items;
        }

        @Override
        public boolean hasNext() {
            return _current < items.length - 1;
        }

        @Override
        public TI next() {
            _current++;
            TI item = (TI)_items[convert(_current)];
            return item;
        }

        @Override
        public void remove() {
            throw new UnsupportedOperationException("...");
        }
    }
}
```

Trong đoạn mã ở trên, con trỏ lặp đầu tiên của vòng lặp sẽ gọi `hasNext()` sau đó là `next`. Hãy chắc chắn rằng cách cài đặt của bạn sẽ trả về giá trị đúng.

Khi bạn gặp vấn đề giống như vậy trong lúc phỏng vấn, có thể bạn không thể nhớ chính xác các hàm và các interface được gọi. Trong trường hợp này, cố gắng đi qua vấn đề một cách tốt nhất mà bạn có thể. Nếu bạn có thể lí giải được các phương thức cần thiết thì bạn sẽ được đánh gía có cơ hội cạnh tranh.