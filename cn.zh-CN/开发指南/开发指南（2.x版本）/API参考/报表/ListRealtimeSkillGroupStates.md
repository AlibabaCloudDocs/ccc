# ListRealtimeSkillGroupStates

调用ListRealtimeSkillGroupStates获取技能组实时数据报表。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListRealtimeSkillGroupStates&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListRealtimeSkillGroupStates|系统规定参数。取值：ListRealtimeSkillGroupStates。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|10|分页大小，范围1-100。 |
|SkillGroupIdList|String|否|\["skg-test1@ccc-test", "skg-test2@ccc-test2"\]|待查询数据的技能组ID列表。如果不传，查询当前分页下的所有技能组。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of SkillGroupState| |技能组状态列表。 |
|BreakingAgents|Long|0|小休坐席数。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|LoggedInAgents|Long|2|在线坐席数。 |
|LongestWaitingTime|Long|0|最大等待时长。 |
|ReadyAgents|Long|2|空闲坐席数。 |
|SkillGroupId|String|skg-test1@ccc-test|技能组ID。 |
|SkillGroupName|String|test1|技能组名称。 |
|TalkingAgents|Long|0|正在通话坐席数。 |
|WaitingCalls|Long|0|当前排队电话个数。 |
|WorkingAgents|Long|0|话后处理坐席数。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|2|总条目数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|26A34338-5CD9-4C95-A7A6-5BDCE76C6B94|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListRealtimeSkillGroupStates
&InstanceId=ccc-test
&PageNumber=1
&PageSize=10
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>26A34338-5CD9-4C95-A7A6-5BDCE76C6B94</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>2</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <BreakingAgents>0</BreakingAgents>
        <TalkingAgents>0</TalkingAgents>
        <SkillGroupName>test1</SkillGroupName>
        <InstanceId>ccc-test</InstanceId>
        <LoggedInAgents>2</LoggedInAgents>
        <ReadyAgents>2</ReadyAgents>
        <WaitingCalls>0</WaitingCalls>
        <SkillGroupId>skg-test1@ccc-test</SkillGroupId>
        <LongestCall>0</LongestCall>
        <WorkingAgents>0</WorkingAgents>
    </List>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "26A34338-5CD9-4C95-A7A6-5BDCE76C6B94",
	"Message": "无",
	"HttpStatusCode": "200",
	"Data": {
		"TotalCount": "2",
		"PageSize": "10",
		"PageNumber": "1",
		"List": [{
			"BreakingAgents": "0",
			"TalkingAgents": "0",
			"SkillGroupName": "test1",
			"InstanceId": "ccc-test",
			"LoggedInAgents": "2",
			"ReadyAgents": "2",
			"WaitingCalls": "0",
			"SkillGroupId": "skg-test1@ccc-test",
			"LongestCall": "0",
			"WorkingAgents": "0"
		}]
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

