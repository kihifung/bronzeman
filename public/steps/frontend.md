## 必修課題

### 步驟 1: 建立 JavaScript 的開發環境

#### 1-1: 安裝 Node.js

- 利用 [nvm](https://github.com/creationix/nvm) 或 [Homebrew](https://brew.sh/index_zh-tw) 安裝最新版本的 Node.js
- 以 `node -v` 指令來確認 Node.js 的版本

#### 1-2: 安裝 [yarn](https://yarnpkg.com/zh-Hans/)

- `$ brew install yarn`
- 以 `$ yarn -v` 指令來確認版本
- 了解 `package.json` 基本內文格式與基本指令
- 了解 `dependencies`、`devDependencies`、`peerDependencies` 的差異與指令

### 步驟 2: 在 GitHub 建立 repo

- 在你的環境中安裝 git
  - macOS 的話，請以 `brew` 等工具安裝
  - 以 `$ git config` 設定 user name 和 email
- 請考慮專案名稱（也等於 repo 名稱）
- 建立 repo
  - 如果沒有帳號的話，先申請帳號
  - 接著產生空白的 repo

### 步驟 3: 建立 React 專案

- 以 `$ npx create-react-app` 指令，建立 app 最低限度的樣板和檔案
- 在 `create-react-app` 產生的專案目錄下，建立 `docs` 資料夾，並將本教程文件 commit 進去
  - 搬進來是為了方便之後開發時可以參考
- 將成品 push 到 GitHub 的 repo
- 將使用的 Node.js 版號寫進 `package.json`（也請確認 React 版號是否有標明）

### 步驟 4: 復刻 [五倍官網首頁](https://5xruby.tw/)

- 引入 `bootstrap`、`jquery` 請使用 yarn 安裝使用
- 不使用 React、其它 library, 只能用 jquery + css 實作官網上的元件(bootstrap 只可用 grid system、排版用的 class)
- 請分成三階段發 PR, header、footer、content
- 只需考量 sm、md、lg 3 種 RWD breakpoint
- Bootstrap Carousel 元件的實作需要達成以下要求：
  - 點下圓點按鈕可以跳到指定的 Slide
  - 自動播放（5 秒換頁一次）
  - 按下圓點按鈕可以停止自動播放
- 目標著重於 jquery、javascript、css 熟悉度

### 步驟 5: 使用 React 改寫 [五倍官網首頁](https://5xruby.tw/)

- 將靜態資料抽離存成 json 檔, 並以 react props 的方式帶入
- 目標著重於 React 元件模組化與 props 傳遞

### 步驟 6: 使用 React 製作 [/contacts](https://5xruby.tw/contacts) 頁面

- 必須符合 Controlled Components 特性
- 各個欄位必須加上 html5 validate
- 使用 [React Modal](https://github.com/reactjs/react-modal) 將送出的表單資料顯示在 Popup Modal 上面(樣式只要求有 popup modal 效果)

### 步驟 7: 改用 [webpack](https://webpack.js.org/) 替代 `create-react-app`

- 設定 loader, 讓專案能讀取 css、js、font、image 等...檔案
- 設定 babel, 能編譯 react jsx + es6 語法
- 分類好資料夾架構
- 將先前的五倍首頁 react 版本導入至 webpack 並可運作

### 步驟 8: 加入 eslint 修正語法錯誤與 coding style

- 要求參照 [airbnb config](https://github.com/airbnb/javascript/tree/master/packages/eslint-config-airbnb)
- 能夠在終端機使用 `$ yarn lint` 來跑專案內的 js 檔案做檢查
- 修正所有 eslint 錯誤

### 步驟 9: 整合 Travis CI

- 加入 eslint 當做測試項目

### 步驟 10: 加入 [React-Router](https://github.com/ReactTraining/react-router)

- 將首頁 nav 的導覽項目做成各個 router page, 並可以有 single page render(SPA) 的效果
- 新加入的 router page 不需實作該頁內容, 只需標註是哪一頁即可
- 需有當前網頁路徑的 nav list hightlight 的效果

### 步驟 11: fetch api 資料串接

- 使用 React 製作 [/posts](https://5xruby.tw/posts) 頁面, 資料來源請使用 [jsonplaceholder](https://jsonplaceholder.typicode.com/)
- 使用 React 製作 pagination component 需達成以下要求：
  - 必須是一個獨立且可引入使用的 component
  - 一頁 post 資料比數最多顯示 4 筆
  - 至少需要有 `首頁`、`末頁`、`下一頁` 按鈕功能

### 步驟 12: 錯誤處理

- 使用 [HOC](https://reactjs.org/docs/higher-order-components.html) 與 [Error Boundaries](https://reactjs.org/docs/error-boundaries.html#introducing-error-boundaries) 替 `/post` 頁面製作 fetch api 拿不到資料的錯誤處理
- 錯誤處理的效果顯示自行定義

### 步驟 13: 使用 [React Context Api](https://reactjs.org/docs/context.html#api) refactor component

- 了解 context api 使用時機, 並在現有程式碼尋找哪個 component 適合使用 context api 並以此做 refactor
- 此步驟可以隨時安插在其他步驟實作

### （番外篇）選修課題

- [react render props](https://reactjs.org/docs/render-props.html): 可替代 HOC 的另一種程式碼共用手法。
- react: 用 create-react-app 建立一個新的專案，並研究用 [npm run eject](https://github.com/facebook/create-react-app/blob/master/packages/react-scripts/template/README.md#npm-run-eject) 產生出來的 webpack 設定檔與步驟七手刻的版本有哪些差異？
- react application test： https://jestjs.io/docs/en/tutorial-react
- redux (container、action、reducer)
- react: credit card form (信用卡表單)
- react: infinite scroll
- react: popup video
