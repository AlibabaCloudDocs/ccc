# PickOutboundNumbers

调用接口PickOutboundNumbers获取外呼号码。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=PickOutboundNumbers&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|PickOutboundNumbers|系统规定参数。取值：PickOutboundNumbers。 |
|CalledNumber|String|是|13888888888|被叫号码。 |
|Count|Integer|是|1|希望返回的可选号码数量， 默认1。 |
|InstanceId|String|是|ccc-test|呼叫实例ID |
|SkillGroupIdList|String|是|\["test@ccc-test"\]|技能组ID集合， 格式 ： \[技能组ID\] |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Array of NumberPair| |数据。 |
|Callee|Struct| |被叫号码。 |
|City|String|北京|城市 |
|Number|String|13888888888|号码 |
|Province|String|北京|省份 |
|Caller|Struct| |主叫号码。 |
|City|String|北京|城市 |
|Number|String|01089898989|号码 |
|Province|String|北京|省份 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=PickOutboundNumbers
&CalledNumber=13888888888
&Count=1
&InstanceId=ccc-test
&SkillGroupIdList=["test@ccc-test"]
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <Callee>
        <Number>13888888888</Number>
        <City>北京</City>
        <Province>北京</Province>
    </Callee>
    <Caller>
        <Number>1089898989</Number>
        <City>北京</City>
        <Province>北京</Province>
    </Caller>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
    "RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
    "HttpStatusCode": 200,
    "Data": {
        "Callee": {
            "Number": 13888888888,
            "City": "北京",
            "Province": "北京"
        },
        "Caller": {
            "Number": 1089898989,
            "City": "北京",
            "Province": "北京"
        }
    },
    "Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

