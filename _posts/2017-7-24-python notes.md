---
layout: post
title: Python notes
excerpt: "study and write python."
tags: [python, code]
comments: true
---

###读写文件的一些操作

	a=' hello'
	a.strip()
	'hello'
	
	b='aaa@bbb'
	b.split('@')
	['aaa','bbb']
	
	lists = fin.readlines()#将文件读入list[]中
	
	for item in lists:
		item = item.replace('\n',' ')#将list中每个元素（string）其中的换行符变成空格
		a=a+item#合并为一个大的string
	
	b=a.split(' ')#根据大string其中存在的特殊符号进行划分构建出一个有用的list[]
	
	set(b)#直接去除重复值
	
	sorted(list_name,key = lambda list_name:listname[position],reverse=True)#排序方法
	
	'symbol'.join(object)#help convert list to string
	
	复制list，区别于引用的概念
	NEW = OLD[:]
	
	x in list[]#to see whether x is in list[]
	
	["foo","bar","baz"].index('bar')#throw errorexception if not found
	
	