# GetInstance

调用GetInstance获取云呼实例详细信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=GetInstance&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetInstance|系统规定参数。取值：GetInstance。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|AdminList|Array of User| |管理员列表。 |
|DisplayName|String|云呼测试1|管理员的姓名。 |
|Email|String|18866668888@163.com|电子邮件地址。 |
|Extension|String|80326034|分机号码。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|LoginName|String|user-test|用户登陆名。 |
|Mobile|String|138xxxx2114|用户电话号码。 |
|RoleId|String|Admin@ccc-test|用户的角色ID。 |
|RoleName|String|Admin|角色名称。

 -   管理员（Admin）
-   技能组组长（Manager）
-   坐席（Agent） |
|UserId|String|user-test@ccc-test|用户ID。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|AliyunUid|String|1571234567890123|呼叫中心系统规格所对应的阿里云账户ID。 |
|ConsoleUrl|String|https://ccc-v2.aliyun.com/\#/workbench/ccc-test|呼叫中心控制台URL，由阿里云呼叫中心官方URL加呼叫中心实例的域名组成。 |
|Description|String|测试实例|呼叫中心实例简单描述。 |
|DomainName|String|ccc-test|呼叫中心实例的二级域名，全局唯一。 |
|Id|String|ccc-test|呼叫中心实例ID。 |
|Name|String|云呼测试实例|呼叫中心实例名称。 |
|NumberList|Array of PhoneNumber| |呼叫中心号码列表。 |
|Active|Boolean|true|是否可用。 |
|City|String|乐山|号码归属地市。 |
|ContactFlowId|String|a3fb6c62-9b49-4942-ae5b-cf2abd4123ek|该电话号码所关联的联系流IVR ID。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|Number|String|083xxxx0011|号码。 |
|Province|String|四川|号码归属地省。 |
|SkillGroups|Array of SkillGroup| |号码所关联的技能组列表。 |
|Description|String|测试|技能组描述。 |
|DisplayName|String|测试技能组|技能组展示名。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|Name|String|test|技能组名称。 |
|PhoneNumberCount|Integer|1|该技能组关联的号码数量。 |
|SkillGroupId|String|test@ccc-test|技能组ID。 |
|UserCount|Integer|2|技能组所关联的客服数量。 |
|Usage|String|Bidirection|号码用途。 |
|UserId|String|user-test@ccc-test|坐席ID，如果此参数不为空，说明该号码是座席专属号码。 |
|Status|String|RUNNING|实例状态。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|响应参数。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetInstance
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Params>无</Params>
<Data>
    <Status>RUNNING</Status>
    <Description>测试实例</Description>
    <DomainName>ccc-test</DomainName>
    <ConsoleUrl>https://ccc-v2.aliyun.com/#/workbench/ccc-test</ConsoleUrl>
    <AliyunUid>1571234567890123</AliyunUid>
    <Id>ccc-test</Id>
    <Name>云呼测试实例</Name>
    <AdminList>
        <Extension>80326034</Extension>
        <LoginName>user-test</LoginName>
        <RoleName>Admin</RoleName>
        <Email>18866668888@163.com</Email>
        <InstanceId>ccc-test</InstanceId>
        <UserId>user-test@ccc-test</UserId>
        <DisplayName>云呼测试1</DisplayName>
        <RoleId>Admin@ccc-test</RoleId>
        <Mobile>138xxxx2114</Mobile>
        <WorkMode>ON_SITE</WorkMode>
    </AdminList>
    <NumberList>
        <Usage>Bidirection</Usage>
        <Active>true</Active>
        <Number>083xxxx0011</Number>
        <InstanceId>ccc-test</InstanceId>
        <ContactFlowId>a3fb6c62-9b49-4942-ae5b-cf2abd4123ek</ContactFlowId>
        <UserId>user-test@ccc-test</UserId>
        <City>乐山</City>
        <Province>四川</Province>
        <SkillGroups>
            <Description>测试</Description>
            <PhoneNumberCount>1</PhoneNumberCount>
            <InstanceId>ccc-test</InstanceId>
            <UserCount>2</UserCount>
            <DisplayName>测试技能组</DisplayName>
            <SkillGroupId>test@ccc-test</SkillGroupId>
            <Name>test</Name>
        </SkillGroups>
    </NumberList>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
	"RequestId": "EEEE671A-3E24-4A04-81E6-6C4F5B39DF75",
	"Message": "无",
	"HttpStatusCode": "200",
	"Params": "无",
	"Data": {
		"Status": "RUNNING",
		"Description": "测试实例",
		"DomainName": "ccc-test",
		"ConsoleUrl": "https://ccc-v2.aliyun.com/#/workbench/ccc-test",
		"AliyunUid": "1571234567890123",
		"Id": "ccc-test",
		"Name": "云呼测试实例",
		"AdminList": [{
			"Extension": "80326034",
			"LoginName": "user-test",
			"RoleName": "Admin",
			"Email": "18866668888@163.com",
			"InstanceId": "ccc-test",
			"UserId": "user-test@ccc-test",
			"DisplayName": "云呼测试1",
			"RoleId": "Admin@ccc-test",
			"Mobile": "138xxxx2114",
			"WorkMode": "ON_SITE"
		}],
		"NumberList": [{
			"Usage": "Bidirection",
			"Active": "true",
			"Number": "083xxxx0011",
			"InstanceId": "ccc-test",
			"ContactFlowId": "a3fb6c62-9b49-4942-ae5b-cf2abd4123ek",
			"UserId": "user-test@ccc-test",
			"City": "乐山",
			"Province": "四川",
			"SkillGroups": [{
				"Description": "测试",
				"PhoneNumberCount": "1",
				"InstanceId": "ccc-test",
				"UserCount": "2",
				"DisplayName": "测试技能组",
				"SkillGroupId": "test@ccc-test",
				"Name": "test"
			}]
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

