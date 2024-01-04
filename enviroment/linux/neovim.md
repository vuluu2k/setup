# NeoVim

#### AppImage ("universal" Linux package)

The [Releases](https://github.com/neovim/neovim/releases) page provides an [AppImage](https://appimage.org/) that runs on most Linux systems. No installation is needed, just download `nvim.appimage` and run it. (It might not work if your Linux distribution is more than 4 years old.)

```
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim.appimage
chmod u+x nvim.appimage
./nvim.appimage
```

If the `./nvim.appimage` command fails, try:

```
./nvim.appimage --appimage-extract
./squashfs-root/AppRun --version

# Optional: exposing nvim globally.
sudo mv squashfs-root /
sudo ln -s /squashfs-root/AppRun /usr/bin/nvim
nvim
```

#### Note

You want apply new neovim, you need to remove neovim old from OS&#x20;

```
sudo apt remove neovim
```
