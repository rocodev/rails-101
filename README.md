# 前言

學習曲線過高往往是有志於學習 Ruby on Rails 的開發者心中的一抹遺憾。市面上的中文書不知過期了幾年，網路上找到的 Hello World 跑不起來。最誇張的是，光是想裝一套穩當的開發環境在電腦上，卻發現自己完全不得其門而入，做不到！

我是 xdite，台灣知名的資深 Ruby on Rails 程式設計師。07年 自學 Rails 至今。曾經訓練、帶領多支技術團隊開發過各式各樣的 Rails 專案。 

在過去的自學過程當中，我意識到 Ruby on Rails 的版本變革過速，是造成開發者培育不易的主要原因。培育一個合格的初級 Rails Developer，企業可能往往要投上數月甚至一年才有所得。 

如果能幫新手**弭平各式各樣的超級門檻**，是不是能把長達一年的摸索期，砍到只剩短短的幾個禮拜？最後，我設計了一份超級新手作業(最後變成了本書）。這份作業成功的讓我將新人培育的時間從**數月降至兩週以下**。這些開發者，有的甚至**之前從未有過任何網頁開發背景**。 

你也想學 Rails 嗎？他們可以，我相信你也辦得到！

# 說明

這份文件 是 [Rails 101](http://rails-101.logdown.com) 的部分公開資料。若您喜歡本書，請付費 [購買支持](http://rails-101.logdown.com)。

另外要提醒的是，Rails 用「看的」並不會「達成任何效果」。而這本書裡面的每一個章節，都是身為 Rails Developer 中基本再基本的功夫，跳過任何一章只會讓你屆時在實戰中踢到更大的鐵板。建議讀者反覆練習寫到倒背如流。

筆者建議的練習標準是：能夠在五分鐘之內用手寫出 RESTful 七個 action，讀者不妨可以試看看。

# 目錄

* [購買一台 Mac](#buy-a-mac)
* [Learn Git and Command Line](#learn-git-and-command-line)
* [建置 Bug Free Rails 開發環境 (Mac/Ubuntu)]

## Buy a Mac

開發 Ruby on Rails 基本上強烈建議使用 OS X 10.6 + 以後作為開發平台。因為不少的 Rails ecosystem 都圍繞著 OSX。不用 Mac 開發基本上非常容易碰壁。

### 硬體需求

* 一台 2009 後出款的 Mac Mini / Macbook Pro / Macbook Air 。
* 4 - 8GB 以上的記憶體。（開發網站的時候，有實際開 VM 測 IE 的需求。）

## Learn Git and Command Line

Rails 的生態圈與 Git 和 Unix Command Line 綁的非常深。不熟悉的入門者，建議購買以下教材實作練習：

* Peepcode 的 [Git](https://peepcode.com/products/git) $12 ，練習以下七個指令
  - git commit
  - git push
  - git pull
  - git branch
  - git checkout
  - git merge

* Peepcode 的 [Meet the Command Line](https://peepcode.com/products/meet-the-command-line) $12 與 [Advanced Commandline](https://peepcode.com/products/advanced-command-line) $12。跟著練習裡面所有的指令

## 建置 Bug Free Rails 開發環境

## Rails : RESTful , 雙層 Resource

### 作業目標

開發一個簡易論壇系統。系統要有 Board 與 Post 兩個 model，寫出 CRUD 介面，並且文章網址是使用 <http://forum_demo.dev/board/1/post/2> 這種表示。

### 吸收觀念

* CRUD & migration
* has_many 與 belongs_to
* resources 與雙層 resources
* before_filter :find_board


## Rails : 實作使用者認證系統

### 作業目標

為論壇加入使用者機制，使用者必須能夠 註冊 / 登入，登入後才可以發表 Post，不然只能瀏覽。只有自己的 Post 才能進行修改與刪除。

### 吸收觀念

* plugin 安裝與使用 : devise
* routes 優先權與 route alias
* before_filter: login_required
* session : current_user 
* [before_filter](http://apidock.com/rails/ActionController/Filters/ClassMethods/before_filter)

## 為論壇加入管理者機制以及管理者後台

### 作業目標

實作簡單的 admin 機制， admin 擁有一個後台，可以刪改所有文章。admin 可以開板 / 刪板。網址是 http://forum_demo.dev/admin/boards 。只有身分是 admin 的人可以進後台。admin 的判別方是 column 裡加一個 boolean，判斷是否 admin。這個 attribute 必須用 attr_accessible / attr_protected 保護。

### 吸收觀念

* [attr_accessible](http://apidock.com/rails/v3.0.7/ActiveModel/MassAssignmentSecurity/ClassMethods/attr_accessible) / [attr_protected](http://apidock.com/rails/v3.0.7/ActiveModel/MassAssignmentSecurity/ClassMethods/attr_protected)
* route : namespace
* before_filter : require_is_admin

## 為論壇加上分頁機制

### 作業目標

看板的文章要能夠分頁，每一頁 5 筆，每一個看板要秀出現在看板裡有多少 post 數量。可用 params 配合 scope 在文章列表排序。

### 吸收觀念

* [counter_cache](http://railscasts.com/episodes/23-counter-cache-column)
* pagination : [will_paginate](https://github.com/mislav/will_paginate/wiki/)
* [scope](http://railscasts.com/episodes/108-named-scope) :recent

## Rails : 實作圖片上傳系統

### 作業目標

發表文章時可以順便夾帶一張附件。

### 吸收觀念

[form_for](http://apidock.com/rails/ActionView/Helpers/FormHelper/form_for) multipart  # 內含多媒體要指定

### 上傳檔案套件

[carrierwave](https://github.com/jnicklas/carrierwave)

## Rails : 利用 Rake 撰寫自動執行的 tasks

### 作業目標

用 Rake 撰寫自動化步驟，生假資料。

寫一個 rake 可以達成以下步驟：「砍 db => 建 db => 跑 migration => 生種子資料」，另一個 rake 是生假文章與假論壇。


### 吸收觀念

* rake -T
* rake db:drop ; rake db:create ; rake db:migrate ; rake db:seed
* rake dev:fake ( 自己寫 namespace : dev, 裡面放一個 task 叫做 fake，fake 資料用 Populator 生） # 請自行練習

### 參考資料

* [Ruby on Rails Rake Tutorial (aka. How rake turned me into an alcoholic)](http://jasonseifer.com/2010/04/06/rake-tutorial)
* [What’s New in Edge Rails: Database Seeding](http://ryandaigle.com/articles/2009/5/13/what-s-new-in-edge-rails-database-seeding)

## 將論壇 deploy 到租來的 VPS

### 作業目標

在租來的 VPS 上面建置 Ruby on Rails production 環境，使用 Ruby 1.9 與 mod_rails。使用 [Capistrano](https://github.com/capistrano/capistrano/wiki) 佈署 application。

### 吸收觀念

* cap deploy:setup
* cap deploy 
* cap deploy:rollback 
* cap deploy:restart

### 參考資料

* [rails-nginx-passenger-ubuntu](https://github.com/jnstq/rails-nginx-passenger-ubuntu)
* [AWDR4](http://pragprog.com/titles/rails4/agile-web-development-with-rails) 的 deploy 章節 , Rails Pocket Reference 的 Capistrano 章節


## Rails 最新線上學習資源

### Podcast

* [Ruby5](http://ruby5.envylabs.com/)
* [Ruby Rogues](http://rubyrogues.com/)
* [Thoughtbot Podcast](http://robots.thoughtbot.com/tagged/podcast)
* [The Ruby Show](http://rubyshow.com/)

### 商業教材

* [Codeschool](http://codeschool.com)
* [Railscast](http://railscast.com)
* [DestroyAllSoftware](https://www.destroyallsoftware.com/)
* [Peepcode](https://peepcode.com/)

### Websites

* [Ruby Inside](http://www.rubyinside.com/)
* [RubyFlow](http://www.rubyflow.com/)
* [Ruby Weekly](http://rubyweekly.com/)
* [Ruby Tips](http://rubyquicktips.com/)
* [Rails Tips](http://railstips.org)
* [Ruby Toolbox](http://ruby-toolbox.com/)
