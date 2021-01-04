# 保存WebRTC统计信息

调用SaveWebRTCStats保存客服端WebRTC语音传输统计信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=SaveWebRTCStats&type=RPC&version=2017-07-05)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SaveWebRTCStats|系统规定参数。取值：**SaveWebRTCStats**。 |
|CalleeNumber|String|是|131228450|被叫号码 |
|CallerNumber|String|是|021607806|主叫号码 |
|CallId|String|是|294834804|通话ID |
|CallStartTime|Long|是|1607655438368|通话开始时间 |
|InstanceId|String|是|9f46dde1-207a-46dd-926e-c0f39a124|待获取用户的呼叫中心实例ID |
|RecordTime|Long|是|160765543836|调用此API的时间（客户端电脑的时间） |
|Stats|String|是|\[XXX\]|从rtcPeerConnection.getStats\(selector\)中获取的语音传输统计信息（每隔3秒获取一次） |
|TenantId|String|是|acc2626|租户ID |
|Uid|String|是|247361754012232|客服的RAM ID |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码 |
|HttpStatusCode|Integer|200|HTTP状态码 |
|Message|String|无|响应信息 |
|RequestId|String|CF1C21B9-2D49-4B54-880F-FBE248C16903|请求ID |
|RowCount|Long|1|存入数据库后返回的行数，一般为1 |
|Success|Boolean|true|是否成功 |

## 示例

请求示例

```
http(s)://ccc.cn-shanghai.aliyuncs.com/?Action=StartBack2BackCall
&CalleeNumber=131228450
&CallerNumber=021607806
&CallId=294834804
&CallStartTime=1607655438368
&RecordTime=160765543836
&Stats=[XXX]
&TenantId=acc2626
&Uid=247361754012232
&InstanceId=9cfad875-6260-4a53-ab6e-b13e3fb31f7d
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<SaveWebRTCStatsResponse>
      <code>OK</code>
      <httpStatusCode>200</httpStatusCode>
      <requestId>CF1C21B9-2D49-4B54-880F-FBE248C16903</requestId>
      <rowCount>1</rowCount>
      <success>true</success>
</SaveWebRTCStatsResponse>
```

`JSON` 格式

```
{
    "code":"OK",
    "httpStatusCode":200,
    "requestId":"CF1C21B9-2D49-4B54-880F-FBE248C16903",
    "rowCount":1,
    "success":true
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

