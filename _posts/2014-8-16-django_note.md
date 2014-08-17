	django-admin.py startapp name_of_app
	cd route_to_app
	templates放在application下面
	static放在app下面放一些静态资料
	回到目录的设定的位置，settings之中
	在install apps里面加上自己新建的app
	加一个STATIC_DIRS=(加入资料的绝对文档位置)
	加一个TEMPLATE_DIRS=(加入templates的绝对文档位置)
	加一个STATIC_ROOT = ''作为存储static 里面内容远程推送的位置
	
	修改url，将app的地址对应match好
	在app下面的url也要修改好对应
	后面在view中设置response和动态产生的资料
	
	插入：
		vim的功能：vertical vsp default horizontal sp 加档案名字可以产生新的窗口，ctrl+w后再按方向键可以切换激活窗口
	
	问好是get parametor的起始符号
	
	小结与思考：
	project下的url所担当的作用主要是域名解析和指向，使得url的请求对应的不同的app下面的urls解析之中（一级分地址）
	在被指向的app其url中需要建立在一级分地址下的地址中去匹配到地址对图示的对应关系，图示以method的方式被反馈出来，可以对这一url的对应关系做一个姓名的标识以简化日后template中的调用
	views中的method，有用的函数，request.GET.get("key_name","default_value")#常用的根据url的表现形态做parsing以及收集获取数据资料的方式，相对应POST在更复杂的需求下使用
	render(request,"template",value_passed_to_the_template(often a dictionary name))
	而在template中需要对待换的地方传入dictionary的key的名字，帮助查询工作的完成