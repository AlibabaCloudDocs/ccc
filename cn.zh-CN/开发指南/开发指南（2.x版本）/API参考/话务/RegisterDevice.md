# RegisterDevice

调用RegisterDevice注册设备，此接口只适用于SIP话机设备，通过此接口来设置设备密码。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=RegisterDevice&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|DeviceId|String|是|Yealink SIP-T23G 44.84.203.6|设备ID,格式：厂商名称+话机型号+固件版本; |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|Password|String|是|80xxxx33|设备密码。 |
|UserId|String|是|user-test@ccc-test|呼叫中心实例的用户ID，实例内唯一。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=RegisterDevice
&DeviceId=Yealink SIP-T23G 44.84.203.6
&InstanceId=ccc-test
&Password=80xxxx33
&UserId=user-test@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Code>OK</Code>
```

`JSON`格式

```
{"RequestId":"EEEE671A-3E24-4A04-81E6-6C4F5B39DF75","Message":"无","HttpStatusCode":"200","Params":"无","Code":"OK"}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

