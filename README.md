Dev Container For Vue3 & TS & Yarn & yrm
==========

### 说明
- vscode用户设置json补充`"dev.containers.copyGitConfig": false`防止自动拷贝宿主机git配置文件到容器内（也可以通过GUI界面-设置-用户-扩展-Dev Containers-Dev>Containers: Copy Git Config 取消勾选）

- 容器创建后会自动将此项目根目录映射到容器内`/workspace/当前文件夹名称`

### 开发
- 容器内git代理设置（宿主机代理需要设置允许局域网访问）
    - git config --global http.proxy 'http://[宿主机局域网IP]:7890'
    - git config --global https.proxy 'http://[宿主机局域网IP]:7890'

- vscode新建终端会进入容器内的shell，进入到容器内`/workspace/当前文件夹名称`，使用`git clone`拉取项目进行开发