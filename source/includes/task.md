#任务操作接口

##创建任务接口

###功能说明：

通过此接口可以创建新的任务

###更新说明：

创建任务,支持使用多个无主叫固话,只需设置总坐席数,由系统自动分配每个线路的坐席数量。
注意：
1.ai坐席数的总数可在crm界面企业账户中看到
2.开启重拨需要的枚举
0   已接听
1   拒接
2   无法接通
3   主叫号码不可用
4   空号
5   关机
6   占线
7   停机
8   未接
9   主叫欠费
10  呼损
11  黑名单

>入参JSON示例：

```
{
    "companyId" : 1, 
    "taskName" : "测试任务", 
    "taskType" : 2, 
    "startDate" : "2017-10-19",
    "workingStartTime" : "08:00",
    "workingEndTime" : "22:00", 
    "breakStartTime" :"12:00",
    "breakEndTime" : "13:00",
    "userPhoneIds" : [1], 
    "callType" : 0, 
    "concurrencyQuota" : 1, 
    "robotDefId" : 1, 
    "sceneDefId" : 1, 
    "sceneRecordId" : 7, 
    "concurrencyQuota":1,
    "smsType":1,
    "remark" : "创建任务",
    "repeatCall": true,
    "repeatCallPhoneStatus": 1,
    "repeatCallTimes": 1,
    "repeatCallInterval": 2
    }
```

>返回对象示例：

```
{
    "code": 200,
    "data": 67, //返回刚刚创建的任务ID
    "resultMsg": "操作成功",
    "errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/task/createTask

###请求方法：

POST

###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |----------
 companyId| int| 是 | 公司Id| 1 |
 taskName| String| 是 |任务名称| 测试API任务 |
 taskType| int| 是 | 任务类型, 1-定时,2-手动| 1 |
 startDate| String| 是 | 任务开始日期| "2017-10-19"  |
 workingStartTime| String| 否 | 可拨打开始时间| 08:00 |
 workingEndTime| String| 否 | 可拨打结束时间| 22:00 |
 breakStartTime| String| 否 | 暂时停止开始时间| 12:00 |
 breakEndTime| String| 否 | 暂时停止结束时间| 13:00 |
 userPhoneIds| int| 是 | 主叫电话号码id列表，详见获取公司的主叫电话列表(getPhones)接口| [1,2] |
 sceneDefId| int| 是 | 场景id| 1 |
 robotDefId| int| 是 | 机器人id| 1 |
 sceneRecordId| int| 是 | 机器人话术录音id| 1 |
 callType| int| 是 | 主叫号码类型，0-sim卡,1-固话（默认）, 2-无主叫| 1 |
 concurrencyQuota| int| 否 | ai坐席数，默认1| 1 |
 remark| String| 否 | 备注| 测试|
 repeatCall|boolean|否|是否开启重拨|
 repeatCallPhoneStatus|String|否| 需要开启重拨的通话状态{"1","2"} |
 repeatCallTimes|int|否| 重拨次数 |
 repeatCallInterval|int|否| 重拨间隔时长（分钟） |
 



###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码 |
 data|int | 刚刚创建的任务ID |
 resultMsg| String | 响应说明 |

##启动任务接口

###功能说明：

通过此接口可以启动指定的任务

>返回对象示例：

```
{
    "code": 200,
    "data": null,
    "resultMsg": "启动成功",
    "errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/task/start

###请求方法：

POST


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |----------
 taskId| int| 是 | 任务Id| 1 |


###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码 |
 resultMsg| String | 响应说明 |
 
##暂停任务接口
 
###功能说明：
 
 通过此接口可以暂停指定的任务
 
 >返回对象示例：
 
 ```
 {
     "code": 200,
     "data": null,
     "resultMsg": "执行成功",
     "errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/pause
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  taskId| int| 是 | 任务Id| 1 |
 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |

##停止任务接口
 
###功能说明：
 
 通过此接口可以停止  指定的任务
 
 >返回对象示例：
 
 ```
 {
     "code": 200,
     "data": null,
     "resultMsg": "执行成功",
     "errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/stop
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  taskId| int| 是 | 任务Id| 1 |
 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |
  
##删除任务
  
###功能说明：
  
通过调用此接口可以删除任务信息
>入参JSON示例

```
{
  "taskId": "1"
}
```
>返回对象示例：

```
{
    "code": 200,
    "data": null,
    "resultMsg": "删除成功",
    "errorStackTrace": null
}

```
  
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/delete
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  taskId| String| 是 | 删除任务| 1 |  
###响应：
 
 参数名 | 类型 | 描述 |
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |

##向任务中导入客户接口
 
###功能说明：
 
 通过此接口可以向指定的任务导入客户信息，用于拨打电话
 
 >入参JSON示例:
 
  ```
 
{
	"taskId":10000,
	"companyId":2000,
	"customerInfoList":[
		{
			"name":"测试0",
			"phone":"18311110000",
			"properties":{  //客户额外信息，如果话术中包含变量，则需要在properties中加上对应字段，map的key和话术中的变量保持一致。如果话术没有变量，则不要properties
				"real_name":"real"
			}
		},
		{
			"name":"测试1",
			"phone":"18311112222",
			"properties":{  //客户额外信息，如果话术中包含变量，则需要在properties中加上对应字段，map的key和话术中的变量保持一致。如果话术没有变量，则不要properties
				"real_name":"real"
			}
		}
	]
} 
  
  ```
  
 >返回对象示例：
 
 ```
 {
     "code": 200,
     "data": null,
     "resultMsg": "操作成功",
     "errorStackTrace": null
 }
 
 ```
 
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/importTaskCustomer

###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  companyId| int| 是 | 公司id| 1 |
  taskId| int| 是 | 任务Id| 1 |
  name| String| 是 | 客户名称| 张三 |
  phone| String| 是 | 客户电话| 13998987676 |
  properties| Map<String,String>| 否 | 客户额外信息| 请看json入参 |
  forceTransferCustomer|Integer|是否强制转移客户 1：是 0：否（默认1）| 1|
  
  tip:
  forceTransferCustomer字段使用方式（默认强制转移）
  有多个子账号（团队成员）情况下，客户【a】被子账号A跟进，此时通过api向子账号B创建的任务中导入客户【a】
  会因为跟进人不是子账号B导致失败，如果forceTransferCustomer设置为1，则会强制将客户【a】导入到子账号B
  创建的任务中，并且将客户【a】分配给子账号B

 
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |

##修改任务

###功能说明：

通过接口可以更改AI坐席数量，功能同crm端编辑话术时修改外呼号码的AI坐席数

>入参JSON示例

```
{
  //公司Id
  "companyId": 123,
  //任务Id
  "taskId":1669,
  //任务名称
  "taskName":"test",
  //任务类型 详见枚举
  "taskType":1,
  //外呼号码列表，当有多个外呼号码时可以用[,]分隔
  "userPhoneIds":"255,244",
  //外呼类型 详见枚举
  "callType":1,
  //并发数(ai坐席数)
  "concurrencyQuota":2,
  //多并发数(专业版及以上,最大100)
  "concurrencyPhone":4,
  //外呼开始日期
  "startDate":"2018-12-12",
  //任务开始时间
  "workingStartTime":"09:00",
  //任务结束实际
  "workingEndTime":"20:00",
  //午休开始时间
  "breakStartTime":"12:00",
  //午休结束时间
  "breakEndTime":"14:00"
}

```

>返回对象示例：

```
{
    "code": 200,
    "data": null,
    "resultMsg": "修改成功",
    "errorStackTrace": null
}

```

###请求：

URL：http://api.byrobot.cn/openapi/v1/task/update

###请求方法：

POST


###请求参数:

参数名 | 类型 | 是否必须 | 描述 | 示例 
--------- | ------- |------- | ------ |------
 companyId| int| 是 | 公司Id| 1 |
 taskId| int| 是 | 任务Id| 1 |
 taskName| String| 是 | 任务名称| 1 |
 taskType| int| 是 | 任务类型| 1 |
 userPhoneIds| String| 是 | 外呼号码| 1 |
 callType| int| 是 | 外呼类型| 1 |
 concurrencyQuota| int| 是 | 坐席数| 1 |
 concurrencyPhone| int| 否 | 并发量 | 1|
 startDate| String|否|开始日期|"2018-12-13"|
 workingStartTime|String|否|任务开始时间|"09:00"|
 workingEndTime|String|否|任务结束时间|"20:00"|
 breakStartTime|String|否|任务中断午休开始时间|"12:00"|
 breakEndTime|String|否|任务中断午休结束时间|"14:00"|


###响应：

参数名 | 类型 | 描述 
--------- | ------- |------
 code|int | 响应码 |
 resultMsg| String | 响应说明 |
 
##单次电话外呼
  
###功能说明：
  
通过调用此接口可以进行单次电话外呼
注意：此接口仅限测试和少量外呼，如需大量外呼请使用外呼任务

>入参JSON示例

```
{
  "customerId": 1
  "mobile": 13886871111
  "companyId": 1
  "variable": {
    "userName":"张三",
    "age":15
  }
  "sceneDefId": 255
  "sceneRecordId": 256
  "robotDefId": 230
}
```
>返回对象示例：

```
{
    "code": 200,
    "data": null,
    "resultMsg": "外呼成功",
    "errorStackTrace": null
}

```
  
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/call
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  customerId| int| 是 | 客户Id| 1 |  
  mobile| int| 是 | 客户手机号| 1 |  
  companyId| int| 是 | 公司Id| 1 |  
  variables| Map<String,String>| 否 | 1.变量（如果话术内设置变量则需要传入）2.不传值情况下需要保留字段名| 1 |      
  sceneDefId| int| 是 | 机器人话术场景Id| 1 |  
  sceneRecordId| int| 是 |机器人话术录音Id | 1 |  
  robotDefId| int| 是 | 机器人话术Id | 1 |  
 
###响应：
 
 参数名 | 类型 | 描述 
 --------- | ------- |------
  code|int | 响应码 |
  resultMsg| String | 响应说明 |

##根据手机号进行单次电话外呼
  
###功能说明：
  
通过调用此接口可以通过手机号直接进行单次电话外呼，外呼结果会通过回调返回，并且将通话记录增加到公司id对应的crm账号下

注意：此接口仅限测试和少量外呼，如需大量外呼请使用外呼任务
>入参JSON示例

```
{
  "mobile": "13886871111"
  "companyId": 1,
  "variable": {
    "userName":"张三",
    "age":15
  },
  userName:,"客户姓名",
  "sceneDefId": 255,
  "sceneRecordId": 256,
  "robotDefId": 230
}
```
>返回对象示例：

```
{
    "code": 200,
    "data": null,
    "resultMsg": "外呼成功",
    "errorStackTrace": null
}

```
  
###请求：
 
 URL：http://api.byrobot.cn/openapi/v1/task/singleCallByMobile
 
###请求方法：
 
 POST
 
 
###请求参数:
 
 参数名 | 类型 | 是否必须 | 描述 | 示例 
 --------- | ------- |------- | ------ |----------
  mobile| String| 是 | 客户手机号| 1 |  
  companyId| int| 是 | 公司Id| 1 |  
  variables| Map<String,String>| 否 |  1.变量（如果话术内设置变量则需要传入）2.不传值情况下需要保留字段名| 1 |      
  sceneDefId| int| 是 | 机器人话术场景Id| 1 |  
  sceneRecordId| int| 是 |机器人话术录音Id | 1 |  
  robotDefId| int| 是 | 机器人话术Id | 1 |  
  userName|String|否|客户姓名|1|
 
###响应：
 
 参数名 | 类型 | 描述 |
 --------- | ------- |------
  code|int | 响应码 |
  data|int | 通话记录Id|
  resultMsg| String | 响应说明 |
  
  
  
