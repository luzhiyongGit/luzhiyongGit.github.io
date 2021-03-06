
---

title: Github+Hexo搭建个人博客详细教程

date: 2018-11-10 09:14:00 +0800

categories: Hexo

tags: [教程]

---

<a name="sl6tws"></a>
#### [](#sl6tws)安装Node.js

1. 安装nvm

```powershell
$ curl -o- https://raw.githubusercontent.com/creationix/nvm/v0.30.2/install.sh | bash
```

2. 安装node

```powershell
$ nvm install node
```

3. 验证node是否安装成功

```powershell
$  node -v
$  v8.12.0
```
<a name="t8a8gr"></a>
#### [](#t8a8gr)安装Hexo
```powershell
$ npm install -g hexo
```
安装完成后，进入一个文件夹，执行
```powershell
$ hexo init
$ npm install hexo --save
```
<a name="ua2lyy"></a>
#### [](#ua2lyy)Github创建个人仓库
在Github上创建一个新仓库，并命名为  `你的github用户名.github.io`
<a name="oefdft"></a>
#### [](#oefdft)配置_config.yml
```
deploy:
   type: git
   repository: https://github.com/username/username.github.io
   branch: master
```
<a name="s6t5gs"></a>
#### [](#s6t5gs)编写博客
```
$ hexo new post '文章标题'
```
在source/_posts/ 文件夹下新建了博客，文件格式为markdown，编辑此文件。
<a name="ybauhr"></a>
#### [](#ybauhr)推送站点
```powershell
$ hexo g
$ hexo d
```
上传成功后，访问[https://username.github.io](https://username.github.io)

---

接下来再介绍一些进阶用法：
<a name="padgfi"></a>
#### [](#padgfi)多台电脑管理hexo博客
利用github管理博客内容，进行多台电脑的同步，既可以新建一个仓库单独进行博客内容的管理，也可以在现有仓库的基础上新建一个分支进行管理，相比较而言新建分支管理更加便捷。

1. 新建分支 hexo

2. 在设置里将hexo设置为默认分支

3. clone代码到本地，在hexo分支下进行博客的编写，利用hexo d同步到master分支，同时手动同步到hexo分支

4. 新电脑需要重新安装hexo环境，安装完成后clone代码到本地

<a name="xhgmdd"></a>
#### [](#xhgmdd)绑定个人域名
拥有自己的独立域名能瞬间提升博客的逼格，接下来就是绑定个人域名的流程

1. 购买域名


     一般去阿里云购买，具体流程网上很多，就不再细说

2. 配置DNS地址


     在阿里云后台配置DNS信息，将[https://username.github.io](https://username.github.io)的ip绑定到你想要绑定的域名上

3. 配置hexo文件


     在source目录下，新建文件，命名为`CNAME`，填入域名地址。

4. 发布到github


我的博客地址是[http://blog.ileafly.com](http://blog.ileafly.com)
<a name="yst3oh"></a>
#### [](#yst3oh)绑定语雀管理博客内容
可以利用语雀管理博客内容，非常方便，详细流程可参考[使用语雀管理博客](http://www.ileafly.com/2018/11/09/yuque/使用语雀管理博客/)。
<a name="qvkuep"></a>
#### [](#qvkuep)自定义主题
Hexo有非常非常多的主题，你可以在[Themes | Hexo](https://hexo.io/themes/index.html)浏览这些主题，选择你喜欢的主题进行使用。<br />我比较喜欢的主题是[maupassant](https://github.com/tufu9441/maupassant-hexo)，这里就以[maupassant](https://github.com/tufu9441/maupassant-hexo)为例简述一下集成的流程。
```shell
# 安装
$ git clone https://github.com/tufu9441/maupassant-hexo.git themes/maupassant
$ npm install hexo-renderer-pug --save
$ npm install hexo-renderer-sass --save

# 修改博客配置文件 `_config.yml` 主题属性 theme 为 `maupassant`
# 更多的配置信息可以参考ReadMe
```
<a name="ctisce"></a>
#### [](#ctisce)集成评论
Gittalk是基于Github issues开发的评论系统，每一篇文章对应一个issues，issues里面的评论对应文章的评论，这样对于利用GitHub搭建的博客来说简直是完美的搭配。

1. 创建一个OAuth Application
- 访问 [https://github.com/settings/applications/new](https://github.com/settings/applications/new)
- 随意填写一个Application Name
- 在Homepage URL一栏填入博客的地址：https://ileafly.github.io
- 在Authorization callback URL一栏同样填入博客的地址：https://ileafly.github.io
- 创建应用，得到 `Client ID` 和 `Client Secret` 
2. 修改主题配置，填入 `Client ID` 和 `Client Secret` 

```ruby
gittalk:
  enable: true ## If you want to use Gitment comment system please set the value to true.
  owner: ileafly ## Your GitHub ID, e.g. username
  repo: ileafly.github.io ## The repository to store your comments, make sure you're the repo's owner, e.g. imsun.github.io
  client_id: ## GitHub client ID, e.g. 75752dafe7907a897619
  client_secret: ## GitHub client secret, e.g. ec2fb9054972c891289640354993b662f4cccc50
  admin: ileafly
```



