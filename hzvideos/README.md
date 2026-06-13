# 主动呈现训练营发布包

生成日期：2026-06-13

## 内容

- `index.html`：微信/COS 可访问的手机滑动播放页，当前视频静音自动播放。
- `videos/`：已上线视频文件，共 4 / 24 集。
- `covers/`：视频封面。
- `video-manifest.json`：发布清单，记录标题、分类、源文件和上线状态。

## 数据来源

页面数据来自 `../video-data.json`。构建脚本不会自动扫描素材目录，也不会自动复制视频或封面。

## 重新生成

```bash
node scripts/build-publish-page.mjs
```

如需生成“转发 HTML 文件也能加载视频”的版本，请在上传 COS 后填入真实 HTTPS 地址：

```bash
COS_BASE_URL=https://你的域名/路径 node scripts/build-publish-page.mjs
```

## 腾讯云 COS 设置

- 上传 `publish/` 目录内全部文件，保持目录结构不变。
- `index.html` 的 Content-Type 设置为 `text/html; charset=utf-8`。
- `videos/*.mp4` 的 Content-Type 设置为 `video/mp4`。
- 微信里优先发送 COS 的 HTTPS 页面链接；单独转发 HTML 文件时，必须先用真实 `COS_BASE_URL` 重新生成。
