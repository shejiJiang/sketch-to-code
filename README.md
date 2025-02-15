# sketch-to-code

## Installation

- [Download](../../releases/latest/download/sketch-to-code.sketchplugin.zip) the latest release of the plugin
- Un-zip
- Double-click on sketch-to-code.sketchplugin

## Development Guide

_This plugin was created using `skpm`. For a detailed explanation on how things work, checkout the [skpm Readme](https://github.com/skpm/skpm/blob/master/README.md)._

### Usage

Install the dependencies

```bash
npm install
```

Once the installation is done, you can run some commands inside the project folder:

```bash
npm run build
```

To watch for changes:

```bash
npm run watch
```

Additionally, if you wish to run the plugin every time it is built:

```bash
npm run start
```

### Custom Configuration

#### Babel

To customize Babel, you have two options:

- You may create a [`.babelrc`](https://babeljs.io/docs/usage/babelrc) file in your project's root directory. Any settings you define here will overwrite matching config-keys within skpm preset. For example, if you pass a "presets" object, it will replace & reset all Babel presets that skpm defaults to.

- If you'd like to modify or add to the existing Babel config, you must use a `webpack.skpm.config.js` file. Visit the [Webpack](#webpack) section for more info.

#### Webpack

To customize webpack create `webpack.skpm.config.js` file which exports function that will change webpack's config.

```js
/**
 * Function that mutates original webpack config.
 * Supports asynchronous changes when promise is returned.
 *
 * @param {object} config - original webpack config.
 * @param {boolean} isPluginCommand - whether the config is for a plugin command or a resource
 **/
module.exports = function(config, isPluginCommand) {
  /** you can change config here **/
}
```

### Debugging

To view the output of your `console.log`, you have a few different options:

- Use the [`sketch-dev-tools`](https://github.com/skpm/sketch-dev-tools)
- Run `skpm log` in your Terminal, with the optional `-f` argument (`skpm log -f`) which causes `skpm log` to not stop when the end of logs is reached, but rather to wait for additional data to be appended to the input

### Publishing your plugin

```bash
skpm publish <bump>
```

(where `bump` can be `patch`, `minor` or `major`)

`skpm publish` will create a new release on your GitHub repository and create an appcast file in order for Sketch users to be notified of the update.

You will need to specify a `repository` in the `package.json`:

```diff
...
+ "repository" : {
+   "type": "git",
+   "url": "git+https://github.com/ORG/NAME.git"
+  }
...
```


## FAQ
### 开发过程中, 插件不能过去
手工建立软链接;类似于
```shell
➜  my-plugin pwd
/Users/dong/Library/Application Support/com.bohemiancoding.sketch3/Plugins/my-plugin
➜  my-plugin ll
total 0
lrwxr-xr-x  1 dong  staff  51 10 14 09:35 my-plugin.sketchplugin -> /Users/dong/Falcon/my-plugin/my-plugin.sketchplugin
➜  my-plugin
```


建立软链接执行以下命令
```shell
ln -s /Users/dong/Falcon/sketch-to-code/sketch-to-code.sketchplugin/ ~/Library/Application\ Support/com.bohemiancoding.sketch3/Plugins/sketch-to-code
```

### 节点合并规则

以水平布局, 垂直布局去合并元素;



## sektch设计稿处理技巧
### img-cook指令 " -合并",把相关区域合成一个图片;