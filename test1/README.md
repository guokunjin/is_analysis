# 实验1：业务流程建模
|学号|班级|姓名|照片|
|:-------:|:-------------: | :----------:|:---:|
|201510414108|软件(本)15-1|郭昆进|![flow1](../head.jpg)|

## 流程图1：考试及成绩管理流程

**PlantUML源码如下：**

``` flow1
@startuml
title 期末考试流程
start
:安排考试;
:考试安排表]
:出卷;
fork
:A、B试卷]
fork again
:打印审批表]
:审批签字;
:打印审批表]
end fork
:打印试卷;
:试卷]
:参加考试;
:答卷]
:阅卷出成绩;
fork
:成绩单]
if(有不及格?) then(有)
:安排补考;
endif
:补考安排表]
fork again
:答卷]
:装订存档;
end fork
:期末流程结束;

stop

@enduml
```

**业务流程图如下：**

![flow1](flow1.jpg)

**流程说明：**

说明文字....

## 流程图2： 客户维修服务流程

**PlantUML源码如下：**

``` flow2
@startuml
title 客户维修服务流程
start
:申请服务;
if(是新客户吗?) then(是)
      :登记客户信息;
else(不是)

endif
:上门勘察;
:制定方案;
if(满意吗?) then(否)
   stop
else(是)
:签订服务合同;
fork
:安排工人;
fork again
:安排材料;
end fork
:填写订单;
:领取材料;
:上门服务;
:验收并填写反馈意见;
:交回派工单;
:结算收款;
stop
@enduml
```

**业务流程图如下：**

![flow2](flow2.jpg)

**流程说明：**

说明文字....

