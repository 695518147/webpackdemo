##概念
本质上，webpack 是一个现代 JavaScript 应用程序的静态模块打包器(module bundler)。

###1.entry
来指定一个入口起点（或多个入口起点）。默认值为 ./src

```javascript

// 语法：entry: string|Array<string>

const config = {
  entry: './path/to/my/entry/file.js'
};

module.exports = config;
// entry 属性的单个入口语法，是下面的简写：

const config = {
  entry: {
    main: './path/to/my/entry/file.js'
  }
};

```
当你向 entry 传入一个数组时会发生什么？向 entry 属性传入「文件路径(file path)数组」将创建“多个主入口(multi-main entry)”。在你想要多个依赖文件一起注入，并且将它们的依赖导向(graph)到一个“chunk”时，传入数组的方式就很有用。


###2.output

在 webpack 中配置 output 属性的最低要求是，将它的值设置为一个对象，包括以下两点：

filename 用于输出文件的文件名。
目标输出目录 path 的绝对路径。

```javascript

const config = {
  output: {
    filename: 'bundle.js',
    path: '/home/proj/public/assets'
  }
};

module.exports = config;

```

#####多个入口起点
如果配置创建了多个单独的 "chunk"（例如，使用多个入口起点或使用像 CommonsChunkPlugin 这样的插件），则应该使用占位符(substitutions)来确保每个文件具有唯一的名称。

```javascript

{
  entry: {
    app: './src/app.js',
    search: './src/search.js'
  },
  output: {
    filename: '[name].js',
    path: __dirname + '/dist'
  }
}

// 写入到硬盘：./dist/app.js, ./dist/search.js

```


