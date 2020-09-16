# Social Network Project

## Initial Set Up

- open settings > search for live sass > edit setting.json file

```json
 "liveSassCompile.settings.formats": [
        {
            "format": "compressed",
            "extensionName": ".css",
            "savePath": "/dist/css"
        }
    ]
```

- compiled sass files are stored in _/dist/css_ path.
- create two folders _dist_ and _scss_.
- create index.html in dist folder, _style.scss_ file in scss folder.
- to compile the scss file to css, click on _Watch Sass_ on editor.

**screenshot**

![image](./screenshots/path.png 'image')

---

- In scss folder, create diff scss file for variables, functions, mixins.

- this files rcalled **partials**.

- v create file called _\_config.scss_ to store all variables.

- later import that file to _style.scss_

---

## adding mixins and fucnton to set background and text color

**\_config.scss**

```scss
// function to set text color based on bg color lightness
@function check-lightness($color) {
  @if (lightness($color) > 70) {
    @return #333333;
  } @else {
    @return #fff;
  }
}
// create mxin - set color and bg-color
@mixin set-bg-text-color($color) {
  background-color: $color;
  // text color depends on background color
  color: check-lightness($color);
}
```

## background color utitlies class

**\_utilities.scss**

```scss
// background utility classes
.bg {
  // inclde the mixin here
  &-primary {
    @include set-bg-text-color($primary-color);
  }
  &-light {
    @include set-bg-text-color($light-color);
    border: #cccccc 1px solid;
  }
  &-dark {
    @include set-bg-text-color($dark-color);
  }
  &-danger {
    @include set-bg-text-color($danger-color);
  }
  &-success {
    @include set-bg-text-color($success-color);
  }
  &-white {
    @include set-bg-text-color(#ffffff);
    border: #cccccc 1px solid;
  }
}
```

---

## buttton utllities

**index.html**

```html
<div class="buttons">
  <a href="register.html" class="btn btn-primary">Sign Up</a>
  <a href="login.html" class="btn">Login</a>
</div>
```

**scss/_utilities.scss**

```scss
// Buttons
.btn {
  font-size: 1rem;
  display: inline-block;
  cursor: pointer;
  background: $light-color;
  color: #333333;
  padding: 0.5rem 1.2rem;
  border: none;
  outline: none;
  margin-right: 0.5rem;
  // transiton all properties
  transition: all 0.3s ease-in;

  &.btn-primary {
    // call mixin
    @include set-bg-text-color($primary-color);
    &:hover {
      // apply lighten() function - lighten the color by 5%
      background: lighten($color: $primary-color, $amount: 5%);
    }
  }
  &.btn-dark {
    @include set-bg-text-color($dark-color);
    &:hover {
      background: lighten($color: $dark-color, $amount: 5%);
    }
  }
  &.btn-light {
    @include set-bg-text-color($light-color);
    &:hover {
      background: lighten($color: $light-color, $amount: 5%);
    }
  }
  &.btn-danger {
    @include set-bg-text-color($danger-color);
    &:hover {
      background: lighten($color: $danger-color, $amount: 5%);
    }
  }
  &.btn-success {
    @include set-bg-text-color($success-color);
    &:hover {
      background: lighten($color: $success-color, $amount: 5%);
    }
  }
  &:hover {
    background: lighten($color: $dark-color, $amount: 20%);
    color: #ffffff;
  }
}
```
