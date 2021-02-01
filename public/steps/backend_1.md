## 必修課題

### 步驟 1: 建立 Rails 的開發環境

#### 1-1: 安裝 Ruby

> - 利用 [rbenv](https://github.com/rbenv/rbenv) 或 [RVM](https://rvm.io) 安裝最新版本的 Ruby
> - 以 `ruby -v` 指令來確認 Ruby 的版本

1. 安裝 RVM Install RVM:
   `$ \curl -sSL https://get.rvm.io | bash -s stable`
2. For installing RVM with default Ruby and Rails in one command, run:
   `$ \curl -sSL https://get.rvm.io | bash -s stable --rails`
3. 列出可安裝的 ruby 版本，`$ rvm list known`
4. 更新至最新版，`$ rvm get master`
5. 安裝 ruby 並指定版本，`$ rvm install 3.0.0`
6. 確認已經安裝在電腦裡的 ruby 有哪些？`$ ruby list`
7. 查看現在使用的 ruby 版本， `$ ruby -v`

##### 其他指令

1. 更換使用其他版本，`$ rvm use 2.7.2`，其中 use 可省略
2. 使用 RVM 指定的 Ruby 版本會在每次開啟新的終端機視窗的時候變回預設值(也就是變回系統內建的 Ruby 版本)，可使用指令指定預設的版本，`$ rvm 2.6.6 --default`。
3. rvm 會依照 PATH 裡面的路徑來執行相應的 ruby 版本，排後面的優先（後面的會覆蓋前面的）
4. 切換回預設版本，`$ ruby system`
5. 移除特定版本的 ruby，`$ rvm uninstall 2.6.3`

---

#### 1-2: 安裝 Rails

> - 以 gem 指令安裝 Rails
> - 安裝最新版本的 Rails
> - 以 `rails -v` 指令來確認 Rails 的版本

---

#### 1-3: 安裝資料庫（PostgreSQL）

- 在你使用的 OS 下安裝 PostgreSQL
  - macOS 的話，請以 `brew` 等工具安裝

### 步驟 2: 在 GitHub 建立 repository

- 在你的環境中安裝 Git
  - macOS 的話，請以 `brew` 等工具安裝
  - 以 `git config` 設定 user name 和 email
- 請考慮專案名稱（也等於 repo 名稱）
- 建立 repo
  - 如果沒有帳號的話，先申請帳號
  - 接著建立空白的 repo

### 步驟 3: 建立 Rails 專案

- 以 `rails new` 指令，建立 Rails 應用程式最低限度的樣板和檔案
- 在 `rails new` 產生的專案目錄下，建立 `docs` 資料夾，並將本教程文件 commit 進去
  - 目的是為了方便之後開發時可以參考
- 將成品 push 到 GitHub 的 repo
- 將使用的 Ruby 版號寫進 `Gemfile`（也請確認 Rails 版號是否有標明）

### 步驟 4: 想像網站成品會是什麼樣子

- 開始進行設計之前，先和導師一起討論對最終成品的預想。建議在紙上畫 prototype
- 請參照網站需求，開始想需要怎樣的資料結構
  - 需要哪些 model (或資料表)？
  - 資料表會需要哪些欄位？
- 有想法之後，將 model 的關係圖手繪出來
  - 完成後將關係圖拍照存檔，放進 repo 裡
  - 把 table schema 寫進 `README.md`（model 名稱、欄位名稱、資料形態）

※ 在這個階段，model 關係圖不需要是完全正確的。以現在所能預想的範圍來規劃就好（做到後面的步驟，發現需要修改時再來調整的概念）

### 步驟 5: 資料庫連接等週邊設定

- 建立新的 topic 分支
  - 之後都在 topic 分支上開發並進行 commit
- 安裝 bundler
- 在 `Gemfile` 安裝 `pg`（PostgreSQL 的 adapter）
- 設定 `database.yml`
- 以 `rails db:create` 建立資料庫
- 以 `rails db` 確認有正確連接資料庫
- 在 GitHub 上建立 PR 並請人 review
  - 必要時，請在 PR 上標柱 WIP（Work In Progress）
  - 收到 Comment 後就做必要的處置。收到兩個 LGTM（Looks Good To Me） 後就可以 merge 回 master

### 步驟 6: 建立任務 model

開始來做管理任務所需要的 CRUD。一開始先簡單做，只要能記錄名字和任務內容即可。

- 以 `rails generate` 指令建立 CRUD 所需的 model 類別
- 撰寫 migration 並以此建立資料表
  - 非常重要：migration 要確定能安全回到上一步的狀態！請養成以 `redo` 確認的習慣
- 以 `rails c` 指令，透過 model 確認有正確連接資料庫
  - 順便試著以 ActiveRecord 建立資料
- 在 GitHub 上發 PR 並請人 review

### 步驟 7: 新增、修改、刪除任務

- 製作任務的列表、新增、檢視以及修改頁面
  - 以 `rails generate` 指令產生 controller
    - 請和導師討論要用哪一種 template engine（ERB / Slim / Haml..etc）
  - 實做 controller 和 view 必要的部分
  - 完成新增、修改、刪除之後需要在畫面上顯示的 Flash 訊息
- 修改 `routes.rb`，讓 `http://localhost:3000/` 會顯示任務的列表頁面
- 在 GitHub 上發 PR 並請人 review
  - 之後的 PR，如果覺得過於龐大，就需要開始考慮分割成多個 PR

### 步驟 8: 寫 E2E 測試

- 寫 spec 的事前準備
  - 準備 `spec/spec_helper.rb` 、`spec/rails_helper.rb`
- 針對任務的功能來寫 feature spec
- 導入 Travis CI 之類的 CI 工具，每次 Push 後自動跑 Spec
  - 太難的話可以請導師幫忙設定

### 步驟 9: 將網站中的中文部分共用化

- 利用 Rails 的 i18n 功能，將 View / Controller / Model 中的語言部份共用化

※ i18n 化的好處是，之後的步驟中，各種訊息的處理會輕鬆很多

### 步驟 10: 設定 Rails 的時區

- 將 Rails 的時區設為台灣（台北）

### 步驟 11: 任務列表以建立時間排序

- 資料預設是以 id 進行排序，請試著讓它以建立時間排序
- 完成後，撰寫 feature spec

### 步驟 12: 資料驗證

- 開始設定資料驗證
  - 請思考需要在哪個欄位上加入哪種驗證比較好
  - 與之配合的 DB 限制，請寫成 migration
  - 以 `rails generate` 指令產生 migration file
- 在頁面上加入驗證的錯誤訊息
- 撰寫對應的 model 測試
- 在 GitHub 上發 PR 並請人 review
