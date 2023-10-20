# setup docker in wsl2

## Tải [docker desktop](https://www.docker.com/products/docker-desktop) về trước

## 1. Bắt đầu cài đặt cấu hình phù hợp để chạy docker trên wsl2

Trong verison hệ điểu hành ảo mà bạn chọn ơ đây mình chọn ubuntu 20.04 mở terminal của nó lên

```shell
sudo vim /etc/wsl.conf
```

\
**Thêm đoạn code sau vào dưới cuối để limit memory và cho phép localhost trên máy windows và wsl2 thông nhau**\


```console
[wsl2]
memory=6GB
swap=0
localhostForwarding=true
```

## 2. Trong Docker desktop

* Tích chọn **Enable the experimental WSL2 based engine**
* Bỏ tích **Expose tcp://localhost:2375** ![](https://images.viblo.asia/dc34682d-7c96-4586-8a70-28befdca80c4.png)
* Bật WSL2 integration với Distro dùng WSL2 ![](https://images.viblo.asia/dc34682d-7c96-4586-8a70-28befdca80c4.png)
* Apply & Restart rồi mọi thứ sẽ chạy như bình thường.
