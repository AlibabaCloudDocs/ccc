# GetRoutePoint {#doc_api_CCC_GetRoutePoint .reference}

调用GetRoutePoint获取联系流的路由点

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=GetRoutePoint&type=RPC&version=2017-07-05)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetRoutePoint|系统规定参数。取值：GetRoutePoint。

 |
|ContactFlowId|String|是|dDMD\_0mif4hv|联系流ID

 |
|InstanceId|String|是|9cfad875-6260-4a53-ab6e-b13e3fb31f7d|云呼叫中心实例ID

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码

 |
|HttpStatusCode|Integer|200|响应状态码

 |
|Message|String|无|响应信息

 |
|RequestId|String|F81866AD-A125-4D9A-A942-1CD6FBA9E9F5|请求ID,用于日志查询

 |
|RoutePoint|String|80206198|路由点

 |
|StatusCode|String|无|状态码

 |
|StatusDesc|String|无|状态描述信息

 |
|Success|Boolean|true|是否成功

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

http://ccc.cn-shanghai.aliyuncs.com?Action=GetRoutePoint
&InstanceId=9cfad875-6260-4a53-ab6e-b13e3fb31f7d
&ContactFlowId=dDMD_0mif4hv
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<GetRoutePointResponse>
	    <HttpStatusCode>200</HttpStatusCode>
	    <RequestId>F81866AD-A125-4D9A-A942-1CD6FBA9E9F5</RequestId>
	    <RoutePoint>80206198</RoutePoint>
	    <Success>true</Success>
	    <Code>OK</Code>
</GetRoutePointResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"HttpStatusCode":200,
	"RequestId":"F81866AD-A125-4D9A-A942-1CD6FBA9E9F5",
	"RoutePoint":"80206198",
	"Success":true,
	"Code":"OK"
}
```

## 错误码 { .section}

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

