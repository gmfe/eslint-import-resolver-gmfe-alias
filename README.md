使用 webpack alias 的时候，eslint 会报错 import/no-unresolverd 错误。
官方有提供 eslint-import-resolver-webpack 解决，但是会运行 webpack.config.js 获取 config.resolver.alias 配置，这样就做了没有必要的开销。受不了

于是折腾了个插件...

# 使用

安装

```
yarn add eslint-import-resolver-gmfe-alias
```

然后配置eslint，比如 `.eslintrc.js`

```
module.exports = {
  ...
  settings: {
    'import/resolver': {
      // 配置 alias,和 webpack config.resolver.alias 保持一致即可
      'gmfe-alias': {
        common: path.resolve(__dirname, 'js/common/'),
        stores: path.resolve(__dirname, 'js/stores/'),
        svg: path.resolve(__dirname, 'svg/'),
        img: path.resolve(__dirname, 'img/')
      }
    }
  }
}
```
