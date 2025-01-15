# Kiểm Thử Tự Động Chức Năng Đăng Nhập Sử Dụng Selenium (Java)

## 1. Mô tả bài tập

Bài tập này tập trung vào việc xây dựng bộ kiểm thử tự động cho chức năng đăng nhập của website demo sử dụng Selenium WebDriver và JUnit framework. Website được sử dụng để kiểm thử: [https://the-internet.herokuapp.com/login](https://the-internet.herokuapp.com/login)

### 1.1 Mục tiêu học tập
- Hiểu và áp dụng được các nguyên tắc cơ bản của kiểm thử tự động.
- Thành thạo việc sử dụng Selenium WebDriver để tương tác với web elements.
- Nắm vững cách tổ chức và viết test cases sử dụng JUnit framework.
- Phát triển kỹ năng xử lý các tình huống bất đồng bộ trong kiểm thử web.
- Áp dụng các practice tốt trong việc tổ chức mã nguồn và tài liệu.

## 2. Cấu trúc project

![image](https://github.com/user-attachments/assets/c2fbfb33-005e-41a5-9010-b9233211ffaa)

## 3. Yêu cầu cài đặt

### 3.1 Yêu cầu môi trường
- JDK 11 trở lên
- Maven 3.6.3 trở lên
- Chrome browser phiên bản mới nhất
- ChromeDriver tương thích với phiên bản Chrome

### 3.2 Cài đặt dependencies
Thêm các dependencies sau vào file `pom.xml`:

```xml
<dependencies>
    <!-- Selenium WebDriver -->
    <dependency>
        <groupId>org.seleniumhq.selenium</groupId>
        <artifactId>selenium-java</artifactId>
        <version>4.16.1</version>
    </dependency>

    <!-- JUnit Jupiter -->
    <dependency>
        <groupId>org.junit.jupiter</groupId>
        <artifactId>junit-jupiter-api</artifactId>
        <version>5.10.1</version>
        <scope>test</scope>
    </dependency>

    <!-- TestNG -->
    <dependency>
        <groupId>org.testng</groupId>
        <artifactId>testng</artifactId>
        <version>7.8.0</version>
        <scope>test</scope>
    </dependency>

    <!-- Log4j -->
    <dependency>
        <groupId>org.apache.logging.log4j</groupId>
        <artifactId>log4j-core</artifactId>
        <version>2.22.1</version>
    </dependency>

    <!-- ExtentReports -->
    <dependency>
        <groupId>com.aventstack</groupId>
        <artifactId>extentreports</artifactId>
        <version>5.1.1</version>
    </dependency>
</dependencies>

```

## 4. Các test case đã implement

### 4.1 Test cases cơ bản

- testLoginSuccess
Mục đích: Kiểm tra đăng nhập thành công với thông tin hợp lệ.
Input: username="tomsmith", password="SuperSecretPassword!"
Expected output: Hiển thị thông báo đăng nhập thành công.

- testLoginInvalidUsername
Mục đích: Kiểm tra xử lý đăng nhập với username không hợp lệ.
Input: username="invalid_user", password="SuperSecretPassword!"
Expected output: Hiển thị thông báo lỗi.

- testLoginInvalidPassword
Mục đích: Kiểm tra xử lý đăng nhập với password không hợp lệ.
Input: username="tomsmith", password="wrong_password"
Expected output: Hiển thị thông báo lỗi.

### 4.2 Test cases nâng cao (đã thêm)

- testEmptyCredentials
Kiểm tra xử lý khi không nhập username và password.

- testSpecialCharacters
Kiểm tra xử lý ký tự đặc biệt trong form đăng nhập.

- testMaxLength
Kiểm tra giới hạn độ dài của username và password.

## 5. Cách chạy test

### 5.1 Chạy toàn bộ test suite

mvn test

### 5.2 Chạy test case cụ thể

mvn test -Dtest=LoginTest

### 6. Các cải tiến đã thực hiện
- Tối ưu hóa cấu trúc project.
- Áp dụng Page Object Model.
- Sử dụng TestNG annotations để quản lý test flow.
- Implement logging system với Log4j.
- Sử dụng ExtentReports để tạo báo cáo test.

Xử lý bất đồng bộ
- Sử dụng WebDriverWait và ExpectedConditions.
- Custom FluentWait cho các trường hợp đặc biệt.

Báo cáo test
- HTML reports với ExtentReports.
- Screenshots tự động khi test fail.
- Log details cho từng test step.

## 7. Hướng phát triển

Thêm các test case cho:

- Session handling.
- Cross-browser testing (sử dụng WebDriverManager).
- Performance testing với JMeter.

Cải thiện reporting:

- Tích hợp với Jenkins pipeline.
- Gửi email report tự động.
- Dashboard theo dõi test metrics.
## 8. Tài liệu tham khảo

- Selenium Java Documentation
- TestNG Documentation
- Page Object Model Practices


## 9. Đóng góp
Mọi đóng góp và phản hồi xin gửi về email: ToanNguyen130104@gmail.com
