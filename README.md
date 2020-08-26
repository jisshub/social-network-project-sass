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
