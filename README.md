# Qdriver-python

电赛云台视觉跟踪上位机：矩形检测 + PID，经串口驱动 STM32 云台。

配套仓库：

- 固件：[QGimbal-master-stm32f4](https://github.com/CameliaDev/QGimbal-master-stm32f4)
- 视觉库：[QGimbal-Vision-master-python](https://github.com/CameliaDev/QGimbal-Vision-master-python)

## 硬件（参考）

- 树莓派 + USB 摄像头（固定，不在云台上）
- STM32F407 大疆 C 板云台（示例：`/dev/ttyAMA0`，115200 8N1）

## 安装

```bash
pip install -r requirements.txt
# 若复用上游 vision/control 包，请把 QGimbal-Vision 仓库放在旁路路径，
# 或设置 PYTHONPATH 指向该仓库根目录（main.py 内有历史相对路径兼容逻辑）。
```

## 快速开始

```bash
# 纯检测（不控云台）
DISPLAY=:0 python main.py

# 跟踪 + 云台
bash run.sh
```

## 常用命令

```bash
DISPLAY=:0 python main.py --serial-port /dev/ttyAMA0
python reset_gimbal.py
DISPLAY=:0 python debug_detect.py
```

## 文件说明

| 文件 | 用途 |
|------|------|
| `main.py` | 主程序：检测 + PID + 串口 |
| `gimbal_commands.py` | 云台串口协议封装 |
| `debug_detect.py` / `detect_headless.py` | 检测调试 |
| `reset_gimbal.py` | 归零 |
| `run.sh` | 一键启动 |
| `main01.py` | **学习用 stub**：拍一张照片存到 `cermal/`（非主路径） |
| `official_*.py` | 官方 UART / HEX 参考 |

## License

MIT © 2026 CameliaDev