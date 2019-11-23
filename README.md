# 練習 - 購物網站介面

[gh-pages](https://hedgehogkucc.github.io/Pr-Bootstrap-3/)

## Dropdown

```html
<div class="dropdown ml-auto">
  <button class="btn btn-sm btn-cart" data-toggle="dropdown" data-flip="false">
    <i class="fa fa-shopping-cart text-dark fa-2x" aria-hidden="true"></i>
    <span class="badge badge-pill badge-danger">11</span>
  </button>
</div>
```

使用 `button` 包住 `shopping cart icon` 和 `badge`

<br>

```scss
.btn-cart {
  background-color: transparent;
  position: relative;
  .badge {
    position: absolute;
    top: 1px;
    right: 0;
  }
}
```

因為 `shopping cart icon` 和 `badge` 這兩個元素都會被計算到空間

那要取消 `badge` 的空間來疊在 `shopping cart icon` 上面

就會使用到 `相對定位` 和 `絕對定位` 

<br>

### dropdown-menu

```html
<!-- Heads up ! Dropdowns are positioned thanks to Popper.js (except when they are contained in a navbar) -->
<div class="dropdown-menu dropdown-menu-right" style="min-width: 300px">
  <div class="px-4 py-3">
    <h6> ... </h6>
    <table class="table table-sm">
      <tbody>
        <tr>
          <td>
            ...
          </td>
        </tr>
      </tbody>
    </table>
    <a href="#" class="btn btn-primary btn-block">結帳</a>
  </div>
</div>
```

`style="min-width: 300px"` : 最小寬度為 300px

`btn-block` : 將按鈕寬度撐滿 100% 的空間

[dropdowns-menu-alignment](https://getbootstrap.com/docs/4.3/components/dropdowns/#menu-alignment) 

有一個要注意的地方，在 `navbar` 容器中時就無法自己計算位置，所以我們要重新去寫 `dropdown-menu-right`。 

(Bootstrap 4.1.3 以後已不需要另外加入定位)

<br>

## Jumbotron

```html
<div class="jumbotron jumbotron-fluid jumbotron-bg d-flex align-items-end">
  <div class="container">
    <div class="bg-lighter p-3">
      <h1 class="display-3"> ... </h1>
      <p class="lead"> ... </p>
    </div>
  </div>
</div>
```

```scss
.jumbotron-bg {

  // 加入背景圖
  background-image: url('...');

  // 讓圖盡量完整呈現
  background-size: cover;

  // 定位圖的位置
  background-position: center center;

  // 最小高為 400px
  min-height: 400px;
}

.bg-lighter {
  background-color: rgba(255, 255, 255, .65);
}
```

給予 `min-height: 400px;` 會讓 ***文字偏上*** 

如果要往下移使用 `d-flex` `align-items-end`

<br>

背景色比較亂時，就要 **自定義透明背景色** (`bg-lighter`) 來襯托出字 !

同時加上 `p-3` 給它一個空間

<br>

## Card & Grid

```html
<!-- 主要商品列表 (Card) -->
<div class="container">
  <div class="row">
    <div class="col-md-4"></div>
    <div class="col-md-8">
      <div class="row">
        <div class="col-md-4 mb-4">
          <div class="card text-center h-100 border-0 box-shadow">
            <img class="card-img-top" src="..." alt="...">
            <div class="card-body">
              <h4 class="card-title"> ... </h4>
              <p class="card-text"> ... </p>
            </div>
            <div class="card-footer border-top-0 bg-white">
              <div class="btn-group btn-group-sm">
                <a href="#" class="btn btn-outline-secondary">SM</a>
                <a href="#" class="btn btn-outline-secondary">M</a>
                <a href="#" class="btn btn-outline-secondary disabled">L</a>
                <a href="#" class="btn btn-outline-secondary">XL</a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

使用 [Card-deck](https://getbootstrap.com/docs/4.3/components/card/#card-decks) 會將所有卡片擠在同一列 !!!

而使用 `card` 搭配 `Grid` 不會因為卡片數量變多就造成擠壓

還是會維持三分之一的寬度來排列並且超過時就會換行

`card` 在排版時還有一個特性就是 `card-body` 的空間會自動伸展

所以當 `card-body` 內容不一致時，可以在每個 `card` 加上 `h-100` !

<br>

使用 [utilities](https://getbootstrap.com/docs/4.3/utilities/borders/) 來修改樣式

`border-0` `border-top-0`

<br>

增加 `card` 陰影 `box-shadow`

```scss
.box-shadow {

  // 水平, 垂直, 擴散, rgba來做透明 
  box-shadow: 0 3px 5px rgba(0, 0, 0, .16);

  // 加上漸變效果
  transition: box-shadow .3s;

  &:hover {
    box-shadow: 0 4px 10px rgba(0, 0, 0, .24);
  }
}
```

<br>

## List-group

[links-and-buttons](https://getbootstrap.com/docs/4.3/components/list-group/#links-and-buttons)

[tabindex](https://developer.mozilla.org/zh-CN/docs/Web/HTML/Global_attributes/tabindex)

[sticky-top](https://getbootstrap.com/docs/4.3/utilities/position/#sticky-top) 畫面滾動時將會固定在上方

[list-group Methods](https://getbootstrap.com/docs/4.3/components/list-group/#methods) 畫面的切換

```html
<!-- list-group Methods -->
<a 
  class="list-group-item list-group-item-action active" 
  data-toggle="list" 
  href="#list-gold"
><i class="fa fa-diamond" aria-hidden="true"></i> 金牌專賣店</a>

<div class="tab-content">
  <div class="tab-pane active" id="list-gold">
    <div class="row">
      <div class="col-md-4">
        ...
      </div>
    </div>
  </div>
  <div class="tab-pane" id="list-gift">
    ...
  </div>
  <div class="tab-pane" id="list-film">
    ...
  </div>
  <div class="tab-pane" id="list-paw">
    ...
  </div>
</div>
```

加上 

- `data-toggle="list"` 
- `href="#list-gold"`
- `tab-content`
- `tab-pane` 加上 ***active*** 預設頁面呈現

小陷阱 : 

加上 `href="#list-gold"` 請記得將 `href="#"` 刪除

一個標籤裡面同一個屬性只能出現一次，出現第二次的話其中一個會失效 !!!

<br>

## 產品購買區塊製作

電商會特別注意 `SEO`

一個網頁只能有一個標籤 `<h1>...</h1>` 具有語意

而 `class="h1"` 只是樣式大小沒有語意

背景色移除可使用 `bg-transparent`

將 `breadcrumb` 設為 `pl-0` 

<hr>

使用 `d-flex` 來排售價區塊

售價靠齊右邊 `justify-content-end`

文字對齊底部 `align-items-end`

網路價 ***margin-left 自適應*** `ml-auto`

`class="h3"` 會有 ***margin-bottom: .5rem;*** 所以要多加 `mb-0`

```html
<div class="d-flex justify-content-end align-items-end">
  <del class="text-muted">售價 $1299</del>
  <div class="h3 ml-auto text-danger mb-0">
    <small>網路價 NT$</small>
    <strong>520</strong>
  </div>
</div>
```

<br>

上面這樣排版的好處是把下方程式碼註解後

售價會自己靠齊右邊

```html
<div class="h3 ml-auto text-danger mb-0">
  <small>網路價 NT$</small>
  <strong>520</strong>
</div>
```

<br>

`btn-group` 中的小訣竅

在 `btn` 加上

```scss
.btn.disabled {
  pointer-events: none;
}
```

可以避免發生點選 `disabled` 尺寸時 

`radio` 都沒有選擇尺寸的狀態

<br>

要排出 `select` 和 `button` 並排

可以使用 `input-group`

```html
<div class="input-group mt-3">
  <select name="" class="form-control mr-1" id="">
    <option value="1">1 件</option>
    <option value="2">2 件</option>
    <option value="3">3 件</option>
  </select>
  <a href="#" class="btn btn-primary">
    <i class="fa fa-shopping-cart" aria-hidden="true"></i> 加入購物車
  </a>
</div>
```

<br>

將區塊放入 `.sticky-top` 裡面

讓用戶滑動網頁時都能固定在上方

並在上方預留空間 `top: 10px`

```html
<div class="sticky-top" style="top: 10px;">
  ...
</div>
```

<br>

## 使用 alert 元件 製作多步驟提示

`form-row` 會讓間距變小一點

`col-12` 在 576px 以 ***下*** 呈現滿版

`col-sm` 在 576px 以 ***上*** 自適應欄位

`alert-rounded` 將方框設定為圓邊

```html
<!-- 輸入資料頁 -->
<div class="container main-content py-5">
  <h1 class="text-center mb-3 text-secondary">六角血拼 結帳</h1>
  <div class="form-row text-center">
    <div class="col-12 col-sm">
      <div class="alert alert-primary alert-rounded" role="alert">
        1.輸入訂單資料
      </div>
    </div>
    <div class="col-12 col-sm">
      <div class="alert alert-light alert-rounded" role="alert">
        2.金流付款
      </div>
    </div>
    <div class="col-12 col-sm">
      <div class="alert alert-light alert-rounded" role="alert">
        3.完成
      </div>
    </div>
  </div>
</div>
```

```scss
.alert-rounded {
  border-radius: 50px;
}
```

<br>

## 收合購物車

使用 [collapse](https://getbootstrap.com/docs/4.3/components/collapse/#accordion-example) 來做到折疊效果

對於使用在手機上非常方便

可以將資訊隱藏起來

需要看的時候再點開

記得將 `<div id="collapseOne" ...>` 移出至 `<card>` 外面

如果不一開始呈現出來 `class="collapse show"` 請把 `show` 刪除

<br>

