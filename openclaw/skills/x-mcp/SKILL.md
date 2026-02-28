---
name: x-mcp
description: "小红书全能助手：支持账号状态检查、搜索笔记、生成封面、获取详情及发布图文/视频。"
---

# 小红书自动化工具集

通过 mcporter 桥接 aredink.com 提供的 MCP 服务。

## xhs_check_login_status
检查当前小红书账号的登录状态。

### 运行
```bash
npx mcporter x-mcp.xhs_check_login_status
```

## xhs_search_feeds

搜索小红书内容。

### 参数

* `keyword`: (required) 搜索关键词。
* `sort`: (optional) 排序方式：general(综合), popularity(热门), time(最新)。

### 运行

```bash
npx mcporter x-mcp.xhs_search_feeds --keyword "{{keyword}}" --sort "{{sort}}"
```

## xhs_get_recommend_feeds

获取小红书首页推荐内容流。

### 运行

```bash
npx mcporter x-mcp.xhs_get_recommend_feeds
```

## xhs_get_feed_detail

获取小红书笔记详情，包括内容、图片、作者及评论。

### 参数

* `feedId`: (required) 笔记 ID。
* `xsecToken`: (required) 访问令牌（从 Feed 列表获取）。

### 运行

```bash
npx mcporter x-mcp.xhs_get_feed_detail --feedId "{{feedId}}" --xsecToken "{{xsecToken}}"
```

## xhs_generate_cover

生成小红书封面图并返回 URL。

### 参数

* `title`: (required) 主标题文字。
* `subtitle`: (required) 副标题文字。
* `template`: (required) 模板样式：modern, minimal, pixel。
* `description`: (optional) 描述文字。
* `emoji`: (optional) 要显示的 emoji 表情。

### 运行

```bash
npx mcporter x-mcp.xhs_generate_cover --title "{{title}}" --subtitle "{{subtitle}}" --template "{{template}}" --description "{{description}}" --emoji "{{emoji}}"
```

## xhs_publish_content

发布图文笔记，支持定时。

### 参数

* `title`: (required) 标题（最多20个字）。
* `content`: (required) 正文内容。
* `images`: (required) 图片列表（Array），支持 URL、Base64 或本地路径。
* `tags`: (optional) 话题标签列表，如 ["美食", "穿搭"]。
* `schedule_at`: (optional) 定时发布时间（ISO 格式）。

### 运行

```bash
npx mcporter x-mcp.xhs_publish_content --title "{{title}}" --content "{{content}}" --images "{{images}}" --tags "{{tags}}" --schedule_at "{{schedule_at}}"
```

## xhs_publish_video

发布视频笔记。

### 参数

* `title`: (required) 视频标题。
* `content`: (required) 视频描述。
* `video_url`: (optional) 视频 URL 地址。
* `tags`: (optional) 话题标签列表。
* `schedule_at`: (optional) 定时发布时间。

### 运行

```bash
npx mcporter x-mcp.xhs_publish_video --title "{{title}}" --content "{{content}}" --video_url "{{video_url}}" --tags "{{tags}}"
```

## xhs_post_comment

发表评论到指定笔记。

### 参数

* `feedId`: (required) 笔记 ID。
* `xsecToken`: (required) 访问令牌。
* `content`: (required) 评论内容。

### 运行

```bash
npx mcporter x-mcp.xhs_post_comment --feedId "{{feedId}}" --xsecToken "{{xsecToken}}" --content "{{content}}"
```
