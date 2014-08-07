#The step-by-step tutorial to create the blog

__建立工作文档__

	mkdir project_name
	
__进入文件夹并对目录初始化__

	cd project_name
	git init
	
__创建一个没有父节点的分支gh-pages该分支中的页面将会生成网页文件__
	
	git checkout --orphan gh-pages
	
__创建设置文件__

根目录下建立_config.yml，这个是jekyll的设置配置文件

	baseurl: /project_name
	
__创建模板文件__

在根目录下创建_layouts文件夹，用来放置模板文件

__在_layouts文件夹中创建模板文件__

创建default.html文件，作为blog的默认模板

__在project根目录中创建一个_posts目录，用来存放blog文章__

	mkdir _posts
	
__在_posts文件夹中写文章，html或者是markdown都可以__

	文章头部必须要有一个yaml文件头，设置元数据，三根短线开头---，---结尾
	包括 layout: default
	title: #网页的头显示
	同时，文件必须符合年-月-日-文件名.文件后缀名

__在根目录里需要创建一个index.html或者是md文件__
	
	其中需要放置yaml文件头信息
	
__发布内容__

在根目录下
 
	git add .
	git commit -m "注释说明"
	
在github中建立一个存储仓库project_name

	git remote add alias https://github.com/username/project_name.git
	git push alias gh-pages
	
__目录文件的参考模板__


	　　---
	　　layout: default
	　　title: 我的Blog
	　　---
	　　<h2>{{ page.title }}</h2>
	　　<p>最新文章</p>
	　　<ul>
	　　　　{% for post in site.posts %}
	　　　　　　<li>{{ post.date | date_to_string }} <a href="{{ site.baseurl }}{{ post.url }}">{{ post.title }}</a></li>
	　　　　{% endfor %}
	　　</ul>
	　　
__ _post中文章的参考模板 __

	　　---
	　　layout: default
	　　title: 你好，世界
	　　---
	　　<h2>{{ page.title }}</h2>
	　　<p>我的第一篇文章</p>
	　　<p>{{ page.date | date_to_string }}</p>


__blog的参考默认模板__


	　　<!DOCTYPE html>
	　　<html>
	　　<head>
	　　　　<meta http-equiv="content-type" content="text/html; charset=utf-8" />
	　　　　<title>{{ page.title }}</title>
	　　</head>
	　　<body>
	
	　　　　{{ content }}
	
	　　</body>
	　　</html>
　　
###使用现成模板的整个方法

	git clone https://github.com/krisb/jekyll-template.git mysite
	cd mysite
	rm -rf .git
	git init
	git add -A
	git commit -m 'initial template based on https://github.com/krisb/jekyll-template'
	git remote add origin git@github.com:username/reponame.git
	git push -u origin master
　　
　　
　　
###git 的一些操作技巧

修改本地源名对应的远程地址

	git remote set-url origin https://github....
	
直接删除本地源

	git remote remove origin
　　
显示所有的源

	git remote show origin
　　

<http://gogojimmy.net/2012/01/17/how-to-use-git-1-git-basic/>

<http://richohan.github.io/yong-pelican-github-pagejian-li-ge-ren-bu-luo-ge.html#.U93vku3ka9L>

<https://pages.github.com>

<http://www.ruanyifeng.com/blog/2012/08/blogging_with_jekyll.html>

<http://site.douban.com/196781/widget/notes/12161495/note/264946576/>

<http://jekyllrb.com>

<https://www.andrewmunsell.com/tutorials/jekyll-by-example/introduction>

<http://trefoil.github.io/2013/10/05/jekyll.html>

