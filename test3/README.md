# 实验3：图书管理系统领域对象建模
|学号|班级|姓名|照片|
|:-------:|:-------------: | :----------:|:---:|
|201510414108|软件(本)15-1|郭昆进|![flow1](../head.jpg)|

## 1. 图书管理系统的类图

### 1.1 类图PlantUML源码如下：

``` class
@startuml
class Reserve_预借信息类{
    +String  ISBN
    +String  readerId
    +int  number
    +Data  data
    +add()
    +delete()
    +update()
    +get()
}
class Lend_借阅信息类{
    +String  ISBN
    +String  readerId
    +Data  lenddata
    +Data  returndata
    +boolean  isOvertime
    +add()
    +delete()
    +get()
}

class Lender_借阅者{
    +String  ID
    +String  name
    +String  sex
    +String  role
    +int  maxBorrowNum
    +int  maxBorrowDays
    +int  borrowNum
    +select()
    +borrow()
    +xujie()
    +yujie()
    +returnBook()
    +findBook()
}
class BookInfo_图书信息类{
    +String  ISBN
    +BookDescribeInfo bookDes
    +int  status
    +add()
    +select()
    +delete()
    +update()
    +setStatus()
}
class BookDescribeInfo_图书描述{
    +String ISBN
    +String bookName
    +String type
    +List<String> catalog
    +String describe
}
class teacher{
    +String role="teacher"
}
class student{
    +String role="student"
}
class admin_管理员{
    String adminID
    int accessLevel
    adminMethod()
}
teacher --|> Lender_借阅者:Extension
student --|> Lender_借阅者:Extension
BookDescribeInfo_图书描述 --* BookInfo_图书信息类:Composition
Lender_借阅者 ..> BookInfo_图书信息类
Lender_借阅者 ..> Reserve_预借信息类
Lender_借阅者 ..> Lend_借阅信息类
BookInfo_图书信息类 <.. admin_管理员
Reserve_预借信息类 <.. admin_管理员
Lend_借阅信息类  <.. admin_管理员
@enduml
```

### 1.2. 类图如下：

![class](classes.png)

### 1.3. 类图说明：
```
图书管理系统能够对图书进行注册登记，也就是将图书的基本信息
（如编号、书名、价格、作者等）预先存入数据库中，供以后检索，
并且能够对借阅人进行注册登记，包括记录借阅人的姓名、编号、
班级、年龄、性别、地址、电话等信息。同时，图书管理系统提高
方便的查询方法。如以书名、作者、出版社、出版时间等信息进行
图书检索，并能反映出图书的借阅情况；以借阅人编号对借阅人信
息进行检索；以出版社名称查询出版社联系方式等信息。图书管理
系统提供对书籍进行预订的功能，也提供旧书销毁功能，对于淘汰、
损坏、丢失的书名可及时对数据库进行修改。图书管理系统能够对
使用该管理系统的用户进行管理，按照不同的工作职能提供不同的
功能授权。总的来说，图书管理系统主要包含下列功能。  
1）读者管理：读者信息的制定、输入、修改、查询，包括种类、性别、借
	书数量、借书期限、备注等。  
2）书籍管理：书籍基本信息制定、输入、修改、查询，包括书籍编号、类别、关键词、备注。  
3）借阅管理：包括借书、还书、预订书籍、续借、查询书籍、过期处理和书籍丢失后的处理。  
4）系统管理：包括用户权限管理、数据管理和自动借还机的管理。
```




## 2. 图书管理系统的对象图
### 2.1 类Reserve
#### 源码如下：
``` class
@startuml
class Reserve_预借信息类{
    +String  ISBN
    +String  readerId
    +int  number
    +Data  data
    +add()
    +delete()
    +update()
    +get()
}
@enduml
``` 
#### 对象图如下：
![class](reserve.png)
#### 说明：
```
Reserve：预借信息类
	属性：
		ISBN：图书编号
		readerId：读者ID
		number：预借数量
		data：借书日期
	方法：
		add()：添加一条预借记录
		delete()：删除一条预借记录
		update()：修改预借记录
		get():获取预借信息
```

### 2.2 类Lend
#### 源码如下：
``` class
@startuml
class Lend_借阅信息类{
    +String  ISBN
    +String  readerId
    +Data  lenddata
    +Data  returndata
    +boolean  isOvertime
    +add()
    +delete()
    +get()
}
@enduml
``` 
#### 对象图如下：
![class](lend.png)

#### 说明：
```
Lend：借阅信息类
	属性：
		ISBN：图书编号
		readerId：读者ID
		lenddata：借书日期
		returndata：还书日期
		isOvertime：是否超时
	方法：
		add()：添加一条借书记录
		delete()：删除一条借书记录
		get():获取借书信息
```
### 2.3 类Lender
#### 源码如下：
``` class
@startuml
class Lender_借阅者{
    +String  ID
    +String  name
    +String  sex
    +String  role
    +int  maxBorrowNum
    +int  maxBorrowDays
    +int  borrowNum
    +select()
    +borrow()
    +xujie()
    +yujie()
    +returnBook()
    +findBook()
}
@enduml
``` 
#### 对象图如下：
![class](lender.png)

#### 说明：
```
Lender：借阅者
	属性：
		ID：读者ID
		name：姓名
		sex：性别
		role：借阅者类型
		maxBorrowDays：最大借阅天数
		maxBorrowNum:最大借阅数量
		borrowNum:已借数量
	方法：
		select()：查询自己的借阅记录
		borrow()：借书
		xujie():续借图书
		yujie():预借图书
		returnBook()：归还图书
		findBook():查询图书信息
```

### 2.4 类BookInfo
#### 源码如下：
``` class
@startuml
class BookInfo_图书信息类{
    +String  ISBN
    +BookDescribeInfo bookDes
    +int  status
    +add()
    +select()
    +delete()
    +update()
    +setStatus()
}
@enduml
``` 
#### 对象图如下：
![class](bookInfo.png)

#### 说明：
```
BookInfo：图书信息类
	属性：
		ISBN：图书编号
		bookDes：图书信息描述
		status：图书状态：标记借出、预借、可借阅状态
	方法：
		add()：添加图书
		delete()：删除图书
		select():查询图书
		updata():更新图书
		setStatus():设置图书状态
```
### 2.5 类BookDescribeInfo
#### 源码如下：
``` class
@startuml
class BookDescribeInfo_图书描述{
    +String ISBN
    +String bookName
    +String type
    +List<String> catalog
    +String describe
}
@enduml
``` 
#### 对象图如下：
![class](bookDescribeInfo.png)

#### 说明：
```
BookDescribeInfo：图书描述类
	属性：
		ISBN：图书编号
		bookName：书名
		type：图书类型
		catalog：目录
		describe：图书简介
```