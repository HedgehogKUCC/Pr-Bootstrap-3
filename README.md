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

