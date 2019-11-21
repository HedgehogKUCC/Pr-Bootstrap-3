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

