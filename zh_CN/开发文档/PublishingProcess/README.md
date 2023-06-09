SolidUI项目发版流程
-------------------------

## 授权

现在都是PMC成员发起发版流程，有发版本权限。

## 物料包
### 分支
从dev分支作为待发布分支，如现在要发布${release_version}版本，则从待发布分支拉取新分支release-${release_version}-${condition_version}， 此后所有操作都在release-${release_version}-${condition_version}分支上进行。

### 基于待发布的开发分支，创建release-${release_version}-rcx分支

如当前开发的源码分支为dev，需要发布0.1.0的版本，创建分支：release-0.1.0-rc1

### clone对应的release分支到本地
```shell
#-b release-0.1.0-rc1 指定clone分支  -c(config) 指定使用的配置  core.autocrlf=false 关闭自动换行符的转换
git clone -b release-0.1.0-rc1  -c core.autocrlf=false  git@github.com:CloudOrc/SolidUI.git 
```

## 版本号确认

## 验证物料包

准备的物料最好在window和类unix系统中都进行验证，避免系统兼容问题 如换行符问题

## 发起投票

### 社区投票阶段

issue 发起投票，PMC需要先按照文档检查版本的正确性，然后再进行投票。 至少统计到3个+1 PMC member 票后，才能结束投票。

### 关闭投票线程

如果投票已达到所需票数后，进行结果统计前，需要直接回复投票邮件，说明关闭本次投票线程。

### 取消投票（如果需要取消）

如果反馈了一些严重问题，需要修复后，重新发布，则需要取消投票，发布经理需要新起取消投票issue并进行说明。

### 宣布投票结果

issue 公布结果

## 正式发布

### GitHub 版本创建

进入到创建页面 https://github.com/CloudOrc/SolidUI/releases/new 基于之前SolidUI-0.1.0-rc1分支创建名为0.1.0的tag， 填写标题SolidUI Release-0.1.0，将该版本的release notes 写入

检查

合并${release_version}-RC分支到master分支(如果未合并)
