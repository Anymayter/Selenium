# Kiểm Thử Tự Động Chức Năng Đăng Nhập Sử Dụng Selenium (Java)

# 1. Giới thiệu

Dự án này hướng dẫn sinh viên thực hành viết và thực thi các kịch bản kiểm thử tự động cho chức năng đăng nhập của một trang web mẫu. Selenium là một công cụ kiểm thử tự động phổ biến, hỗ trợ tương tác với các thành phần giao diện người dùng như nhập liệu, nhấn nút, và kiểm tra kết quả hiển thị, từ đó giúp phát hiện lỗi một cách hiệu quả và nhanh chóng trong quá trình phát triển phần mềm. của một trang web mẫu sử dụng Selenium WebDriver và ngôn ngữ Java.

# 2. Mục tiêu

- Thực hành tương tác với các thành phần giao diện web qua Selenium.

- Kiểm thử tự động chức năng đăng nhập với các tình huống:

- Đăng nhập thành công.

- Đăng nhập thất bại.

- Trường nhập liệu trống.

# 3. Yêu Cầu Dự Án

1. Cài đặt Môi Trường

- Cài đặt Java JDK.

- Thêm Selenium vào project qua Maven hoặc JAR file.

- Tải xuống WebDriver (ChromeDriver, GeckoDriver, v.v.).

2. Kịch Bản Kiểm Thử

- Test Case 1: Đăng nhập thành công với tên người dùng và mật khẩu hợp lệ.

- Test Case 2: Đăng nhập thất bại với tên người dùng hoặc mật khẩu không hợp lệ.

- Test Case 3: Nhấn đăng nhập khi để trống các trường nhập liệu.

3. Mã Nguồn Java

```java

import org.openqa.selenium.By;
import org.openqa.selenium.WebDriver;
import org.openqa.selenium.WebElement;
import org.openqa.selenium.chrome.ChromeDriver;

public class LoginTest {
    public static void main(String[] args) {
        // Thiết lập WebDriver và đường dẫn đến ChromeDriver
        System.setProperty("webdriver.chrome.driver", "path_to_chromedriver");
        WebDriver driver = new ChromeDriver();

        try {
            // Truy cập trang web
            driver.get("https://example.com/login");

            // Test Case 1: Đăng nhập thành công
            WebElement usernameField = driver.findElement(By.id("username"));
            WebElement passwordField = driver.findElement(By.id("password"));
            WebElement loginButton = driver.findElement(By.id("login_button"));

            usernameField.sendKeys("valid_username");
            passwordField.sendKeys("valid_password");
            loginButton.click();

            String successMessage = driver.findElement(By.id("success_message")).getText();
            if (successMessage.contains("Welcome")) {
                System.out.println("Test Case 1: PASS");
            } else {
                System.out.println("Test Case 1: FAIL");
            }

            // Test Case 2: Đăng nhập thất bại
            driver.get("https://example.com/login");
            usernameField = driver.findElement(By.id("username"));
            passwordField = driver.findElement(By.id("password"));
            loginButton = driver.findElement(By.id("login_button"));

            usernameField.sendKeys("invalid_username");
            passwordField.sendKeys("invalid_password");
            loginButton.click();

            String errorMessage = driver.findElement(By.id("error_message")).getText();
            if (errorMessage.contains("Invalid username or password")) {
                System.out.println("Test Case 2: PASS");
            } else {
                System.out.println("Test Case 2: FAIL");
            }

            // Test Case 3: Trường trống
            driver.get("https://example.com/login");
            loginButton = driver.findElement(By.id("login_button"));
            loginButton.click();

            String emptyFieldMessage = driver.findElement(By.id("error_message")).getText();
            if (emptyFieldMessage.contains("Please enter username and password")) {
                System.out.println("Test Case 3: PASS");
            } else {
                System.out.println("Test Case 3: FAIL");
            }

        } catch (Exception e) {
            System.out.println("Có lỗi xảy ra: " + e.getMessage());
        } finally {
            // Đóng trình duyệt
            driver.quit();
        }
    }
}

```

# 4. Kết Quả Mong Đợi

- Mỗi trường Selenium được thiết lập và chạy thành công.

- Kết quả kiểm thử phải được đối chiếu với từng kịch bản bằng cách:

   1. Xác minh thông báo hiển thị trên giao diện sau khi thực hiện từng thao tác kiểm thử.

   2. Kiểm tra trạng thái (PASS/FAIL) được in ra console phù hợp với điều kiện mong đợi trong mỗi test case.

   3. Đối chiếu dữ liệu đầu vào với kết quả thực tế hiển thị để đảm bảo không có lỗi phát sinh.

- Kết quả chạy tốt cho 3 kịch bản:

   1. PASS hoặc FAIL được in ra console.

   2. Xác minh đúng các thông báo sau khi đăng nhập.

# 5. Yêu Cầu Nộp Bài


# 6. Mở Rộng (Tùy Chọn)

- Thực hiện kiểm thử trên nhiều trình duyệt (Chrome, Firefox).

- Kiểm thử các chức năng khác như tìm kiếm, đăng ký, đặt hàng.

- Tạo báo cáo tự động bằng ExtentReports hoặc Allure.
