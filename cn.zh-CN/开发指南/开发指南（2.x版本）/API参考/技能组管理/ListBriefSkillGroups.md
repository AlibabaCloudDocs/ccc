# ListBriefSkillGroups

调用接口ListBriefSkillGroups获取实例下技能组列表，坐席工作台转接时使用。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListBriefSkillGroups&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListBriefSkillGroups|系统规定参数。取值：ListBriefSkillGroups。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|10|分页大小，范围1-100。 |
|SearchPattern|String|是|user-test|基于名称过滤。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of SkillGroup| |技能组列表。 |
|Description|String|测试技能组|技能组描述。 |
|DisplayName|String|测试技能组|技能组展示名。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|PhoneNumberCount|Integer|1|技能组关联号码数量。 |
|SkillGroupId|String|test@ccc-test|技能组ID。 |
|SkillGroupName|String|测试技能组|技能组名称。 |
|UserCount|Integer|1|技能组坐席人数。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|10|分页大小。 |
|TotalCount|Integer|1|总数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|3969FC68-CEC2-4398-B76A-60D2F7EDEBAF|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListBriefSkillGroups
&InstanceId=ccc-test
&PageNumber=1
&PageSize=10
&SearchPattern=user-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>3969FC68-CEC2-4398-B76A-60D2F7EDEBAF</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>1</TotalCount>
    <PageSize>10</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <SkillGroupName>测试技能组</SkillGroupName>
        <Description>测试技能组</Description>
        <PhoneNumberCount>1</PhoneNumberCount>
        <InstanceId>ccc-test</InstanceId>
        <UserCount>1</UserCount>
        <DisplayName>测试技能组</DisplayName>
        <SkillGroupId>test@ccc-test</SkillGroupId>
    </List>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
    "RequestId": "3969FC68-CEC2-4398-B76A-60D2F7EDEBAF",
    "Message": "无",
    "HttpStatusCode": 200,
    "Data": {
        "TotalCount": 1,
        "PageSize": 10,
        "PageNumber": 1,
        "List": {
            "SkillGroupName": "测试技能组",
            "Description": "测试技能组",
            "PhoneNumberCount": 1,
            "InstanceId": "ccc-test",
            "UserCount": 1,
            "DisplayName": "测试技能组",
            "SkillGroupId": "test@ccc-test"
        }
    },
    "Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|
|400|Parameter.Blank|The parameter %s may not be null or blank.|该参数不能为null或含有空白符的字符串。|
|400|Parameter.Null|The parameter %s may not be null.|该参数不能为null值.|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

