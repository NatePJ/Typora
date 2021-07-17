- 1、在GitHub上建立一个分支`repositories`，命名为 `GitHubname.GitHub.io`

- 2、hexo创建的博客文件夹下的`_config.yml`文件打开更改配置

  - > deploy:
    >   type: git
    >   repo: https://github.com/NatePJ/NatePJ.GitHub.io.git
    >   branch: master

  - > url: https://natepj.github.io/

- 3、安装`hexo-deployer-git`
  - 在本地博客文件地址cmd输入以下命令安装`npm install hexo-deployer-git --save`

- 4、在博客地址cmd输入以下命令上传文件到GitHub

  ​		`hexo d`

- 5、打开浏览器输入网址`https://natepj.github.io/`浏览已经搭建并上传的本地主页

