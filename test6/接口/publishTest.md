<!-- markdownlint-disable MD033-->
<!-- 禁止MD033类型的警告 https://www.npmjs.com/package/markdownlint -->

# 接口：publishTest  [返回](../README.md)
用例： [发布实验](../用例/发布实验.md)

- 功能：
    教师发布新的实验任务。
    
- 权限：
    老师  
    
- API请求地址： 
    接口基本地址/v1/api/publishTest

- 请求方式 ：
    POST

- 请求实例：

        {
            "course_id":1,
            "title":"实验1",
            "desc":"本实验的目的是了解PlantUML标准，搭建系统分析文档编写平台，并能绘制出一些简单的业务流程。
                    重新绘制Page107图6.1: 考试及成绩管理流程
                    重新绘制Page108图6.2: 客户维修服务流程
                    重新绘制的两个流程图要汇总到REMADE.md文本文件中进行说明，说明文件用Markdown格式编写。",
            "link":"https://github.com/zwdbox/is_analysis/blob/master/test1.md"
        }
        
- 请求参数说明:        

  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |course_id|实验所属课程的编号|
  |title|实验的标题| 
  |desc|实验的描述|
  |link|实验的详细介绍地址（github）|
  
- 返回实例：

        {         
            "status": true,
            "info": null,    

        }
 
- 返回参数说明： 
 
  |参数名称|说明|
  |:---------:|:--------------------------------------------------------|      
  |status|bool类型，true表示正确的返回，false表示有错误|
  |info|返回结果说明信息|


