SolidUI项目发版流程
-------------------------

## 授权

现在都是PMC成员发起发版流程，有发版本权限。

## 物料包
### 分支
从待发布分支拉取新分支作为待发布分支，如现在要发布${release_version}版本，则从待发布分支拉取新分支release-${release_version}-${condition_version}， 此后所有操作都在release-${release_version}-${condition_version}分支上进行。

### 基于待发布的开发分支，创建release-${release_version}-rcx分支

如当前开发的源码分支为dev-1.1.2，需要发布1.1.2的版本，创建分支：release-1.1.2-rc1

