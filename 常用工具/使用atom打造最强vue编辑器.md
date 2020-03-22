### 常用插件

- atom-beautify 代码格式化



### vue专属插件

- linter-eslint(检查js代码及vue代码)

为了让atom能够检查vue代码，需要下载的插件有

- eslint
- eslint-plugin-vue

##### atom操作方法

设置`linter-eslint`的第一个配置项 `List of scopes to run eslint on`，让eslint生效的文件，在末尾追加

`text.html.vue`，重启atom编辑器。

##### 常用eslint配置

使用的一些第三方规则，有一些使用不太习惯的，例如语句末尾不能加分号、只能使用单引号等等，下面提供修改规则的方法。

我们可以在 `eslintrc.js`文件中修改，文件内容如下，一般我们只需要修改rules属性中的值即可

``` javascript
module.exports = {
  root: true,
  env: {
    node: true
  },
  extends: [
    'plugin:vue/essential',
    '@vue/standard'
  ],
  parserOptions: {
    parser: 'babel-eslint'
  },
  rules: {
    'no-console': process.env.NODE_ENV === 'production' ? 'error' : 'off',
    'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off',
  }
}
```

#### 规则设置

eslint规则有三种状态

- off：关闭规则
- warn：开启规则，使用警告级别的错误，warn不会导致程序退出
- error：触发时程序退出

##### 语句末尾必须分号结束

```javascript
module.exports = {
  ...,
  rules: {
   'semi': ["error", "always"]
  },
  ...
}
```

- always代表语句末尾必须使用分号

##### 字符串必须使用双引号

``` javascript
module.exports = {
  ...,
  rules: {
    "quotes": ["error","double"]
  },
  ...
}
```

还有一些规则可以参照eslint官网进行设置

#### eslint-plugin-vue相关配置

如果想要对`.vue`，做相应的规则，还是修改`eslintrc.js`

```javascript
module.exports = {
  ...,
  rules: {
  	//设置缩进
    "vue/html-indent":["error",4],
    //设置单/双引号
    "vue/html-quotes":["error","double"]
  },
  ...
}
```

可以看到所有规则都由vue开头，更多的设置及用法可以看看[eslint-plugin-vue官网](https://eslint.vuejs.org/rules/v-on-style.html)