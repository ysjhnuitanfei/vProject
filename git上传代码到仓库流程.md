# 作者：知乎其微
# 编辑于：2018-05-21 16:30

<h3>如果将自己本地的代码托管到git仓库&&创建远端分支</h3>
<h3>如何克隆别人仓库的代码，然后修改后提交</h3>

一：将本地代码上传到git仓库
1、
	1.1-登录你的git账号，选择右上角的“+”号，选择New repository
	1.2-为你的项目起一个名字；如：demo
	1.3-点击下面Create repository按钮保存
2、
	2.1-创建完之后页面会有这么一个地址：https://github.com/ysjhnuitanfei/demo.git，这个地址就是你这个demo仓库的地址
	2.2-复制这个地址，然后去电脑：d盘（自己随意），鼠标右键>Git Bash Here(或者你可以用node命令都可以)，然后会出现git命令工具
	2.3-在命令行执行拉取我们的仓库，地址为你刚刚你复制的地址，如：git clone https://github.com/ysjhnuitanfei/demo.git(PS:你也可以直接可以鼠标右键，选择Git 克隆)
	
到此我们的基本工作就做好了

3、
	3.1-在我们的demo文件夹下将你的代码拷贝进来，或者自己创建一些文件(注意：readme.md文件必须存在)
	3.2-在命令行执行： git init  //初始化
	3.2-执行： git add .   //将项目的所有文件添加到仓库中
	3.3-到这里我们执行以下： git remote -v  //看看我们是否关联了我们的仓库地址
	3.4-执行： git push origin master:master  //将本地分支master推送到远端
	
到此我们git仓库就已经有我们上传的代码了

二：创建本地&&远端分支&&合并分支
1、
	1.1-执行： git chekout -b dev  //创建dev分支并切换，或者可以这样(git branch dev / git checkout dev)
	1.2-执行： git branch  //查看我们分支是否创建完成  *号代表当前所在分支（本地创建完成）
	
	2.1-当要创建远端分支的时候，本地分支需切换到你想要创建远端分支的分支下，比如远端要创建dev分支
	2.2-执行： git push origin dev:dev  //我们去查看git仓库，发现多了一个dev的分支（远端创建完成）
	
	3.1-我们在dev的分支下创建文件或者修改一些文件
	3.2-如果为提交或者拉取省下麻烦，我们可以让本地分支与远端分支的哪一个分支关联一下
	3.3-执行： git branch --set-upstream dev origin/dev  //本地dev分支自动跟踪远端dev分支
	4.3-然后我们上传一下我们刚才修改的到远端dev分支下；
	4.4-合并： 先切换分支到master(git checkout master),然后执行(git merge dev)
	4.5-到此我们就将dev分支的修改合并到master上面了，你可以选择删除本地dev分支(git branch -d dev)
	
	
三：如何克隆别人的仓库代码，修改其中BUG再提交与仓库作者完成合并
1、
	1.1-进入到别人仓库，选择一个项目
	1.2-点击右上角的Fork按钮，再点击refresh按钮，然后你的仓库中就会出现你刚克隆的代码
	1.3-然后在本地将仓库代码git clone出来
	1.4-然后随便修改东西上传
	1.5-进入到仓库中，点击Pull requests选项，进入后点击create a pull request
	1.6-我们会看到看到我们当前的改动指向原作者的仓库，然后我们选择下面的create  pull request按钮，注明改动了什么，在点击编辑框右下角的create pull request按钮
	1.7-到这里我们的步骤就算完了，如果你是原作者的贡献者，你的界面会出现一个Merge pull request按钮，点击后会合并到原作者的对应分支，对方只需要pull即可
	1.8-如果我们不是贡献者，那么原作者会在他的仓库看到改动请求，如果对方查看没问题后可以合并你的更改