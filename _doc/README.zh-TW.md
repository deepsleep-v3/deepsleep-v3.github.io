# Hux blog 模板

### [我的博客在這裡 &rarr;](http://huxpro.github.io)


### 關於收到「Page Build Warning」的 email

由於 jekyll 升級到 3.0.x，對原來的 pygments 程式碼高亮不再支援，現只支援一種 -rouge，所以你需要在 `_config.yml` 檔案中修改 `highlighter: rouge`。另外還需要在 `_config.yml` 檔案中加上 `gems: [jekyll-paginate]`。

同時，你需要更新你的本地 jekyll 環境。

使用 `jekyll server` 的同學需要這樣：

1. `gem update jekyll` # 更新 jekyll
2. `gem update github-pages` # 更新依賴的套件

使用 `bundle exec jekyll server` 的同學在更新 jekyll 後，需要輸入 `bundle update` 來更新依賴的套件。

參考文件：[using jekyll with pages](https://help.github.com/articles/using-jekyll-with-pages/) & [Upgrading from 2.x to 3.x](http://jekyllrb.com/docs/upgrading/2-to-3/)


## 關於模板 (beta)

我的部落格倉庫——`huxpro.github.io`，是經常修改的，而且還會有人亂提交程式碼，因此給大家做了一個穩定版的模板。大家可以直接 fork 模板——`huxblog-boilerplate`，要改的地方我都說明了。或者可以直接下載 zip 到本地自己去修改。

```
$ git clone git@github.com:Huxpro/huxblog-boilerplate.git
```

**[在這裡預覽模板 &rarr;](http://huangxuan.me/huxblog-boilerplate/)**

## 各版本特性

##### New Feature (V1.5.2)

* 當你 fork 了我的倉庫之後，還要刪掉裡面的關於我的文件是不是感到略煩躁呢？**Boilerplate** 模板將幫助你快速開始，方便合併與更新。
* `-apple-system` 被添加到了字型規則裡面了，這套字型格式能將 iOS9 預設的新字型 **San Francisco** 表現的非常漂亮。
* 解決了程式碼過長自動換行的 bug，替換為橫向滾動條。詳情請見 [issue#15](https://github.com/Huxpro/huxpro.github.io/issues/15)

###### 其他歷史版本個人覺得沒有必要了解，看看英文就行了。



## 支援

* 你可以自由的 fork。如果你能將主題作者和 github 的地址保留在你的頁面底部，我將非常感謝你。
* 如果你喜歡我的這個部落格模板，請在 `huxpro.github.io` 這個 repository 點個讚——右上角 **star** 一下。

## 說明文件

* 開始
	* [環境要求](#environment)
	* [開始](#get-started)
	* [寫一篇博文](#write-posts)
* 元件
	* [側邊欄](#sidebar)
	* [迷你關於我](#mini-about-me)
	* [推薦標籤](#featured-tags)
	* [好友連結](#friends)
	* [HTML5 演示文件佈局](#keynote-layout)
* 評論與 Google/Baidu Analytics
	* [評論](#comment)
	* [網站分析](#analytics) 
* 高級部分
	* [自定義](#customization)
	* [標題底圖](#header-image)
	* [搜尋展示標題 - 頭文件](#seo-title)

#### Environment

如果你安裝了 jekyll，那你只需要在命令列輸入 `jekyll serve` 就能在本地瀏覽器預覽主題。你還可以輸入 `jekyll serve --watch`，這樣可以邊修改邊自動運行修改後的檔案。

經 [@BrucZhaoR](https://github.com/BruceZhaoR) 的測試，好像兩個命令都是可以的自動運行修改後的檔案的，刷新後可以實時預覽。官方檔案是建議安裝 bundler，這樣你在本地的效果就跟在 github 上面是一樣的。詳情請見這裡：https://help.github.com/articles/using-jekyll-with-pages/#installing-jekyll


#### Get Started

你可以通用修改 `_config.yml` 檔案來輕鬆的開始搭建自己的部落格：

```
# Site settings
title: Hux Blog             # 你的部落格網站標題
SEOTitle: Hux Blog			# 在後面會詳細談到
description: "Cool Blog"    # 隨便說點，描述一下

# SNS settings      
github_username: huxpro     # 你的 github 帳號
weibo_username: huxpro      # 你的微博帳號，底部連結會自動更新的。

# Build settings
# paginate: 10              # 一頁你準備放幾篇文章
```

Jekyll 官方網站還有很多的參數可以調，比如設定文章的連結形式...網址在這裡：[Jekyll - Official Site](http://jekyllrb.com/) 中文版的在這裡：[Jekyll 中文](http://jekyllcn.com/).

#### write-posts

要發表的文章一般以 markdown 的格式放在這裡 `_posts/`，你只要看看這篇模板裡的文章你就立刻明白該如何設定。

yaml 頭檔案長這樣：

```
---
layout:     post
title:      "Hello 2015"
subtitle:   "Hello World, Hello Blog"
date:       2015-01-29 12:00:00
author:     "Hux"
header-img: "img/post-bg-2015.jpg"
tags:
    - Life
---

```

在引入 [Rake](https://github.com/ruby/rake) 工具之後，我們可以使用命令：

```
rake post title="Hello 2015" subtitle="Hello World, Hello Blog"
```

來自動生成上面的文章模板。

#### SideBar

看右邊：
![](http://huangxuan.me/img/blog-sidebar.jpg)

設定是在 `_config.yml` 檔案裡面的 `Sidebar settings` 那塊。
```
# Sidebar settings
sidebar: true  # 添加側邊欄
sidebar-about-description: "簡單的描述一下你自己"
sidebar-avatar: /img/avatar-hux.jpg     # 你的大頭貼，請使用絕對地址。
```

側邊欄是響應式佈局的，當螢幕尺寸小於 992px 的時候，側邊欄就會移動到底部。具體請見 bootstrap 柵格系統 <http://v3.bootcss.com/css/>


#### Mini About Me

Mini-About-Me 這個模組將在你的頭像下面，展示你所有的社交帳號。這個也是響應式佈局，當螢幕變小時候，會將其移動到頁面底部，只不過會稍微有點小變化，具體請看程式碼。

#### Featured Tags

看到這個網站 [Medium](http://medium.com) 的推薦標籤非常的炫酷，所以我將他加了進來。
這個模組現在是獨立的，可以呈現在所有頁面，包括主頁和發表的每一篇文章標題的頭上。

```
# Featured Tags
featured-tags: true  
featured-condition-size: 1     # A tag will be featured if the size of it is more than this condition value
```

唯一需要注意的是 `featured-condition-size`: 如果一個標籤的 SIZE，也就是使用該標籤的文章數大於上面設定的條件值，這個標籤就會在首頁上被推薦。
 
內部有一個條件模板 `{% if tag[1].size > {{site.featured-condition-size}} %}` 是用來做篩選過濾的。


#### Friends

好友連結部分。這會在全部頁面顯示。

設定是在 `_config.yml` 檔案裡面的 `Friends` 那塊，自己加吧。

```
# Friends
friends: [
    {
        title: "Foo Blog",
        href: "http://foo.github.io/"
    },
    {
        title: "Bar Blog",
        href: "http://bar.github.io"
    }
]
```


#### Keynote Layout

HTML5 幻燈片的排版：

![](http://huangxuan.me/img/blog-keynote.jpg)

這部分是用於佔用 html 格式的幻燈片的，一般用到的是 Reveal.js, Impress.js, Slides, Prezi 等等。我認為一個現代化的部落格怎麼能少了放 html 幻燈的功能呢~

其主要原理是添加一個 `iframe`，在裡面加入外部連結。你可以直接寫到頭文件裡面去，詳情請見下面的 yaml 頭文件的寫法。

```
---
layout:     keynote
iframe:     "http://huangxuan.me/js-module-7day/"
---
```

iframe 在不同的設備中，將會自動的調整大小。保留內邊距是為了讓手機用戶可以向下滑動，以及添加更多的內容。


#### Comment

部落格不僅支援多說 [Duoshuo](http://duoshuo.com) 評論系統，也支援 [Disqus](http://disqus.com) 評論系統。

`Disqus` 優點是：國際比較流行，介面也很大氣、簡介，如果有人評論，還能實時通知，直接回覆通知的郵件就行了；缺點是：評論必須要去註冊一個 disqus 帳號，分享一般只有 Facebook 和 Twitter，另外在牆內載入速度略慢了一點。想要知道長啥樣，可以看以前的版本點 [這裡](http://brucezhaor.github.io/about.html) 最下面就可以看到。

`多說` 優點是：支援國內各主流社交軟體 (微博，微信，豆瓣，QQ 空間 ...) 一鍵分享按鈕功能，另外登入比較方便，管理介面也是純中文的，相對於 disqus 全英文的要容易操作一些；缺點是：就是介面醜了一點。
當然你是可以自定義介面的 css 的，詳情請看多說開發者文件 http://dev.duoshuo.com/docs/5003ecd94cab3e7250000008 。

**首先**，你需要去註冊一個帳號，不管是 disqus 還是多說的。**不要直接使用我的啊！**

**其次**，你只需要在下面的 yaml 頭文件中設定一下就可以了。

```
duoshuo_username: _你的用戶名_
# 或者
disqus_username: _你的用戶名_
```

**最後** 多說是支援分享的，如果你不想分享，請這樣設定：`duoshuo_share: false`。你可以同時使用兩個評論系統，不過個人感覺怪怪的。

#### Analytics

網站分析，現在支援百度統計和 Google Analytics。需要去官方網站註冊一下，然後將返回的 code 貼在下面：

```
# Baidu Analytics
ba_track_id: 4cc1f2d8f3067386cc5cdb626a202900

# Google Analytics
ga_track_id: 'UA-49627206-1'            # 你用 Google 帳號去註冊一個就會給你一個這樣的 id
ga_domain: huangxuan.me			# 預設的是 auto, 這裡我是自定義了的域名，你如果沒有自己的域名，需要改成 auto。
```

#### Customization

如果你喜歡折騰，你可以去自定義我的這個模板的 code，[Grunt](gruntjs.com) 已經為你準備好了。（感謝 Clean Blog）

JavaScript 的壓縮混淆、Less 的編譯、Apache 2.0 許可通告的添加與 watch 程式碼改動，這些任務都攬括其中。簡單的在命令列中輸入 `grunt` 就可以執行預設任務來幫你建構檔案了。如果你想搞一搞 JavaScript 或 Less 的話，`grunt watch` 會幫助到你的。

**如果你可以理解 `_include/` 和 `_layouts/` 資料夾下的程式碼（這裡是整個介面佈局的地方），你就可以使用 Jekyll 使用的模版引擎 [Liquid](https://github.com/Shopify/liquid/wiki) 的語法直接修改/添加程式碼，來進行更有創意的自定義介面啦！**

#### Header Image

標題底圖是可以自己選的，看看幾篇示例 post 你就知道如何設定了。在
  [issue #6 ](https://github.com/Huxpro/huxpro.github.io/issues/6) 中我被問到：怎麼樣才能讓標題底圖好看呢？
  
標題底圖的選取完全是看個人的審美了，我也幫不了你。每一篇文章可以有不同的底圖，你想放什麼就放什麼，最後寬度要夠，大小不要太大，否則載入慢啊。

但是需要注意的是本模板的標題是 **白色** 的，所以背景色要設定為 **灰色** 或者 **黑色**，總之深色系就對了。當然你還可以自定義修改字體顏色，總之，用 github pages 就是可以完全的個性定製自己的部落格。

#### SEO Title

我的部落格標題是 **"Hux Blog"** 但是我想要在搜尋的時候顯示 **"黃玄的部落格 | Hux Blog"** ，這個就需要 SEO Title 來定義了。

其實這個 SEO Title 就是定義了 `<head><title>標題</title></head>` 這個裡面的東西和多說分享的標題，你可以自行修改的。

## 致謝

1. 這個模板是從這裡 [IronSummitMedia/startbootstrap-clean-blog-jekyll](https://github.com/IronSummitMedia/startbootstrap-clean-blog-jekyll) fork 的。感謝這個作者
2. 感謝 [@BrucZhaoR](https://github.com/BruceZhaoR) 的中文翻譯 

3. 感謝 Jekyll、Github Pages 和 Bootstrap!



