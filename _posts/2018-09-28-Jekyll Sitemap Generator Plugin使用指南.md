---
layout: post
title: Jekyll Sitemap Generator Plugin使用指南
subtitle: 生活中总有黑暗笼罩的时刻，永远不要放弃自己
date: 2018-09-28
author: JaceyKan
header-img: img/post-bg-2015.jpg
catalog: true
tags: 
 - Blog
 - jekyll
 - sitemap
---

### 参考文章：
> * [sitemap百度百科](https://baike.baidu.com/item/sitemap)
> * [jekyll-sitemap](https://github.com/jekyll/jekyll-sitemap)
> * [jekyll插件的用法](https://jekyllrb.com/docs/plugins/installation/)
> * [Jekyll Sitemap.xml](https://szhshp.org/tech/2016/03/25/sitemapforjekyll.html)


### `sitemap` 网页地图 
**形式**: XML，html，建站工具 

Sitemap 方便网站管理员通知搜索引擎他们网站上有哪些可供抓取的网页。
在其中列出网站中的网址以及关于每个网址的其他元数据（上次更新的时间、更改的频率以及相对于网站上其他网址的重要程度为何等），以便搜索引擎可以更加智能地抓取网站。


### `jekyll-sitemap`
jekyll的站点地图生成插件

### `jekyll-sitemap`用法

#### 1.安装 `jekyll-sitemap`
打开Start Command Prompt with Ruby
![](https://jaceykan.github.io/img/20180927ruby-jekyll-install.jpg)

在命令行下输入
```
gem install jekyll-sitemap
```
![](https://jaceykan.github.io/img/20180928-01.png)

### 2.进入对应的站点目录下，修改站点的 `_config.yml` 文件
```
url: "http://example.com" # the base hostname & protocol for your site
plugins:
  - jekyll-sitemap
```
![](https://jaceykan.github.io/img/20180928-02.png)

### 3.运行站点
```
jekyll serve
```
![](https://jaceykan.github.io/img/20180927ruby-jekyll-install05.png)

在站点的 `_site` 文件夹下生成 [`sitemap.xml`](https://jaceykan.github.io/sitemap.xml) 文件

![](https://jaceykan.github.io/img/20180928-03.png)

```
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sitemaps.org/schemas/sitemap/0.9 http://www.sitemaps.org/schemas/sitemap/0.9/sitemap.xsd" xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
<url>
<loc>http://localhost:4000/2017/02/06/%E5%BF%AB%E9%80%9F%E6%90%AD%E5%BB%BA%E4%B8%AA%E4%BA%BA%E5%8D%9A%E5%AE%A2/</loc>
<lastmod>2017-02-06T00:00:00+08:00</lastmod>
</url>
<url>
<loc>http://localhost:4000/2017/02/15/Git%E6%8C%87%E4%BB%A4%E6%95%B4%E7%90%86/</loc>
<lastmod>2017-02-15T00:00:00+08:00</lastmod>
</url>
<url>
<loc>http://localhost:4000/2017/02/16/Git-%E4%BB%A3%E7%A0%81%E5%9B%9E%E6%BB%9A/</loc>
<lastmod>2017-02-16T00:00:00+08:00</lastmod>
</url>
<url>
<loc>http://localhost:4000/2017/02/22/%E4%BD%BF%E7%94%A8-.gitignore-%E5%BF%BD%E7%95%A5-git-%E4%BB%93%E5%BA%93%E4%B8%AD%E7%9A%84%E6%96%87%E4%BB%B6/</loc>
<lastmod>2017-02-22T00:00:00+08:00</lastmod>
</url>
<url>
<loc>http://localhost:4000/2017/12/19/%E4%B8%BA%E5%8D%9A%E5%AE%A2%E6%B7%BB%E5%8A%A0-Gitalk-%E8%AF%84%E8%AE%BA%E6%8F%92%E4%BB%B6/</loc>
<lastmod>2017-12-19T00:00:00+08:00</lastmod>
</url>
<url>
<loc>http://localhost:4000/2018/09/26/%E4%BD%A0%E5%B0%B1%E6%98%AF%E8%87%AA%E5%B7%B1%E7%9A%84%E5%B9%B8%E8%BF%90%E5%A5%B3%E7%A5%9E/</loc>
<lastmod>2018-09-26T00:00:00+08:00</lastmod>
</url>
<url>
<loc>http://localhost:4000/2018/09/27/jekyll%E5%9C%A8win10%E4%B8%8B%E7%9A%84%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97/</loc>
<lastmod>2018-09-27T00:00:00+08:00</lastmod>
</url>
<url>
<loc>http://localhost:4000/2018/09/28/sitemap/</loc>
<lastmod>2018-09-28T00:00:00+08:00</lastmod>
</url>
<url>
<loc>http://localhost:4000/about/</loc>
</url>
<url>
<loc>http://localhost:4000/</loc>
</url>
<url>
<loc>http://localhost:4000/offline.html</loc>
</url>
<url>
<loc>http://localhost:4000/tags/</loc>
</url>
</urlset>
```