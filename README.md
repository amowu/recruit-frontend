# Hahow Frontend Engineer 徵才小專案

這是一個小型的徵才專案，會需要你使用 JS framework 和 backend API 所提供的資料，依照 wireframe 來完成頁面。

## 細部需求

- 請參考 wireframe 及 頁面需求 來實作這個專案
- 請使用你習慣的 JavaScript framework (ex: Angular, React, Vue.js)，如果沒有習慣使用的 framework，請盡量使用 Angular
- 請 fork 本專案到自己的 GitHub 作版本管理
- 完成之後請使用 Pull Request 提交作品，並提供以下說明：
  - 我們該如何執行完成的 package
  - 專案的架構、邏輯
  - 你對於所有使用到的第三方 library 的理解，以及它們的功能簡介
  - 你在程式碼中寫註解的原則，遇到什麼狀況會寫註解
  - 在這份專案中你遇到的困難、問題，以及解決的方法

## 加分建議

- 使用 CSS framework
- 程式碼的可讀性與可維護性
- 任何你覺得可以讓網頁變得更酷的事情

## 頁面需求

- 整個專案會需要兩個頁面：
  - Hero List Page（網址：/heroes）
  - Hero Profile Page（網址：/heroes/:heroId）
- Hero List Page、Hero Profile Page 都有一個 Hero List 在頁面上水平置中
- Hero List 上的元素我們稱為 Hero Card，在 Hero List 中由左到右排列，如果在小尺寸螢幕上列表中的元素超出畫面就自動往下排列
- Hero Card 必須包含圖片和名字，且是可以點擊的連結
- Hero Card 連結會連到單一 Hero 的 Hero Profile Page，Hero List 依然在相同位置，並且不因切換連結重新 render
- 當在 Hero Profile Page 時要將現在所選中的 Hero Card 用不同的顏色或圖案標示出來
- Hero Profile Page 中，在 Hero List 底下會有一個 Hero Profile
- Hero Profile 會顯示 Hero 的能力值，並且在數值左右各有一個按鈕，負責做增減功能，另外有一個顯示剩餘的能力點數的地方，一開始預設值是 0
- Hero Profile 最下方有一個儲存按鈕，按下按鈕後，會將現在設定的能力值提交更新 server 上的資料，送出的能力值總和必須與拿到的時候相同
- Hero 能力值不能小於零

## 最後

同時，我們也認為在程式開發的過程中溝通是很重要的，所以如果過程中你有任何問題，不論是看不懂我們所寫的文件，或是對於我們提供的 API 有疑問，都歡迎直接開 Issue 和我們討論。

## Wireframe

![hero-list-page](https://cloud.githubusercontent.com/assets/559351/19520231/151c12a6-9642-11e6-8405-2e700dc31dad.png)

![hero-profile-page](https://cloud.githubusercontent.com/assets/559351/19520255/2a231370-9642-11e6-9d3e-409e9ff667c5.png)

## Backend RESTful API

### List Heroes

Request:

```
curl -H "Accept: application/json" -H "Content-Type: application/json" -X GET http://hahow-recruit.herokuapp.com/heroes
```

Response 200:

```
[
    {
        id: "1",
        name: "Daredevil",
        image: "http://i.annihil.us/u/prod/marvel/i/mg/6/90/537ba6d49472b/standard_xlarge.jpg"
    },
    {
        id: "2",
        name: "Thor",
        image: "http://x.annihil.us/u/prod/marvel/i/mg/5/a0/537bc7036ab02/standard_xlarge.jpg"
    },
    ...
]
```

---

### Single Hero

Request:

```
curl -H "Accept: application/json" -H "Content-Type: application/json" -X GET http://hahow-recruit.herokuapp.com/heroes/1
```

Response 200:

```
{
    id: "1",
    name: "Daredevil",
    image: "http://i.annihil.us/u/prod/marvel/i/mg/6/90/537ba6d49472b/standard_xlarge.jpg"
}
```

---

### Profile of Hero

Request:

```
curl -H "Accept: application/json" -H "Content-Type: application/json" -X GET http://hahow-recruit.herokuapp.com/heroes/1/profile
```

Response 200:

```
{
    str: 2,
    int: 7,
    agi: 9,
    luk: 7
}
```

---

### Patch Hero's Profile

Request:

```
curl -X PATCH -H "Content-Type: application/json" -d '{ "str": 6, "int": 7, "agi": 7, "luk": 5 }' "https://hahow-recruit.herokuapp.com/heroes/1/profile"
```

Response 200:

```
OK
```