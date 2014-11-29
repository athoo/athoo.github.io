---
layout: post
title: google form script notes
excerpt: "study and write google script."
tags: [google, code]
comments: true
---

##google form script notes

everything is function

	a function include all the codes, named function name(){}
	object doc(also a var)
	var doc = DocumentApp.create(name)
	the method of object doc
	
	.getBody().appendParagraph()
	.getUrl()
	.getName()
	
	Session.getActiveUser().getEmail()
	
	GmailApp.sendEmail(address,subject,body)
	
	ctrl+space 自动补全
	cmd+R

## Notes of google service api

how to use google service to see the file name in google drive

	import gdata.docs.service
	client = gdata.docs.service.DocsService()
	client.ClientLogin('account name','account password')
	document_feed = client.GetDocumentListFeed()
	for item in document_feed.entry:
		print item.title.text