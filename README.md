# auto_mouse
Implement Full Functions of AutoMouse Automatic Operation Tool
mplement Full Functions of AutoMouse Automatic Operation Tool
Permission Management: Automatically detect and obtain administrator privileges
Recording Function: Support recording of left mouse button clicks and all keyboard keys, with operation time intervals logged
Playback Function: Precisely replicate operations in the recorded sequence, with configurable playback times
Shortcut Key Support: Ctrl+Shift+F7 to start/pause recording; Ctrl+Shift+F9 to stop recording/playback
Stop Mechanism: Support immediate exit during playback at any time
Logging System: Dual assurance with terminal output and file logging
Stability: Dual keyboard monitoring mechanism ensures reliable capture of keyboard events
Compatibility: Support recording and playback of various special keys and regular keys
# AutoMouse 自动操作工具

AutoMouse是一个功能强大的自动化操作工具，能够录制和回放鼠标和键盘操作，适用于需要批量执行重复性任务的场景。

## 功能特性

### 核心功能
- **权限管理**：自动检测管理员权限，如无则自动以管理员权限重新启动
- **录制功能**：
  - 支持鼠标左键点击坐标录制
  - 支持所有键盘按键录制（普通键和特殊键）
  - 记录每步操作的时间间隔，还原手动操作节奏
  - 录制前倒计时提示，给用户准备时间
  - 终端实时打印录制日志和状态
- **回放功能**：
  - 可配置回放次数（默认5次）
  - 回放前倒计时提示，方便用户切换窗口
  - 按录制的操作序列精准复刻，还原操作时间间隔
  - 终端实时打印回放进度和操作信息
- **稳定性与容错**：
  - 双重键盘监听机制，确保可靠捕获键盘事件
  - 操作间默认延时（0.2秒，可配置）
  - 支持回放过程中随时退出
  - 使用Windows API进行鼠标点击，提高可靠性
- **日志功能**：
  - 终端实时输出不同级别日志（INFO/WARNING/ERROR）
  - 自动生成日志文件，保存所有操作记录
  - 记录程序启动/退出、录制状态、回放进度、异常信息等

### 支持的按键
- 所有字母键（A-Z）
- 所有数字键（0-9）
- 方向键（上、下、左、右）
- 功能键（Enter、Backspace、Space、ESC等）

## 安装步骤

1. 确保已安装Python 3.7或更高版本
2. 安装依赖包：

```bash
pip install -r requirements.txt
```

依赖包包括：
- pyautogui：用于鼠标和键盘操作
- keyboard：用于键盘事件监听
- pynput：作为备用键盘事件监听机制
- pywin32：用于Windows API调用

## 使用方法

### 基本流程
1. 运行程序：

```bash
python auto_mouse.py
```

2. 程序会自动以管理员权限启动
3. 按 `Ctrl+Shift+F7` 开始录制（8秒倒计时）
4. 手动完成一次操作流程
5. 按 `Ctrl+Shift+F9` 停止录制
6. 程序自动开始回放（8秒倒计时）
7. 重复录制的操作指定次数
8. 回放完成后，程序继续等待新的操作指令

### 快捷键说明
| 快捷键 | 功能 |
|--------|------|
| Ctrl+Shift+F7 | 开始/暂停录制 |
| Ctrl+Shift+F9 | 停止录制/回放（回放过程中按此键可随时退出） |

## 配置选项

在 `auto_mouse.py` 文件中可以修改以下配置：

```python
# 配置回放次数
self.playback_count = 5  # 默认回放5次

# 配置操作间默认延时
self.default_delay = 0.2  # 默认延时0.2秒
```

## 注意事项

1. 请确保在录制前关闭所有可能干扰的程序
2. 录制和回放时，请保持目标窗口位置不变
3. 某些安全软件可能会阻止自动化操作，请暂时关闭或添加例外
4. 长时间运行可能会导致系统资源占用增加，建议定期重启程序
5. 如遇到快捷键不响应的情况，请尝试重新启动程序

## 故障排除

### 键盘操作无法录制
- 确保程序以管理员权限运行
- 检查是否有其他程序占用了相同的快捷键
- 尝试重新启动程序

### 回放不准确
- 确保录制和回放时目标窗口位置完全一致
- 调整操作间默认延时（增大`self.default_delay`值）

### 程序崩溃或无响应
- 查看`auto_download_log.log`文件获取详细错误信息
- 尝试关闭其他占用系统资源较多的程序
- 重启计算机后重新运行

## 适用场景

- 批量下载文件
- 重复性数据录入
- 自动化测试
- 批量处理文档
- 其他需要重复执行相同键鼠操作的场景

## 许可证

本项目采用MIT许可证，可自由使用和修改。

## 更新日志

### v1.0.0 (2026-03-20)
- 初始版本发布
- 实现完整的录制和回放功能
- 支持所有键盘按键录制
- 双重键盘监听机制确保稳定性
- 完善的日志系统
- 友好的用户交互提示
