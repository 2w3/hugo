---
title: "Hugo"
date: 2017-08-11T19:45:21+09:00
---
## 1. Why Hugo?

계속 까먹는다.  
정리를 해서 적어놨으면 했다.  
그래, 내 milestone이 필요했다.  

[GitHub Page](https://pages.github.com)를 이용하고 싶었다.  
[https://www.staticgen.com](https://www.staticgen.com)에서 찾아보니 엄청 많았다.  

Jekyll이 인기가 많았다.  
Ruby를 잘 몰랐고, 검색해서 Jekyll를 설치하긴 했는데 뭔가 쉽지 않았다.  
무엇보다 남들 많이 쓰는걸 쓰고 싶지 않았다.  

Python을 열심히 보던때라서 Pelican도 살펴봤지만, python3 안정성의 의구심에 관한 아티클이 있었는데, 나도 Python때문에 고생고생하고 있었던때라서 그 부분에 대해서는 공감이 갔다.  
NodeJS로 구성된 Hexo도 있었는데 NodeJS를 구성하고 싶진 않았다.  

빨랐으면 했다.  
Go로 구성된 Hugo가 눈에 들어왔다.  
Go도 안정성에 대한 의구심이 들었지만, 컴파일언어의 속도에 대한 막연한 기대감과 더불어 무엇보다 Ruby, Python, NodeJS보다 더 새로운 언어 Go로 구성되어있다는 새로운것에 대한 막연한 기대감이 마구마구마구 들었다.  

실제로 Jekyll과 Hugo에 데이터를 루프문으로 엄청 밀어넣고 봤을때 Hugo가 Jekyll보다 겁나 빨랐다.  
# 빠르다.  
---
## 2. Hugo
[https://gohugo.io](https://gohugo.io)  
Hugo is one of the most popular open-source static site generators.

SSG 구성은 간단하다.  
SSG = content + assets + layout

Hugo에서 content는 markup으로 작성할 수 있다.  
markup은 쉽고 빠르다.

assets은 필요에 따라 github repository에 올려두고 링크걸어 사용하면 된다.  
github repository를 이용하니까 호스팅 비용같은건 없다.

layout은 hugo에서 제공하는 많은 theme들이 많아 기존걸 이용해도 되고,  
본인이 만들어서 사용해도 된다.  
[https://themes.gohugo.io](https://themes.gohugo.io)

* 빠른 속도
* 쉬운 컨텐츠 관리
* Markdown
* Built-in Templates (SEO, commenting, analytics template 제공)
* 다국어 i18n지원
* Custom Ouputs (JSON, AMP, multiple custom output지원)
* Theme지원

# SSG
---
## 3. Install Hugo
`brew update && brew install hugo`  
Homebrew install 명령어를 통해 Hugo 설치한다.  
# 설치가 쉽다.
---
## 4. Create New Hugo
`hugo new site {new Hugo}` 명령어를 통해 사이트 구성이 가능하다.  
`tree` 명령어로 살펴보면 Hugo는 아래와 같은 구조를 갖는다.
```
.
├── archetypes
│   └── default.md
├── config.toml
├── content
├── data
├── layouts
├── static
└── themes
```
---
## 5. Add Hugo Theme
```
cd {new Hugo}/themes
git clone https://{hugo theme name}.git
cd {hugo theme name} && rm -rf .git
cd {new Hugo} && echo 'theme = "{hugo theme name}"' >> config.toml
```
# Various Theme.  
---
## 6. Create New Content
`hugo new posts/{new content name}.md`  
위 명령어로 md파일을 생성하고,  
해당 md파일 header 아래부분부터 markup을 작성하면 된다.
```
---
title: "My First Post"
date: 2016-04-21T17:04:37+09:00
draft: true
---
{여기서부터 markup 작성}
```
# markup작성이 쉽다.
---

## 7. Server
`hugo server -w`  
-w, --watch  
watch filesystem for changes and recreate as needed  
hugo server watch옵션으로 작성하는 markup hugo 출력을 웹브라우저에서 http://localhost:1313/ 를 통해 확인가능하다.  
# local Draft watching  
---  
## 8. Static Site Generating
`hugo` 명령어를 통해 static stie generating이 가능하다.  
hugo configuration file을 통해 publishDir 별도설정이 가능하다.
설정이 없을 경우 public폴더에 생성한다.

```
Started building sites ...
Built site for language en:
0 draft content
0 future content
0 expired content
1 regular pages created
8 other pages created
0 non-page files copied
2 paginator pages created
0 categories created
0 tags created
total in 4 ms
```  
Site 생성도 쉽고 빠르다.  
---
## 9.Deploy Hugo as a GitHub Pages
```
cd public
git init
git remote add origin git@github.com:{userid}/{userid}.github.io.git
git add . && git commit -m "{commit message}" && git push -u origin master
git checkout --orphan gh-pages && git merge master && git push origin gh-pages
```





