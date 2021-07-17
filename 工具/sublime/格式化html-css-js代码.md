- 本地安装node

- 本地安装sublime Text3

- 安装HTML-CSS-JS Prettify插件

  - 在Sublime Text 3中，按下Ctrl+Shift+P调出命令面板
  - 输入install 调出 Install Package 选项并回车
  - 输入pretty，并在列表中选择HTML-CSS-JS Prettify后回车即可安装

- 配置node路径

  - 在dos命令下，输入where node并回车查看node安装路径

  - 在Sublime Text 3中，按下Ctrl+Shift+P调出命令面板

  - 输入install 调出 htmlprettify.sublime-settings 选项并回车

  - 在配置文件中修改node路径为本机安装路径

    - >"node_path":
      >    {
      >        "windows": "F:/node/node.exe",
      >        "linux": "/usr/bin/nodejs",
      >        "osx": "/usr/local/bin/node"
      >    },

- 使用
  - 在sublime中打开需要格式化的html-css-js文件
  - 任意位置右键选择 `HTML/CSS/JS Prettify`
  - 再选择`Prettify Code`实现格式化代码