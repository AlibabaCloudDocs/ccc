# TakeBreak

调用接口TakeBreak将坐席设置为小休状态。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=TakeBreak&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|TakeBreak|系统规定参数。取值：TakeBreak。 |
|Code|String|是|default|小休代码。 |
|DeviceId|String|是|ACC-YUNBS-1.0.10-bs3b5f22c6d78f000176aebe9471|座席端提供的唯一ID，用来表示一个座席工作台，一个座席可以有多个不同类型的座席台，比如浏览器，iOS, Android等， 但是在同一时间，只能有一个生效。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|UserId|String|是|user-test@ccc-test|用户ID，格式为username@domain。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|BreakCode|String|default|小休状态码。 |
|DeviceId|String|ACC-YUNBS-1.0.10-bs3b5f22c6d78f000176aebe9471|设备标示。 |
|Extension|String|80011474|座席分机号，一共8位 如果一个用户账号有多种设备，则多个设备用一个分机号，且同一时间只有一个设备可用。 |
|Heartbeat|Long|1609249563836|上次操作时间。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|无|在呼叫状态时的通话ID。 |
|Mobile|String|13900000001|座席手机号码，场外座席情况下通过此号码联系座席。 |
|OutboundScenario|Boolean|false|仅外呼。 |
|Reserved|Long|1609234221864|座席处于预定状态，说明马上有电话给TA. 该参数记录收到预定请求的时间。 |
|SignedSkillGroupIdList|List|\["skill-group@ccc-test"\]|签入的技能组ID列表。 |
|UserId|String|user-test@ccc-test|用户ID，格式为username@domain。 |
|UserState|String|BREAK|座席状态码。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|返回参数。 |
|RequestId|String|B59382D2-5755-4C6D-861F-FA2AAD8F89F7|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=TakeBreak
&Code=default
&DeviceId=ACC-YUNBS-1.0.10-bs3b5f22c6d78f000176aebe9471
&InstanceId=ccc-test
&UserId=user-test@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>B59382D2-5755-4C6D-861F-FA2AAD8F89F7</RequestId>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <UserState>BREAK</UserState>
    <InstanceId>ccc-test</InstanceId>
    <DeviceId>ACC-YUNBS-1.0.10-bs3b5f22c6d78f000176aebe9471</DeviceId>
    <BreakCode>default</BreakCode>
    <OutboundScenario>false</OutboundScenario>
    <Mobile>13900000001</Mobile>
    <SignedSkillGroupIdList>["skill-group@ccc-test"]</SignedSkillGroupIdList>
    <Extension>80011474</Extension>
    <UserId>user-test@ccc-test</UserId>
    <Heartbeat>1609249563836</Heartbeat>
    <WorkMode>ON_SITE</WorkMode>
    <Reserved>1609234221864</Reserved>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
    "RequestId": "B59382D2-5755-4C6D-861F-FA2AAD8F89F7",
    "HttpStatusCode": 200,
    "Data": {
        "UserState": "BREAK",
        "InstanceId": "ccc-test",
        "DeviceId": "ACC-YUNBS-1.0.10-bs3b5f22c6d78f000176aebe9471",
        "BreakCode": "default",
        "OutboundScenario": false,
        "Mobile": 13900000001,
        "SignedSkillGroupIdList": "[\"skill-group@ccc-test\"]",
        "Extension": 80011474,
        "UserId": "user-test@ccc-test",
        "Heartbeat": 1609249563836,
        "WorkMode": "ON_SITE",
        "Reserved": 1609234221864
    },
    "Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|404|NotExists.UserId|The user %s does not exist in instance %s.|呼叫中心实例中不存在指定的用户。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

