# zjuaas.github.io

浙江大学新加坡校友会官网（[zju.sg](https://zju.sg)）

网站为纯静态页面，所有内容集中在 `index.html`，通过 GitHub Pages 自动部署。推送到 `main` 分支后，几分钟内线上即可生效。

---

## 如何维护网站内容

### 1. 添加新活动

在 `index.html` 的"近期活动"区域（`<section id="recent-events">`）添加新的 `<li>` 条目。

以下为一个活动条目的模板：

```html
<li class="list-group-item">
  <a class="event-title" data-bs-toggle="collapse" href="#eventN" role="button" aria-expanded="false" aria-controls="eventN">
    活动标题
  </a>
  <div class="collapse" id="eventN">
    <div class="mt-3">
      <p>活动简介文字……</p>
    </div>
    <!-- 可选：外部链接 -->
    <p>
      <a class="event-link" href="链接URL" target="_blank">活动图册</a>
    </p>
    <!-- 可选：图片展示 -->
    <div class="mt-2 d-flex flex-wrap">
      <img src="./event_YYYYMMDD/1.jpg" class="img-fluid me-2 mb-2" style="width: 30%;" />
    </div>
  </div>
</li>
```

**注意：** 将 `eventN` 中的 `N` 替换为不重复的编号（如 `event4`、`event5`）。

活动图片建议放在独立子目录中，命名规则：`event_YYYYMMDD/`（如 `event_20251201/`）。

---

### 2. 更新组织架构

在 `index.html` 的"组织架构"区域（`<section id="org-chart">`）修改表格内容。

- 修改人员姓名时，直接编辑对应 `<td>` 中的文本。
- 更新日期记录在表格上方的 `<p>` 标签中，格式：`（更新于YYYY年M月D日）`。

---

### 3. 更换首页轮播图

轮播图在 `<section id="index">` 内的 `<div id="homepageCarousel">` 中。

添加或替换图片：
1. 将新图片文件放到项目根目录。
2. 在 `.carousel-inner` 中添加一个 `<div class="carousel-item">`：
   ```html
   <div class="carousel-item">
     <img src="./新图片.jpg" class="d-block w-100 img-fluid" alt="图片描述" />
   </div>
   ```
3. 在 `.carousel-indicators` 中同步添加一个 `<button>` 指示点，`data-bs-slide-to` 值与图片顺序对应（从 0 开始）。

---

### 4. 更新其他文字内容

| 内容 | 对应区域 ID |
|------|------------|
| 校友会简介 | `#history` |
| 会员章程 | `#member-rules` |
| 会员申请说明 | `#application` |
| 赞助信息 | `#sponsorship` |

直接在 `index.html` 中找到对应 `<section id="...">` 标签，修改其中的文字即可。

---

### 5. 添加或更换图片文件

- 组织成员头像放在 `comittee_profile/` 目录下。
- 活动图片放在 `event_YYYYMMDD/` 目录下。
- Logo 等品牌图片直接放在根目录。

图片建议压缩后上传，推荐使用 WebP 或质量 ≤ 85% 的 JPEG，以保证页面加载速度。

---

## 部署

推送到 `main` 分支即可自动发布，无需额外操作：

```bash
git add .
git commit -m "update content"
git push
```

域名 `zju.sg` 通过 `CNAME` 文件指向 GitHub Pages，DNS 已配置完毕，无需改动。
