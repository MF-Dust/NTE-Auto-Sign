# NTE Auto Sign（塔吉多 / 异环）

NTE Auto Sign 是一个塔吉多（异环）自动签到工具，支持短信/refreshToken 登录、多账号管理与切换、社区+游戏签到、奖励日志输出，并提供 `nte.exe` 与 `add_account.exe` 便捷使用。

## 功能特性

- 手机号 + 短信验证码登录
- 手机号 + 密码登录
- `refreshToken` 登录（高级模式）
- 多账号保存到 `TOKEN.txt`（每行一个账号）
- 运行时手动选择账号（单选 / 多选 / 全部）
- 社区签到 + 游戏签到
- 签到结果与奖励日志输出（`logs\YYYY-MM-DD.log`）

## 快速开始（Python）

1. 安装依赖

```bash
pip install -r requirements.txt
```

2. 添加账号（支持连续添加）

```bash
python add_account.py
```

3. 执行签到

```bash
python nte.py
```

## 账号文件（TOKEN.txt）

`TOKEN.txt` 每行一个账号，推荐使用 JSON：

```json
{"refreshToken":"xxx","uid":"10xxxx","deviceId":"xxxxx","gameId":"1289","roleIds":["2160xxxxxxx"]}
```

## 多账号选择

当 `TOKEN.txt` 中有多个账号时，`nte.py` 会提示选择：

- `1`：只签到第 1 个账号
- `1,3`：签到第 1 和第 3 个账号
- 回车 / `all` / `a`：签到全部账号

## Windows EXE 使用

预编译文件位于 `dist\windows\`：

- `nte.exe`：签到主程序
- `add_account.exe`：账号添加工具

双击即可运行。

## 环境变量

| 变量 | 说明 |
| --- | --- |
| `TOKEN` | 账号信息（支持多行，格式同 `TOKEN.txt`） |
| `TGD_GAME_ID` | 默认游戏 ID（默认 `1289`） |
| `TGD_ROLE_IDS` | 角色 ID（逗号分隔，补充/覆盖自动拉取） |
| `TGD_SIGN_GAME_IDS` | 签到时尝试的 gameId 列表（逗号分隔） |
| `EXIT_WHEN_FAIL=on` | 任一账号失败时，进程退出码为 1 |
| `NO_PAUSE=1` | Windows 下失败时不等待回车 |
| `SKYLAND_TYPE=add_account` | 仅添加账号，不执行签到 |

## 常见问题

- `refreshToken 已失效`：删除 `TOKEN.txt` 后重新登录并添加账号。

## 致谢

本项目基于 skyland-auto-sign 修改：  
https://gitee.com/FancyCabbage/skyland-auto-sign

## 演示图片

![演示图 1](assets/1.png)
![演示图 2](assets/2.png)
![演示图 3](assets/3.png)
