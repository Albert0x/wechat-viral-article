# 微信公众号排版交付

个人订阅号无法调用微信的草稿/群发接口，所以"发布"的最佳形态是：**生成一个带内联样式的 HTML 文件，用户在浏览器里全选复制，粘贴进公众号编辑器**，排版会被完整保留。

## 工作方式

写完文章后，除了在对话里输出正文，**额外用 Write 工具生成一个 HTML 文件**（文件名用文章主标题，如 `最先撑不住的，往往是最懂事的那个.html`），然后告诉用户：

> 已生成排版文件：`<文件名>.html`。用浏览器打开它 → Ctrl+A 全选 → Ctrl+C → 粘进公众号编辑器即可，排版会保留。封面图请自行上传。

## 关键原则

1. **样式必须写成内联 `style=""`**。微信会丢弃 `<style>` 标签和 class，只认内联样式。
2. **不要用外部图片/字体**。封面图由用户在后台单独传。
3. **整体包在一个 `<section>` 里**，便于一次性全选。
4. 配色克制：正文深灰（不用纯黑），金句用一个主题色点缀即可。

## HTML 模板（按文章内容填充，样式照搬）

```html
<section style="font-family: -apple-system, 'PingFang SC', 'Microsoft YaHei', sans-serif; font-size: 16px; color: #3f3f3f; line-height: 1.8; letter-spacing: 0.5px; padding: 0 2px;">

  <!-- 题记（可选）-->
  <p style="text-align: center; color: #888; font-size: 14px; font-style: italic; margin: 0 0 28px;">你那么好说话，是因为没人替你说话。</p>

  <!-- 正文段落：每段用一个 p，段间距靠 margin 控制 -->
  <p style="margin: 0 0 20px;">上周有个读者，半夜十一点多给我发消息。</p>

  <p style="margin: 0 0 20px;">她说她在单位算是公认那种"特别好相处"的人。</p>

  <!-- 小标题（01 / 02 / 03）-->
  <p style="text-align: center; font-size: 18px; font-weight: bold; color: #c0392b; margin: 36px 0 22px;">01</p>

  <p style="margin: 0 0 20px;">懂事的人，最容易被当成空气一样的存在。</p>

  <!-- 金句：居中、加粗、主题色，方便截图 -->
  <p style="text-align: center; font-weight: bold; color: #c0392b; font-size: 17px; margin: 28px 0;">你越好说话，别人越不会把你的为难当回事。</p>

  <!-- 分隔符 ▽ -->
  <p style="text-align: center; color: #bbb; margin: 32px 0;">▽</p>

  <!-- 结尾引导 -->
  <p style="margin: 0 0 20px;">点个赞，愿你往后，懂事，但不再委屈。</p>

</section>
```

## 样式速查

| 元素 | 内联样式要点 |
|---|---|
| 容器 section | `font-size:16px; color:#3f3f3f; line-height:1.8; letter-spacing:0.5px` |
| 正文段落 p | `margin:0 0 20px`（靠下边距制造段间留白） |
| 题记 | 居中、灰色 `#888`、14px、斜体 |
| 小标题 01/02 | 居中、加粗、主题色、`margin:36px 0 22px` |
| 金句 | 居中、加粗、主题色 `#c0392b`、17px、上下 `margin:28px` |
| 分隔符 ▽ | 居中、浅灰 `#bbb` |

主题色可按调性换：温和治愈用暖橙 `#e67e22`，犀利通透用红 `#c0392b`，AI 选题用蓝 `#2980b9`。

## 如果将来升级成企业号/服务号（自动发布到草稿箱）

届时可写一个本地脚本调用微信「新增草稿」接口（需要 AppID/AppSecret，密钥存本地、勿上传 GitHub）：
- 获取 access_token：`GET https://api.weixin.qq.com/cgi-bin/token`
- 上传封面图为永久素材：`POST .../cgi-bin/material/add_material?type=image`
- 新增草稿：`POST .../cgi-bin/draft/add`（提交 title/content/thumb_media_id 等）

注意：草稿接口只能把文章送进后台草稿箱，最终群发仍需在后台手动点。
