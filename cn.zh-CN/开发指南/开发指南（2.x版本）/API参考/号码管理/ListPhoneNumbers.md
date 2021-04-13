# ListPhoneNumbers

调用ListPhoneNumbers获取呼叫中心实例的电话号码。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListPhoneNumbers&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListPhoneNumbers|系统规定参数。取值：ListPhoneNumbers。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|PageNumber|Integer|是|1|分页序号，范围1-100。 |
|PageSize|Integer|是|20|分页大小，范围1-100。 |
|SearchPattern|String|否|010|号码查找pattern，可以基于此参数模糊查找。 |
|Usage|String|否|Bidirection|号码用途，如果此参数为空，则获取所有类型的号码。取值：

 -   呼入（Inbound）
-   呼出（Outbound）
-   同时用于呼入和呼出（Bidirection） |
|Active|Boolean|否|true|号码是否可用。如果为空，则获取所有类型的号码。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|List|Array of PhoneNumber| |号码列表。 |
|Active|Boolean|true|号码是否可用。 |
|City|String|乐山|号码归属地市。 |
|ContactFlowId|String|a3fb6c62-9b49-4942-ae5b-cf2abd4123ek|该电话号码所关联的联系流IVR ID。 |
|ContactFlowName|String|测试IVR|该电话号码所关联的联系流IVR名称。 |
|CreateTime|String|1617958538000|创建时间。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|Number|String|083xxxx0011|号码。 |
|Provider|String|ali|号码供应商。 |
|Province|String|四川|号码归属地省。 |
|SkillGroups|Array of SkillGroup| |号码所关联的技能组列表。 |
|DisplayName|String|测试技能组|技能组展示名。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|Name|String|test|技能组名称。 |
|SkillGroupId|String|test@ccc-test|技能组ID。 |
|Tags|String|M1|号码业务标签。 |
|Usage|String|Bidirection|号码用途。 |
|UserId|String|user-test@ccc-test|坐席ID，如果此参数不为空，说明该号码是座席专属号码。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|20|分页大小。 |
|TotalCount|Integer|1|总条目数。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|PageNumber|Integer|1|分页序号。 |
|PageSize|Integer|20|分页大小。 |
|RequestId|String|BA03159C-E808-4FF1-B27E-A61B6E888D7F|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=ListPhoneNumbers
&Active=true
&InstanceId=ccc-test
&PageNumber=1
&PageSize=20
&SearchPattern=010
&Usage=Bidirection
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>BA03159C-E808-4FF1-B27E-A61B6E888D7F</RequestId>
<PageSize>20</PageSize>
<Message>无</Message>
<PageNumber>1</PageNumber>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <TotalCount>1</TotalCount>
    <PageSize>20</PageSize>
    <PageNumber>1</PageNumber>
    <List>
        <Usage>Bidirection</Usage>
        <Active>true</Active>
        <Number>083xxxx0011</Number>
        <InstanceId>ccc-test</InstanceId>
        <ContactFlowId>a3fb6c62-9b49-4942-ae5b-cf2abd4123ek</ContactFlowId>
        <UserId>user-test@ccc-test</UserId>
        <CreateTime>1617958538000</CreateTime>
        <ContactFlowName>测试IVR</ContactFlowName>
        <City>乐山</City>
        <Tags>M1</Tags>
        <Province>四川</Province>
        <Provider>ali</Provider>
        <SkillGroups>
            <InstanceId>ccc-test</InstanceId>
            <DisplayName>测试技能组</DisplayName>
            <SkillGroupId>test@ccc-test</SkillGroupId>
            <Name>test</Name>
        </SkillGroups>
    </List>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
    "RequestId": "BA03159C-E808-4FF1-B27E-A61B6E888D7F",
    "PageSize": 20,
    "Message": "无",
    "PageNumber": 1,
    "HttpStatusCode": 200,
    "Data": {
        "TotalCount": 1,
        "PageSize": 20,
        "PageNumber": 1,
        "List": {
            "Usage": "Bidirection",
            "Active": true,
            "Number": "083xxxx0011",
            "InstanceId": "ccc-test",
            "ContactFlowId": "a3fb6c62-9b49-4942-ae5b-cf2abd4123ek",
            "UserId": "user-test@ccc-test",
            "CreateTime": 1617958538000,
            "ContactFlowName": "测试IVR",
            "City": "乐山",
            "Tags": "M1",
            "Province": "四川",
            "Provider": "ali",
            "SkillGroups": {
                "InstanceId": "ccc-test",
                "DisplayName": "测试技能组",
                "SkillGroupId": "test@ccc-test",
                "Name": "test"
            }
        }
    },
    "Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|400|Parameter.Enumeration|The parameter %s must be one of the value of enumeration %s.|该参数必须为系统限定的枚举值之一。|
|400|Parameter.Maximum|The parameter %s must be less than or equal to %s.|参数必须小于或等于系统规定的最大值。|
|400|Parameter.Minimum|The parameter %s must be greater than or equal to %s.|参数必须大于或等于系统规定的最小值。|
|400|Parameter.Empty|The parameter %s may not be null or empty.|该参数不能为null值或为空字符串。|
|400|Parameter.Null|The parameter %s may not be null.|该参数不能为null值.|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

