# Error

## Open more files in mac

Đây là một vấn đề liên quan đến giới hạn số lượng tệp tin mở cùng lúc trên hệ thống macOS của bạn. Mặc định, giới hạn này được đặt ở mức thấp.

Để giải quyết vấn đề này, bạn cần phải tăng giới hạn số lượng tệp tin mở cùng lúc. Dưới đây là các bước cần thực hiện:

1.  Mở Terminal và chạy lệnh sau để thêm hai cấu hình vào tệp `/etc/sysctl.conf`:

    Copy

    ```
    echo kern.maxfiles=65536 | sudo tee -a /etc/sysctl.conf
    echo kern.maxfilesperproc=65536 | sudo tee -a /etc/sysctl.conf
    ```

    Các cấu hình này sẽ thiết lập giới hạn số lượng tệp tin mở cùng lúc là 65,536.
2.  Chạy các lệnh sau để áp dụng các cấu hình mới:

    Copy

    ```
    sudo sysctl -w kern.maxfiles=65536
    sudo sysctl -w kern.maxfilesperproc=65536
    ```
3.  Cuối cùng, chạy lệnh sau để thiết lập giới hạn số lượng tệp tin mở cùng lúc cho phiên hiện tại:

    Copy

    ```
    ulimit -n 65536
    ```

Sau khi thực hiện các bước trên, hệ thống macOS của bạn sẽ có thể mở nhiều tệp tin cùng lúc hơn, giúp giải quyết vấn đề bạn đang gặp phải.
