### 利用终端上传文件到GitHub

- 在GitHub上新建repository
- 配置ssh
  - mkdir .ssh    创建ssh证书
  - cd .ssh    进入到ssh证书目录
  - ssh-keygen -t rsa -C "wenlistudent@163.com"   生成私钥,公钥
  - pbcopy< ~/.ssh/id_rsa.pub     把私钥复制到粘贴板
- 在GitHub的Settings页面添加刚刚配置的ssh
- ssh -T git@github.com   把证书和GitHub关联
- 上传代码
  - cd / ——进入到你要上传的工程所在目录
  - git init ———初始化git
  - git add . ————添加
  - git commit -m ""———在""内添加日志,这步可以省略
  - git remote add origin <https://github.com/xxx/xxx> ———-和自己的仓库建立远程链接,链接可以在你的GitHub仓库中获得
  - git pull origin master ————拉取
  - git push -u origin master ————推送

