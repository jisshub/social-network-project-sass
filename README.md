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
