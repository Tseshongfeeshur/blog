---
title: 罗小黑主题鼠标指针
date: 2025-12-29 19:14:08

tags:
    - 罗小黑
    - 鼠标指针
    - 移植
categories:
    - 项目

thumbnail: /images/hei-cursors/banner.png
excerpt: 罗小黑主题鼠标指针。由哔哩哔哩用户 1013625945（漓翎_cub）创作，由我移植。
---
## 关于项目

- 原作者：<a href="https://space.bilibili.com/1013625945"><i class="fa-brands fa-bilibili"></i> 漓翎_cub <i class="fa-solid fa-arrow-up-right ml-[0.2em] font-light align-text-top text-[0.7em] link-icon"></i></a>
- 移植者：<a href="https://github.com/Tseshongfeeshur"><i class="fa-brands fa-github"></i> Ryan <i class="fa-solid fa-arrow-up-right ml-[0.2em] font-light align-text-top text-[0.7em] link-icon"></i></a>
- 项目地址：[GitHub](https://github.com/Tseshongfeeshur/hei-cursors)

由于截至项目发布（2025.12.6），原作者仅为 Windows 和 MacOS 平台提供适配，尚未提供 [GNU](https://www.gnu.org/)/[Linux](https://kernel.org/) 版本，遂将其移植为适用于大多数桌面环境的 [XDG 主题包](https://specifications.freedesktop.org/icon-theme/latest/)，以供 [GNU](https://www.gnu.org/)/[Linux](https://kernel.org/) 用户使用。

{% note purple %}
特别感谢原作者的付出和努力，否则该移植项目不可能出现，我们也不可能用到如此精美的鼠标指针。
{% endnote %}

## 项目内容

![封面](/images/hei-cursors/banner.png)

- 以在[《罗小黑战记》](https://www.bilibili.com/bangumi/play/ep32374)系列作品中出场的角色“罗小黑”为原型，由 <a href="https://space.bilibili.com/1013625945"><i class="fa-brands fa-bilibili"></i> 漓翎_cub <i class="fa-solid fa-arrow-up-right ml-[0.2em] font-light align-text-top text-[0.7em] link-icon"></i></a>设计并制作
- **大部分**为动态图标
- 支持 **24 / 32 / 48 / 64 / 96 / 128 / 192 / 256 / 512** 多分辨率

## 适用平台

- [GNU](https://www.gnu.org/)/[Linux](https://kernel.org/) 平台所有支持 [XDG 主题包](https://specifications.freedesktop.org/icon-theme/latest/)的桌面环境

{% note regular %}
在 [KDE Plasma](https://kde.org/plasma-desktop/)、[GNOME](https://www.gnome.org/) 通过测试，表现良好。
{% endnote %}

## 安装方式

{% tabs installation %}
<!-- tab Arch Linux -->
- 使用 AUR 助手
  ```bash
  paru -S hei-cursors-git
  ```
  **或**选择其他您喜欢的 AUR 助手：
  ```bash
  yay -S hei-cursors-git
  ```
- 手动安装 AUR 包
  ```bash
  sudo pacman -S --needed base-devel
  git clone https://aur.archlinux.org/hei-cursors-git.git
  cd hei-cursors-git
  makepkg -si
  ```
<!-- endtab -->
<!-- tab 其他发行版（手动安装） -->
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
                    ```bash
                    sudo apt update
                    sudo apt install git
                    ```
                </li>
                <li>
                    Fedora
                    ```bash
                    sudo dnf install git
                    ```
                </li>
                <li>
                    Arch Linux
                    ```bash
                    sudo pacman -S git
                    ```
                </li>
            </ul>
        </p>
    </div>
</details>
2. 安装主题包
   - 为**当前用户**安装：
   ```bash
   git clone https://github.com/Tseshongfeeshur/hei-cursors.git hei_cursors
   mkdir -p ~/.local/share/icons/
   mv ./hei_cursors ~/.local/share/icons/
   ```
   - **或**为**所有用户**安装 **（不建议）**：
   ```bash
   git clone https://github.com/Tseshongfeeshur/hei-cursors.git hei_cursors
   sudo mkdir -p /usr/share/icons/
   sudo mv ./hei_cursors /usr/share/icons/
   ```
<!-- endtab -->
{% endtabs %}

## 应用方式

{% tabs application %}
 
<!-- tab KDE Plasma -->
 
1. 导航至**系统设置 → 外观和样式 → 颜色和主题 → 光标**，或：
   ```bash
   systemsettings kcm_cursortheme
   ```
2. 单击“**罗小黑**”光标样式后单击窗口右下角“**应用**”
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
                    ```bash
                    sudo apt update
                    sudo apt install gnome-tweaks
                    ```
                </li>
                <li>
                    Fedora
                    ```bash
                    sudo dnf install gnome-tweaks
                    ```
                </li>
                <li>
                    Arch Linux
                    ```bash
                    sudo pacman -S gnome-tweaks
                    ```
                </li>
            </ul>
        </p>
    </div>
</details>
2. 导航至**优化 → 外观 → 光标**
3. 单击下拉菜单，选择“**Hei_cursor**”光标样式
4. 选择观感舒适的光标大小：
   ```bash
   gsettings set org.gnome.desktop.interface cursor-size $px
   # 将“$px”改为您需要的像素值，如 48
   ```
 
<!-- endtab -->
<!-- tab 其他桌面环境 -->
由于桌面环境 / 窗口管理器种类繁多，请查看其他平台对应文档，恕不一一赘述。
<!-- endtab -->
{% endtabs %}

## 鸣谢

- 原作者 <a href="https://space.bilibili.com/1013625945"><i class="fa-brands fa-bilibili"></i> 漓翎_cub <i class="fa-solid fa-arrow-up-right ml-[0.2em] font-light align-text-top text-[0.7em] link-icon"></i></a>，没有他的付出，就没有这个项目
- `xorg-xcursorgen`，它为多分辨率图标的生成提供了很便捷的方式
