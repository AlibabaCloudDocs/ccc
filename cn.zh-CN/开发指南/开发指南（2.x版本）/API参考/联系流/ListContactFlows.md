# ListContactFlows

调用ListContactFlows获取呼叫中心实例中的IVR流程列表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListContactFlows&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListContactFlows|系统规定参数。取值：ListContactFlows。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|10|分页大小，范围1-100。 |
|Type|String|否|MAIN\_FLOW|IVR流程类型：

 -   MAIN\_FLOW（主流程）
-   SUB\_FLOW（子流程）
-   SURVEY\_FLOW（满意度流程） |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of ContactFlow| |IVR列表。 |
|ContactFlowId|String|78128960-bb00-4ddc-8e82-923a8c5bd22d|联系流ID。 |
|CreatedTime|String|2021-03-05 17:35:45.0|创建时间。 |
|Definition|String|\{"activities":\[\{"type":"INCOMING\_CALL","id":"e98f0d47","name":"开始","properties":\{"position":\{"x":263,"y":164\}\},"events":\[\{"event":"complete","next":"2d3ad2c2","edgeId":"41f7dbd0"\}\],"nodeIndex":0\},\{"type":"HANGUP","id":"bd4f37e2","name":"挂机","properties":\{"position":\{"x":765,"y":185\}\},"events":\[\{"event":"complete","next":null\}\],"nodeIndex":999\},\{"type":"PLAY\_SAY","id":"2d3ad2c2","name":"放音","properties":\{"say":"您好，欢迎来到阿里云呼叫中心。","audioResourceId":"","position":\{"x":485.5,"y":153.5\},"audioType":"tts","audioInterrupt":false\},"events":\[\{"event":"complete","next":"bd4f37e2","edgeId":"e1af4f1f"\}\],"nodeIndex":1\}\],"description":""\}|IVR的内容，由云呼IVR Engine解析，用户不需要关心。 |
|Description|String|1.0|版本描述。 |
|DraftId|String|db07c0bb-6b1f-47d2-b37e-2451c617562d|草稿ID，当IVR流程处于未发布状态时返回此字段。 |
|Editor|String|ccc-test|此草稿的当前编辑人的用户名。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|Name|String|测试IVR|IVR名称。 |
|NumberList|List|\["400xxxx289"\]|IVR所绑定的号码列表。 |
|Published|Boolean|true|是否发布过。 |
|Type|String|MAIN\_FLOW|IVR流程类型：

 -   MAIN\_FLOW（主流程）
-   SUB\_FLOW（子流程）
-   SURVEY\_FLOW（满意度流程） |
|UpdatedTime|String|2021-03-08 15:34:49.0|上次修改的时间。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|1|IVR总数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListContactFlows
&InstanceId=ccc-test
&PageNumber=1
&PageSize=10
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>1</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <Type>MAIN_FLOW</Type>
        <Description>1.0</Description>
        <CreatedTime>2021-03-05 17:35:45.0</CreatedTime>
        <InstanceId>ccc-test</InstanceId>
        <ContactFlowId>78128960-bb00-4ddc-8e82-923a8c5bd22d</ContactFlowId>
        <Definition>{"activities":[{"type":"INCOMING_CALL","id":"e98f0d47","name":"开始","properties":{"position":{"x":263,"y":164}},"events":[{"event":"complete","next":"2d3ad2c2","edgeId":"41f7dbd0"}],"nodeIndex":0},{"type":"HANGUP","id":"bd4f37e2","name":"挂机","properties":{"position":{"x":765,"y":185}},"events":[{"event":"complete","next":null}],"nodeIndex":999},{"type":"PLAY_SAY","id":"2d3ad2c2","name":"放音","properties":{"say":"您好，欢迎来到阿里云呼叫中心。","audioResourceId":"","position":{"x":485.5,"y":153.5},"audioType":"tts","audioInterrupt":false},"events":[{"event":"complete","next":"bd4f37e2","edgeId":"e1af4f1f"}],"nodeIndex":1}],"description":""}</Definition>
        <Published>true</Published>
        <UpdatedTime>2021-03-08 15:34:49.0</UpdatedTime>
        <DraftId>db07c0bb-6b1f-47d2-b37e-2451c617562d</DraftId>
        <Editor>ccc-test</Editor>
        <Name>测试IVR</Name>
        <NumberList>["400xxxx289"]</NumberList>
    </List>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"TotalCount": "1",
		"PageSize": "10",
		"PageNumber": "1",
		"List": [{
			"Type": "MAIN_FLOW",
			"Description": "1.0",
			"CreatedTime": "2021-03-05 17:35:45.0",
			"InstanceId": "ccc-test",
			"ContactFlowId": "78128960-bb00-4ddc-8e82-923a8c5bd22d",
			"Definition": "{\"activities\":[{\"type\":\"INCOMING_CALL\",\"id\":\"e98f0d47\",\"name\":\"开始\",\"properties\":{\"position\":{\"x\":263,\"y\":164}},\"events\":[{\"event\":\"complete\",\"next\":\"2d3ad2c2\",\"edgeId\":\"41f7dbd0\"}],\"nodeIndex\":0},{\"type\":\"HANGUP\",\"id\":\"bd4f37e2\",\"name\":\"挂机\",\"properties\":{\"position\":{\"x\":765,\"y\":185}},\"events\":[{\"event\":\"complete\",\"next\":null}],\"nodeIndex\":999},{\"type\":\"PLAY_SAY\",\"id\":\"2d3ad2c2\",\"name\":\"放音\",\"properties\":{\"say\":\"您好，欢迎来到阿里云呼叫中心。\",\"audioResourceId\":\"\",\"position\":{\"x\":485.5,\"y\":153.5},\"audioType\":\"tts\",\"audioInterrupt\":false},\"events\":[{\"event\":\"complete\",\"next\":\"bd4f37e2\",\"edgeId\":\"e1af4f1f\"}],\"nodeIndex\":1}],\"description\":\"\"}",
			"Published": "true",
			"UpdatedTime": "2021-03-08 15:34:49.0",
			"DraftId": "db07c0bb-6b1f-47d2-b37e-2451c617562d",
			"Editor": "ccc-test",
			"Name": "测试IVR",
			"NumberList": "[\"400xxxx289\"]"
		}]
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

