# 小红书链接提取器

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.6%2B-brightgreen.svg)
![Platform](https://img.shields.io/badge/platform-macOS-lightgrey.svg)

一个简单实用的Mac工具，可以自动从复制的小红书分享文本中提取链接，让你快速打开小红书内容而不需要安装App。
！
安装成功后的使用方式：手机端点击帖子的 "复制链接“，mac会立即打开 chrome 浏览器并且复制和进入链接的网页。非常适合有时候需要把小红书帖子放在电脑网页整理的朋友

## 功能特点

- ✅ 自动监听剪贴板变化
- ✅ 智能识别并提取小红书分享文本中的链接
- ✅ 自动将提取的链接复制回剪贴板
- ✅ 可选择自动在Chrome中打开链接
- ✅ 支持命令行和GUI两种使用方式
- ✅ 可设置为开机自动启动

## 快速安装

### 方法一：使用安装脚本（推荐）

1. 克隆仓库到本地：
   ```bash
   git clone https://github.com/你的用户名/xiaohongshu-link-extractor.git
   cd xiaohongshu-link-extractor
   ```

2. 运行安装脚本：
   ```bash
   chmod +x install.sh
   ./install.sh
   ```

3. 按照提示完成安装

### 方法二：手动安装

1. 确保你的Mac上已安装Python 3
2. 克隆仓库到本地：
   ```bash
   git clone https://github.com/你的用户名/xiaohongshu-link-extractor.git
   cd xiaohongshu-link-extractor
   ```

3. 给脚本添加执行权限：
   ```bash
   chmod +x rednote_cleaner.py
   chmod +x rednote_cleaner_gui.py
   ```

## 使用方法

### 命令行版本

```bash
./rednote_cleaner.py [--auto-open] [--interval 秒数]
```

参数说明：
- `--auto-open`：自动在Chrome中打开提取的链接
- `--interval`：设置检查剪贴板的时间间隔，默认为0.5秒

### GUI版本

```bash
./rednote_cleaner_gui.py
```

在GUI界面中：
- 点击"开始监听"按钮开始监听剪贴板
- 勾选"自动在Chrome中打开链接"选项可以自动打开提取的链接
- 在"最近提取的链接"区域可以查看和手动打开链接
- 日志区域显示程序的运行状态

## 使用示例

1. 运行小红书链接提取器
2. 复制小红书分享文本，例如：
   ```
   8 AI momo发布了一篇小红书笔记，快来看吧！ 😆 CpZNsTZQPG1hzGt 😆 http://xhslink.com/m/17KSsrEFyED 复制本条信息，打开【小红书】App查看精彩内容！
   ```
3. 小红书链接提取器会自动提取链接 `http://xhslink.com/m/17KSsrEFyED` 并复制到剪贴板
4. 如果启用了自动打开功能，Chrome会自动打开该链接

## 设置为开机启动

### 使用安装脚本

运行安装脚本时，会询问是否将小红书链接提取器设置为开机启动。

### 手动设置

#### 命令行版本

1. 创建一个plist文件在 `~/Library/LaunchAgents/com.user.rednotecleaner.plist`：
   ```xml
   <?xml version="1.0" encoding="UTF-8"?>
   <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
   <plist version="1.0">
   <dict>
       <key>Label</key>
       <string>com.user.rednotecleaner</string>
       <key>ProgramArguments</key>
       <array>
           <string>/完整路径/到/rednote_cleaner.py</string>
           <!-- 如果需要自动打开Chrome，添加下面这行 -->
           <!-- <string>--auto-open</string> -->
       </array>
       <key>RunAtLoad</key>
       <true/>
       <key>KeepAlive</key>
       <true/>
   </dict>
   </plist>
   ```

2. 替换 `/完整路径/到/rednote_cleaner.py` 为实际脚本路径

3. 加载LaunchAgent：
   ```bash
   launchctl load ~/Library/LaunchAgents/com.user.rednotecleaner.plist
   ```

#### GUI版本

对于GUI版本，你可以将应用添加到登录项：

1. 系统偏好设置 > 用户与群组 > 登录项
2. 点击"+"按钮
3. 找到并选择`rednote_cleaner_gui.py`文件
4. 点击"添加"

## 系统要求

- macOS系统
- Python 3.6+
- 对于GUI版本，需要tkinter库（通常Python自带）

## 常见问题

**Q: 为什么我复制了小红书链接，但工具没有反应？**

A: 请确保复制的文本中包含"小红书"、"xhslink"或"xiaohongshu"关键词，并且链接格式为http://xhslink.com/或xiaohongshu.com开头。

**Q: 如何停止程序运行？**

A: 命令行版本按Ctrl+C停止；GUI版本点击"停止监听"按钮或关闭窗口。

## 贡献指南

欢迎提交Pull Request或Issue来改进这个工具！

## 许可证

本项目采用MIT许可证，详见[LICENSE](LICENSE)文件。 
