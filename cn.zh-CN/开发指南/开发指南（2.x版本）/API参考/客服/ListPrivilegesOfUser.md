# ListPrivilegesOfUser

调用ListPrivilegesOfUser获取坐席权限。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListPrivilegesOfUser&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListPrivilegesOfUser|系统规定参数。取值：ListPrivilegesOfUser。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Array of Data| |数据。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|Name|String|Workbench:Call|权限名称。 |
|Scope|String|SELF\_ONLY|权限范围。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListPrivilegesOfUser
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <Scope>SELF_ONLY</Scope>
    <InstanceId>ccc-test</InstanceId>
    <Name>Workbench:Call</Name>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
    "RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
    "HttpStatusCode": 200,
    "Data": {
        "Scope": "SELF_ONLY",
        "InstanceId": "ccc-test",
        "Name": "Workbench:Call"
    },
    "Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

