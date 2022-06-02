# 多语种翻译插件
基于 [NoneBot2](https://github.com/nonebot/nonebot2)。
## 前言
接口来自 [腾讯机器翻译 TMT](https://cloud.tencent.com/product/tmt) 目前使用 [签名方法 v1](https://cloud.tencent.com/document/api/213/15692#.E4.BD.BF.E7.94.A8.E7.AD.BE.E5.90.8D.E6.96.B9.E6.B3.95-v1-.E7.9A.84.E5.85.AC.E5.85.B1.E5.8F.82.E6.95.B0)
## 准备工作
- 在 [云API密钥](https://console.cloud.tencent.com/capi) 新建密钥，取得 `SecretId` 和 `SecretKey`
- 打开 [机器翻译控制台](https://console.cloud.tencent.com/tmt) 确认是否能正常看到概览页面
  > 若提示没有完成实名认证，则需要完成才能继续和正常使用
## 开始使用
建议使用 poetry
- 通过 poetry 添加到 NoneBot2 项目的 pyproject.toml
```cmd
poetry add nonebot-plugin-translator
```
- 也可以通过 pip 从 [PyPI](https://pypi.org/project/nonebot-plugin-translator/) 安装
```cmd
pip install nonebot-plugin-translator
```
- 参照下文在 NoneBot2 项目的环境文件 `.env.*` 中添加配置项
## 配置项
腾讯云 API 请求的公共参数（必须）

- ***tencentcloud_common_region `str`***  
  &nbsp;&nbsp;&nbsp;&nbsp;[地域参数](https://cloud.tencent.com/document/api/551/15615#.E5.9C.B0.E5.9F.9F.E5.88.97.E8.A1.A8)，用来标识希望操作哪个地域的数据  
- ***tencentcloud_common_secretid `str`***  
  &nbsp;&nbsp;&nbsp;&nbsp;在 [云API密钥](https://console.cloud.tencent.com/capi) 上申请的标识身份的 `SecretId`，一个 `SecretId` 对应唯一的 `SecretKey`  
- ***tencentcloud_common_secretkey `str`***  
  &nbsp;&nbsp;&nbsp;&nbsp;你的 `SecretKey` 用来生成请求签名 Signature
```python
# .env.prod
tencentcloud_common_region = "ap-shanghai"
tencentcloud_common_secretid = ""
tencentcloud_common_secretkey = ""
```
这样，就能够在 Bot 所在群聊或私聊发送 `翻译` 或 `机翻` 使用了
## 常见问题
- ***我确认我的安装和配置过程正确，但我发送 ``翻译`` 或 ``机翻`` 没有反应***  
  &nbsp;&nbsp;&nbsp;&nbsp;如果在 ``.env.*`` 的 ``command_start`` 内仅设置了非空前缀，就必须在命令前加上前缀，比如 ``/翻译`` ``/机翻``
## 特别感谢
- [Mrs4s / go-cqhttp](https://github.com/Mrs4s/go-cqhttp)
- [nonebot / nonebot2](https://github.com/nonebot/nonebot2)
## 优化建议
请积极提交 Issues 或 Pull requests