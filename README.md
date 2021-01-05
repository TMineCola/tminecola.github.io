# My Blog | TMineCola.github.io

[![Build Status](https://travis-ci.org/TMineCola/tminecola.github.io.svg?branch=src)](https://travis-ci.org/TMineCola/tminecola.github.io)

[![Lastest Commit](https://img.shields.io/github/last-commit/TMineCola/tminecola.github.io/src)](https://img.shields.io/)

## 關於 Hugo

網站的 Slogan 宣稱是 "The world’s fastest framework for building websites"，以 Go 語言開發的靜態網站生成套件，個人覺得生態系蠻完整的，有另一個類似的套件 [Hexo](https://hexo.io/) 是由台灣人 [Tommy Chen](https://github.com/tommy351) 以 Node.js 開發，供各位參考，之所以採用 Hugo 純粹因為主題剛好有我喜歡的風格

### Hugo 指令
> 安裝參考 [Install Hugo](https://gohugo.io/getting-started/installing/)

使用 `hugo [command]` 來使用 hugo 相關功能

```
  check       一些驗證性檢查
  config      顯示目前網站設定檔內容
  convert     可以將檔案轉換成 YAML/JSON/TOML 格式
  env         顯示 Hugo 版本與環境資訊
  gen         產生官方說明文件
  help        查看詳細的指令清單
  import      匯入網站
  list        列出文章
  new         新增文章
  server      在本機建立一個 Web Server 即時預覽目前的網站 
  version     顯示 Hugo 目前的版本
```

## 使用筆記

### 網站設定 (依據主題)
> [Reference](https://github.com/kakawait/hugo-tranquilpeak-theme/blob/master/docs/user.md#tranquilpeak-configuration)

### 文章

#### 文章選單顯示

- 自動尋找縮圖 (預設會使用 Cover (封面) 或第一章圖片作為縮圖, Default: `true`)
    ```
    autoThumbnailImage: true/false
    ```
- 縮圖擺放在文章選單的位置
    ```
    thumbnailImagePosition: top/bottom/left/right
    ```
- 縮圖圖片路徑
    ```
    thumbnailImage: /path/to/image
    ```

#### 文章內容標記

```
title: 標題
date: 建立日期
modified: 最後修改日期 (Note: 這是我自己新增的)
categories:
- 分類 (\<meta property="article:section" content="分類"\>)
tags:
- 標籤 (\<meta property="article:tag" content="標籤"\>)
keywords:
- 關鍵字 (\<meta name="keywords" content="關鍵字"\>)
```

#### 文章內容設定

##### 封面

- 封面圖片路徑
    ```
    coverImage: /path/to/image
    ```
- 封面標題
    ```
    coverCaption: 標題 (顯示在封面下方的註腳)
    ```
- 標題位置
    ```
    coverMeta: in (封面中) / out (封面下方)
    ```
- 封面大小
    ```
    coverSize: partial (60% 螢幕高度) / full (滿版)
    ```

##### 標題與摘要

- 標題對齊的方式 (外面文章列表)
    ```
    metaAlignment: left/right/center
    ```
- 文章摘要 (與內文的 `<!-- more -->` 擇一使用，使用 summary 並不會顯示在內文當中)
    ```
    summary: 摘要內容
    ```

##### 功能

- 清晰閱讀模式 (會以設定檔中的 params.clearReading 為預設，側邊攔模式 sidebarBehavior = 3 or 4 時無效)
    ```
    clearReading: true/false
    ```

- 顯示日期
    ```
    showDate: true/false
    ```
- 顯示回應
    ```
    comments: true/false
    ```
- 顯示標籤 (文末)
    ```
    showTags: true/false
    ```
- 顯示分頁按鈕 (上一篇/下一篇)
    ```
    showPagination: true/false
    ```
- 顯示社群按鈕 (臉書/Twitter分享)
    ```
    showSocial: true/false
    ```
- 顯示 Meta 資料 (日期/分類/閱讀時間)
    ```
    showMeta: true/false
    ```
- 顯示分頁及社群按鈕等可操作元件
    ```
    showActions: true/false
    ```
- 畫廊模式 (文末會以畫廊的方式顯示圖片)
    ```
    gallery:
    - 原始圖片 URL [縮圖 URL] [標題]
    ```


### 內容格式

#### 摘要與目錄

- 摘要 (並且會成為 SEO 的 description)
    ```
    <!--more-->
    ```

- Table of content 顯示標題連結表
    ```
    <!-- toc -->
    ```


#### 特殊顯示
> [展示頁面](https://tranquilpeak.kakawait.com/2014/10/tags-plugins-showcase/) 搭配 [原始 mardown 格式](https://raw.githubusercontent.com/kakawait/hugo-tranquilpeak-theme/master/exampleSite/content/post/Tags-plugins-showcase.md)

- 提示標記 (info 藍、success 綠、warning 黃、danger 紅)
    ```
    {{< alert info >}}
    Praesent diam elit, interdum ut pulvinar placerat, imperdiet at magna.
    {{< /alert >}}
    ```

- 引言
    ```
    一般引言
        > Praesent diam elit, interdum ut pulvinar placerat, imperdiet at magna.

    書本引言
        {{< blockquote "作者" "書名" >}}
        Do not just seek happiness for yourself. Seek happiness for all. Through kindness. Through mercy.
        {{< /blockquote >}}

    推特引言
        {{< blockquote "@作者" "來源連結" >}}
        NEW: DevDocs now comes with syntax highlighting. //devdocs.io
        {{< /blockquote >}}

    文章引言
        {{< blockquote "作者" "文章連結" "標題" >}}
        Every interaction is both precious and an opportunity to delight.
        {{< /blockquote >}}
    ```

- 程式碼區塊

    ```
    一般程式碼
        ```js
        alert('Hello World!');
        ```
    
    具有標題
        {{< codeblock "區塊標題" >}}
        alert('Hello World!');
        {{< /codeblock >}}

    具有標題及連結
        {{< codeblock "區塊標題" "標記(似乎不顯示)" "連結" "連結標題" >}}
        alert('Hello World!');
        {{< /codeblock >}}

    ```
- [Gist tag](https://hexo.io/docs/tag-plugins.html#Gist)
- [Image tag](https://github.com/kakawait/hugo-tranquilpeak-theme/blob/master/docs/user.md#image)
- [jsFiddle tag](https://hexo.io/docs/tag-plugins.html#jsFiddle)
- 內嵌註解 (left/right)
    ```
    {{< pullquote left >}}
    Left Quote Example
    {{< /pullquote >}}
    ```
- HighLight [顏色參考](https://github.com/kakawait/hugo-tranquilpeak-theme/blob/master/docs/user.md#highlight-text)
    ```
    {{< hl-text red >}}highlight red{{< /hl-text >}}
    ```
- 分頁程式碼區塊
    ```
    {{< tabbed-codeblock tabbed_codeblock >}}
        <!-- tab html -->
        HTML 內容
        <!-- endtab -->
        <!-- tab js -->
        JS 內容
        <!-- endtab -->
    {{< /tabbed-codeblock >}}
    ```
- 內嵌 Youtube 影片
    ```
    {{< youtube 影片ID >}}
    ```
- 滿版圖片
    ```
    {{< wide-image src="/path/to/image" title="圖片標題" >}}
    ```