# Cài đặt version manager asdf trên wsl2

## 1. Cài đặt một số công cụ cần thiết

```bash
sudo apt-get update
sudo apt install autoconf bison build-essential libssl-dev libyaml-dev libreadline-dev zlib1g-dev libncurses-dev libffi-dev libgdbm-dev
sudo apt install curl git
```

## 2. Vô trang chủ [asdf](hhttps://asdf-vm.com/guide/getting-started.html#community-supported-download-methods)

* Cài đặt phiên bản mới nhất hiện tại

  ```bash
  git clone https://github.com/asdf-vm/asdf.git ~/.asdf --branch v0.11.3
  ```
* Mở cài đặt Cầu hình sao cho phù hợp ở đây mình dùng zsh nên mình sẽ vô zshrc

  ```bash
  sudo vi ~/.zshrc
  ```
* Thêm đoạn mã sau vào cuối file

  ```console
  . "$HOME/.asdf/asdf.sh"
  ```
