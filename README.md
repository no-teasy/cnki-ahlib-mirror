# 知网--安徽省图书馆镜像

[![Script Version](https://img.shields.io/badge/Script-v1.4.0-2988f5?logo=tampermonkey&logoColor=white)](https://github.com/no-teasy/cnki-ahlib-mirror/blob/main/script.user.js)
[![License](https://img.shields.io/github/license/no-teasy/cnki-ahlib-mirror?color=blue&logo=open-source-initiative)](./LICENSE)
<!-- [![Greasy Fork](https://img.shields.io/badge/Greasy_Fork-v1.0.0-F16529?logo=greasyfork)](链接) -->
[![Install Script](https://img.shields.io/badge/INSTALL%20SCRIPT-CLICK%20HERE-2988f5?style=for-the-badge&logo=tampermonkey&logoColor=white)](https://github.com/no-teasy/cnki-ahlib-mirror/raw/main/script.user.js)
> 由衷感谢安徽省图书馆提供的知网免费学术访问
>
> 初次使用请访问 [安徽省图书馆](https://opac.ahlib.com/opac/reader/login) 注册账号



## 简介

通过安徽图书馆镜像站免费访问知网下载文献

## 功能特点

- **自动重定向**：访问知网官方域名时自动跳转到安徽省图书馆镜像
- **全面链接处理**：处理页面中所有包含知网链接的元素（a标签、iframe、img、form等）
- **实时监控**：使用MutationObserver监听DOM变化，实时处理新添加的链接
- **方法拦截**：拦截`window.open`、`location.assign`和`location.replace`等方法
- **相对链接支持**：智能处理相对路径链接
- **详细日志**：提供详细的调试日志，便于排查问题
- **定时检查**：定期检查页面，确保所有链接都被正确处理

## 安装指南

### 前提条件
- 安装支持UserScript的浏览器扩展：
  - [Tampermonkey](https://www.tampermonkey.net/)（Chrome、Firefox、Edge等）
  - [Greasemonkey](https://www.greasespot.net/)（Firefox）

### 安装步骤

1. 安装上述任一用户脚本管理器扩展
2. 点击以下安装链接（推荐）：

[![Install Script](https://img.shields.io/badge/INSTALL%20SCRIPT-CLICK%20HERE-2988f5?style=for-the-badge&logo=tampermonkey&logoColor=white)](https://raw.githubusercontent.com/no-teasy/cnki-ahlib-mirror/main/script.user.js)

3. 或者手动安装：
   - 下载[script.js](https://github.com/no-teasy/cnki-ahlib-mirror/raw/main/script.user.js) 文件
   - 在用户脚本管理器中点击"创建新脚本"
   - 将下载的文件内容粘贴到编辑器中
   - 保存脚本

## 使用说明

1. 安装脚本后，当您访问知网（`*.cnki.net`）或安徽图书馆镜像站（`*.ahlib.com`）时，脚本会自动运行
2. 访问知网官方域名时，会自动重定向到安徽图书馆镜像站
3. 在安徽图书馆镜像站中，所有知网链接会自动转换为镜像站链接
4. 您可以打开浏览器控制台（F12），查看脚本运行日志（以`[知网链接重定向]`开头）

## 技术原理

脚本通过以下方式实现链接重定向：

1. **域名检测**：检测当前页面是否为知网域名或安徽省图书馆镜像域名
2. **URL转换**：
   - 将`*.cnki.net`域名转换为`*-s.ycfw.ahlib.com`格式
   - 例如：`https://m.cnki.net` → `https://m-cnki-net-s.ycfw.ahlib.com`
3. **DOM处理**：
   - 批量处理页面中所有包含知网链接的元素
   - 监听DOM变化，实时处理新添加的元素
4. **方法拦截**：
   - 重写`window.open`、`location.assign`和`location.replace`方法
   - 确保所有程序化跳转也经过重定向

## 调试信息

脚本默认开启调试模式（`DEBUG = true`），您可以在浏览器控制台查看详细日志：

- 脚本初始化信息
- 链接处理过程
- DOM变化监听详情
- URL转换前后的对比

如需关闭调试日志，可在脚本源码中将`const DEBUG = true;`改为`false`。

## 常见问题

### Q: 为什么需要这个脚本？
A: 知网资源有需要付费，安徽省图书馆提供了镜像服务，但镜像站的链接格式与原站不同，此脚本自动完成链接转换，让用户无感知地使用镜像服务。

### Q: 脚本会影响页面性能吗？
A: 脚本经过优化，只处理包含知网链接的元素，并使用高效的DOM监听机制，对页面性能影响极小。

### Q: 为什么有些链接没有被重定向？
A: 可能是以下原因：
   - 链接是通过JavaScript动态生成且未触发DOM变化事件
   - 链接格式不符合脚本处理规则
   - 页面加载速度过快，脚本尚未完全初始化
   - 可尝试刷新页面或检查控制台日志获取更多信息


## 许可证

本项目采用 [MIT 许可证](LICENSE)。

## 致谢

再次感谢安徽省图书馆提供镜像服务，使广大用户能够更便捷地访问学术资源。

---

> **注意**：本脚本仅为技术研究和学习目的开发，请遵守相关法律法规，尊重知识产权，合理使用学术资源。