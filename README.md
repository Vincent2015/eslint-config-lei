# eslint-config 配置

## 安装

```bash
$ npm install eslint-config-lei --save-dev
```

## 使用方法

### 配置文件

在项目根目录下新建文件`.eslintrc.js`：

仅包含 ES6 语法时：

```javascript
module.exports = {
  extends: 'lei',
};
```

包含 ES7 语法时：

```javascript
module.exports = {
  parser: 'babel-eslint',
  parserOptions: {
    sourceType: 'module',
    allowImportExportEverywhere: false,
  },
  extends: 'lei',
};
```

在基于`mocha`框架的单元测试中使用，在`test`目录下新建文件`.eslintrc.js`：

```javascript
module.exports = {
  extends: 'lei/mocha',
};
```

### 使用

执行以下命令即可：

```bash
$ eslint dir/**.js
```

如果需要自动格式化代码，在执行时添加`--fix`选项：

```bash
$ eslint dir/**.js --fix
```


## 常见问题

1、如果在使用`babel-eslint`时报错，可能是该模块的 Bug，目前可以通过以下方法解决：

```javascript
module.exports = {
  parser: 'babel-eslint',
  parserOptions: {
    sourceType: 'module',
    allowImportExportEverywhere: false,
  },
  extends: 'lei',
  rules: {
    // 关闭以下规则
    'generator-star-spacing': 'off',
    'require-yield': 'off',
  },
};
```

2、在使用过程中，可能会遇到一些例外情况，比如需要更改参数对象的属性，可以通过`eslint-disable-next`来临时关闭对下一行的检查：

```javascript
// eslint-disable-next-line no-param-reassign
param.xxx = 'ok';
```

**注意：任何时候请勿使用`eslint-disable`来关闭`eslint`的检查，如果该备注不能与`eslint-enable`成对出现将会导致余下的程序不能正常获得检查**


## License

```
The MIT License (MIT)

Copyright (c) 2016 Zongmin Lei <leizongmin@gmail.com>

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
```
