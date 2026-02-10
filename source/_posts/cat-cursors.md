---
title: 猫标主题鼠标指针
date: 2025-02-11 01:15:24

tags:
    - 鼠标指针
    - 移植
    - Linux
categories:
    - 项目

thumbnail: 
excerpt: 猫标主题鼠标指针。由哔哩哔哩用户 406949928（HappyCadogt）创作，由我移植。
---
## 关于项目

- 原作者：<a href="https://space.bilibili.com/406949928"><i class="fa-brands fa-bilibili"></i> HappyCadogt <i class="fa-solid fa-arrow-up-right ml-[0.2em] font-light align-text-top text-[0.7em] link-icon"></i></a>
- 移植者：<a href="https://github.com/Tseshongfeeshur"><i class="fa-brands fa-github"></i> Ryan <i class="fa-solid fa-arrow-up-right ml-[0.2em] font-light align-text-top text-[0.7em] link-icon"></i></a>
- 项目地址：[GitHub](https://github.com/Tseshongfeeshur/cat-cursors)

由于截至项目发布（2025.12.6），原作者仅为 Windows 平台提供适配，尚未提供 [GNU](https://www.gnu.org/)/[Linux](https://kernel.org/) 版本，遂将其移植为适用于大多数桌面环境的 [XDG 主题包](https://specifications.freedesktop.org/icon-theme/latest/)，以供 [GNU](https://www.gnu.org/)/[Linux](https://kernel.org/) 用户使用。

{% note purple %}
特别感谢原作者的付出和努力，否则该移植项目不可能出现，我们也不可能用到如此精美的鼠标指针。
{% endnote %}

## 项目内容

<!-- ![封面](/images/cat-cursors/banner.png) -->

- 由 <a href="https://space.bilibili.com/406949928"><i class="fa-brands fa-bilibili"></i> HappyCadogt <i class="fa-solid fa-arrow-up-right ml-[0.2em] font-light align-text-top text-[0.7em] link-icon"></i></a>设计并制作
- **全部**为动态图标
- 支持 **24 / 32 / 48 / 64 / 96 / 128 / 192 / 256** 多分辨率

## 适用平台

- [GNU](https://www.gnu.org/)/[Linux](https://kernel.org/) 平台所有支持 [XDG 主题包](https://specifications.freedesktop.org/icon-theme/latest/)的桌面环境

{% note regular %}
在 [KDE Plasma](https://kde.org/plasma-desktop/)、[GNOME](https://www.gnome.org/) 通过测试，表现良好。
{% endnote %}

## 安装方式

{% tabs installation %}
<!-- tab Arch Linux -->
- 使用 AUR 助手
  ```zsh
  paru -S cat-cursors-git
  ```
  **或**选择其他您喜欢的 AUR 助手：
  ```zsh
  yay -S cat-cursors-git
  ```
- 手动安装 AUR 包
  ```zsh
  sudo pacman -S --needed base-devel
  git clone https://aur.archlinux.org/cat-cursors-git.git
  cd hei-cursors-git
  makepkg -si
  ```
<!-- endtab -->
<!-- tab 暂不支持其他发行版（手动安装） -->
1. <details class="regular" data-header-exclude="">
    <summary>
        <i class="fa-solid fa-chevron-right"></i>
        安装 <code>git</code>
    </summary>
    <div class="content markdown-body">
        <p>
            <ul>
                <li>
                    Debian
                    ```zsh
                    sudo apt update
                    sudo apt install git
                    ```
                </li>
                <li>
                    Fedora
                    ```zsh
                    sudo dnf install git
                    ```
                </li>
                <li>
                    Arch Linux
                    ```zsh
                    sudo pacman -S git
                    ```
                </li>
            </ul>
        </p>
    </div>
</details>
2. 安装主题包
   - 为**当前用户**安装：
   ```zsh
   git clone https://github.com/Tseshongfeeshur/cat-cursors.git hei_cursors
   mkdir -p ~/.local/share/icons/
   mv ./hei_cursors ~/.local/share/icons/
   ```
   - **或**为**所有用户**安装 **（不建议）**：
   ```zsh
   git clone https://github.com/Tseshongfeeshur/cat-cursors.git hei_cursors
   sudo mkdir -p /usr/share/icons/
   sudo mv ./hei_cursors /usr/share/icons/
   ```
<!-- endtab -->
{% endtabs %}

## 应用方式

{% tabs application %}
 
<!-- tab KDE Plasma -->
 
1. 导航至**系统设置 → 外观和样式 → 颜色和主题 → 光标**，或：
   ```zsh
   systemsettings kcm_cursortheme
   ```
2. 单击“**猫标**”光标样式后单击窗口右下角“**应用**”
3. 在窗口上方选择观感舒适的光标大小
 
<!-- endtab -->
<!-- tab GNOME -->
 
1. <details class="regular" data-header-exclude="">
    <summary>
        <i class="fa-solid fa-chevron-right"></i>
        安装 <code>gnome-tweaks</code>
    </summary>
    <div class="content markdown-body">
        <p>
            <ul>
                <li>
                    Debian
                    ```zsh
                    sudo apt update
                    sudo apt install gnome-tweaks
                    ```
                </li>
                <li>
                    Fedora
                    ```zsh
                    sudo dnf install gnome-tweaks
                    ```
                </li>
                <li>
                    Arch Linux
                    ```zsh
                    sudo pacman -S gnome-tweaks
                    ```
                </li>
            </ul>
        </p>
    </div>
</details>
2. 导航至**优化 → 外观 → 光标**
3. 单击下拉菜单，选择“**Cat_cursor**”光标样式
4. 选择观感舒适的光标大小：
   ```zsh
   gsettings set org.gnome.desktop.interface cursor-size $px
   # 将“$px”改为您需要的像素值，如 48
   ```
 
<!-- endtab -->
<!-- tab 其他桌面环境 -->
由于桌面环境 / 窗口管理器种类繁多，请查看其他平台对应文档，恕不一一赘述。
<!-- endtab -->
{% endtabs %}

## 鸣谢

- 原作者 <a href="https://space.bilibili.com/406949928"><i class="fa-brands fa-bilibili"></i> HappyCadogt <i class="fa-solid fa-arrow-up-right ml-[0.2em] font-light align-text-top text-[0.7em] link-icon"></i></a>，没有他的付出，就没有这个项目
- `xorg-xcursorgen`，它为多分辨率图标的生成提供了很便捷的方式
