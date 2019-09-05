# ResetUserStatus {#doc_api_CCC_ResetUserStatus .reference}

调用ResetUserStatus重置异常状态的坐席

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ResetUserStatus&type=RPC&version=2017-07-05)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ResetUserStatus|系统规定参数。取值：ResetUserStatus。

 |
|InstanceId|String|是|d278629c-c687-4aa3-b044-4fe9b012e7ef|云呼叫中心实例ID

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码

 |
|HttpStatusCode|Integer|200|响应状态码

 |
|Message|String|无|响应提示信息

 |
|RequestId|String|2D4F3E45-96CD-4210-B15B-F27BAC29FE29|请求ID,可用于接口的日志查询

 |
|Success|Boolean|true|是否调用成功

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http(s)://ccc.cn-hangzhou.aliyuncs.com/?Action=ResetUserStatus
&InstanceId=d278629c-c687-4aa3-b044-4fe9b012e7ef
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ResetUserStatus>
      <HttpStatusCode>200</HttpStatusCode>
      <RequestId>2D4F3E45-96CD-4210-B15B-F27BAC29FE29</RequestId>
      <Success>true</Success>
      <Code>OK</Code>
</ResetUserStatus>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"HttpStatusCode":200,
	"RequestId":"2D4F3E45-96CD-4210-B15B-F27BAC29FE29",
	"Success":true,
	"Code":"OK"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

