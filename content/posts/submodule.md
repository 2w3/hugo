---
title: "Submodule"
date: 2017-08-29T17:52:48+09:00
---

## 1. git submodule

repository에서 다른 repository를 하위 directory형태로 관리할 수 있도록 해준다.  
다른 repository를 directory형태로 포함하는 repository를 superproject라 부른다.  
submodule repository는 submodule id, submodule path와 submodule repository url를 저장하여 superproject와 구분한다.  

## 2. create submodule
`git submodule add {repository url} {submodule name}`

`cat .gitmodules`
```
[submodule "swift-style-guide"]
	path = swift-style-guide
	url = https://github.com/github/swift-style-guide
```	
`git commit -a -m {commit message}`  
`git push`  

## 3. update submodule
`git submodule init`  
`git submodule update`  

다수의 submodule update  
`git submodule foreach 'git pull'`  

## 4. remove submodule
`git submodule deinit -f -- {submodule path}`  
`rm -rf .git/modules/{submodule path}`  
`git rm --cached {submodule path}`  
don't include a trailing slash --that will lead to an error.

