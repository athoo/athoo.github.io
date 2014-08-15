---
layout: post
title: "rubystudy
excerpt: "help learn ruby"
tags: [others]
comments: true
---


##RUBY notes

### generally used function

	.sort
	.reverse
	.to_s.reverse
	.to_a#convert to array
	.length
	.max
	stringname['substring']='replacing string'
	.lines­.to_a.reve­rse.join# replace lines with chars and bytes
	.eqls/==/=~/===	#注意他们的不同
	.object_id
	.equal?
	.each{| |
		....
		}
	number.times {
	...
	}
	for i in a..b
		..
	end
	for a in as
	...
	end
	until 条件 do #until 的意思与while 恰好相反
	statements
	end
	loop{...}
	break # the usage has not been changed 
	next # like continue, just skip the round to next cycle
	redo # add a loop comaring with the action of next ,(skip the round)
	
	
	

### interesting new usage

	unless 条件 then # 与if恰好相反的用法
		statement
	end

	case 对象
	when valueX then
		statementX
	...

	
	
### 关于变数

- 区域变数(local)

		名称以 小写字母 表示 或者 是以 _ 起始的变数

- 全域变数(global)

		名称以 $ 开始的变数# 考虑require的存在会使得相同名字的变数出现在一份文件中

- 实体变数

		名称以 @ 开始的变数，对利用new产生的多个不同的对象，其中同样名字的变量例如，@name，的值各不相关，是由new时候传入的数值所决定的
		


- 类别变数

		名称以 @@ 开始的变数 ,类别所有的实体公用的变数，例如：@@count， 在多次调用后数值会实际累加
	


- 虚拟变数

		true, false, self 等特定名称的变数
		
### 关于方法

- 实体方法	常规的.method

- 类别方法	Time.new 之类的方法

- 函数性的方法	sin(3.14)之类的方法


限制方法的呼叫

- public 将方法公开为外部可以使用的实体方法

- private 将方法限制为只有内部可以使用（不允许接在接收者后面呼叫）

- protected 将方法限制为只有内部可以使用。另外，在同一个类别内可作为实体方法使用

对方法的直接调用，只需要表示为 :methodname 即可

public后面不直接加方法则表示其后面的所有方法都符合其定义



		
### 命名法则

- eg: sort_list_by_name

		用作命名变数，方法的名称
		
- eg: sortByName

		用作命名类别名称，类别名必须大写开头
		
		
		
		
### class initialization 

class name <父类别名
	def initialize(variable="")
		@变量名 = variable
	end
	...
	end

		
		
		
		
#### class 中定义的存取方法

- attr_reader :name

- attr_writer :mame

- attr_accessor :name

- 外部存取class中的常数 classname  ::  variable


### module 

	module MyModule
	...
	end
	
	class Myclass1
		include MyModule
		...
	end
	
	...
	
	when define the module, we should add module_dunction :function_name after finishing definition of the specific module methods in the module
	
	
### Error and Exception

understanding the meaning of the exception throwout

	eg: test.rb:2:in 'open':No such file or directory - "no/file"(Errno::ENOENT)
		from test.rb:2:in 'foo'
		...
	format explanation: Filename:line_number : in 'method_name': error information (exception type)
		from the place calling the method
		
		
	The way ruby manage the error
	
	begin
		possible action incuring the exception
	rescue => ex
		what to do when exception appears
	ensure (thatever the exception appears the action must be done)
	end
	
	variable of teh exception
	$!
	$@
	their methods
	class message backtrace
	
	incur the exception 
	raise xxx
	