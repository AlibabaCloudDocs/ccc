# 根据话务ID查询录音

调用ListRecordingsByContactId根据话务ID查找相关的录音详细信息。

有以下两种获取话务ID（**ContactId**）方式：

1. 通过调用**ListCallDetailRecords**，返回参数中包含**ContactId**。

2. 通过监听软电话SDK中的回调事件（参数表如下），回调事件中会携带每通通话全局唯一的**ContactId**。

```

钩子：某些事件触发时的回调函数
onCallComing  //来电，参数表（connid<通话id>,caller<主叫号码>,calee<被叫号码>,contactId<录音id>,skillgroupId<技能组id>）
onCallDialing  //去电，参数表（connid,caller,calee,contactId）

```

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListRecordingsByContactId&type=RPC&version=2017-07-05)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListRecordingsByContactId|系统规定参数。取值：**ListRecordingsByContactId**。 |
|ContactId|String|是|2020927020|话务ID |
|InstanceId|String|是|9cfad875-6260-4a53-ab6e-b13e3fb31f7d|呼叫中心实例ID |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码 |
|HttpStatusCode|Integer|200|HTTP状态码 |
|Message|String|无|响应信息 |
|Recordings|Array of Recording| |录音列表 |
|Recording| | | |
|AgentId|String|293939422320312215|坐席ID。

 坐席ID等同于该座席的RAM子账户ID。 |
|AgentName|String|小芳|坐席名称 |
|CalledNumber|String|15588886666|被叫号码 |
|CallingNumber|String|80327683|主叫号码 |
|Channel|String|无|已废弃字段 |
|ContactId|String|2020927020|话务ID |
|ContactType|String|Outbound|话务类型 |
|Duration|Integer|10|通话时长 |
|FileDescription|String|20180711125511-小芳|录音文件描述 |
|FileName|String|153128491143400080327683.wav|录音文件名称 |
|FilePath|String|无|已废弃字段 |
|InstanceId|String|无|已废弃字段 |
|QualityCheckTaskId|String|1F0BF809-7B30-4918-9424-4DF23A8BB9B1|智能质检任务ID |
|QualityCheckTid|String|23A1F0BF-7B30-4918-9424-4DF8B809B9B1|智能质检文本ID |
|StartTime|Long|1531284911000|通话开始时间 |
|RequestId|String|0997CE25-94D3-41DE-8C7A-E6FCFD8C01E0|请求ID |
|Success|Boolean|true|是否成功 |

## 示例

请求示例

```
http(s)://ccc.cn-shanghai.aliyuncs.com/?Action=ListRecordingsByContactId
&ContactId=2020927020
&InstanceId=9cfad875-6260-4a53-ab6e-b13e3fb31f7d
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<ListRecordingsByContactIdResponse>
      <HttpStatusCode>200</HttpStatusCode>
      <Recordings>
            <Recording>
                  <FileDescription>20180711125511-小芳</FileDescription>
                  <AgentName>小芳</AgentName>
                  <CalledNumber>15588886666</CalledNumber>
                  <CallingNumber>80327683</CallingNumber>
                  <FileName>153128491143400080327683.wav</FileName>
                  <Duration>10</Duration>
                  <ContactId>2020927020</ContactId>
                  <StartTime>1531284911000</StartTime>
                  <AgentId>293939422320312215</AgentId>
                  <ContactType>Outbound</ContactType>
            </Recording>
      </Recordings>
      <RequestId>0997CE25-94D3-41DE-8C7A-E6FCFD8C01E0</RequestId>
      <Success>true</Success>
      <Code>OK</Code>
</ListRecordingsByContactIdResponse>
```

`JSON`格式

```
{
    "HttpStatusCode":200,
    "Recordings":{
        "Recording":[
            {
                "FileDescription":"20180711125511-小芳",
                "AgentName":"小芳",
                "CalledNumber":"15588886666",
                "CallingNumber":"80327683",
                "FileName":"153128491143400080327683.wav",
                "Duration":10,
                "ContactId":"2020927020",
                "StartTime":1531284911000,
                "AgentId":"293939422320312215",
                "ContactType":"Outbound"
            }
        ]
    },
    "RequestId":"0997CE25-94D3-41DE-8C7A-E6FCFD8C01E0",
    "Success":true,
    "Code":"OK"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

