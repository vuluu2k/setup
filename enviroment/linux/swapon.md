---
description: swapon more ram for linux
---

# Swapon

Để tạo một phân vùng swap bằng cách sử dụng một phần của RAM trong Linux, bạn có thể làm theo các bước sau:

1. Mở một terminal: Mở một terminal trên hệ thống Linux của bạn. Bạn thường có thể tìm thấy nó trong menu ứng dụng hoặc bằng cách sử dụng phím tắt Ctrl+Alt+T.
2.  Kiểm tra không gian swap có sẵn: Chạy lệnh sau để kiểm tra xem bạn đã có một phân vùng swap hoặc tệp tin swap đã được thiết lập chưa:

    ```
    sudo swapon --show
    ```

    Lệnh này sẽ hiển thị bất kỳ phân vùng swap hoặc tệp tin swap hiện có cùng kích thước của chúng.
3.  Tạo một tệp tin swap: Nếu bạn chưa có phân vùng swap hoặc tệp tin swap, bạn có thể tạo một tệp tin swap. Xác định kích thước mong muốn cho tệp tin swap của bạn. Ví dụ, nếu bạn muốn tạo một tệp tin swap 2GB, bạn có thể sử dụng lệnh sau:

    ```
    sudo fallocate -l 2G /swapfile
    ```

    Lệnh này sẽ tạo một tệp tin 2GB có tên là `/swapfile`. Điều chỉnh kích thước tùy theo nhu cầu của bạn.
4.  Thiết lập quyền hợp lý: Thiết lập quyền hợp lý cho tệp tin swap bằng lệnh sau:

    ```
    sudo chmod 600 /swapfile
    ```

    Lệnh này đảm bảo rằng chỉ người dùng root mới có quyền đọc và ghi vào tệp tin swap.
5.  Thiết lập không gian swap: Kích hoạt không gian swap bằng cách chạy lệnh sau:

    ```
    sudo mkswap /swapfile
    ```

    Lệnh này định dạng tệp tin swap theo định dạng swap.
6.  Kích hoạt tệp tin swap: Kích hoạt tệp tin swap vừa tạo bằng lệnh sau:

    ```
    sudo swapon /swapfile
    ```

    Lệnh này kích hoạt tệp tin swap và làm cho nó sẵn sàng để sử dụng.
7.  Làm cho tệp tin swap tồn tại: Để đảm bảo rằng tệp tin swap được kích hoạt tự động khi khởi động hệ thống, hãy mở tệp tin `/etc/fstab` bằng một trình soạn thảo văn bản bằng lệnh sau:

    ```
    sudo nano /etc/fstab
    ```

    Thêm dòng sau vào cuối tệp tin:

    ```
    /swapfile none swap sw 0 0
    ```

    Lưu tệp tin và thoát trình soạn thảo văn bản.
8.  Xác minh không gian swap: Bạn có thể xác minh rằng không gian swap đã được thiết lập đúng bằng cách chạy lệnh:

    ```
    sudo swapon --show
    ```

    Nó sẽ hiển thị tệp tin swap và kích thước của nó.

Bằng cách làm theo các bước này, bạn có thể tạo một tệp tin swap sử dụng một phần của không gian đĩa làm bộ nhớ ảo trong Linux.
