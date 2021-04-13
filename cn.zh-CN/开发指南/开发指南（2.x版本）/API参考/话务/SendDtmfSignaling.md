# SendDtmfSignaling

调用接口SendDtmfSignaling发送DTMF按键信息。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=SendDtmfSignaling&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|SendDtmfSignaling|系统规定参数。取值：SendDtmfSignaling。 |
|ChannelId|String|是|ch:customer:01089898989-\>13188888888:1609234221870:job-65735740600893440|待取回通道ID。 |
|DeviceId|String|是|ACC-YUNBS-1.0.10-bse05179638553000176add4046f|座席端提供的唯一ID，用来表示一个座席工作台，一个座席可以有多个不同类型的座席台，比如浏览器，iOS, Android等， 但是在同一时间，只能有一个生效。 |
|Dtmf|String|是|5|DTMF按键信息。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |
|JobId|String|是|:job-65735740600893440|话务ID。 |
|UserId|String|是|user-test@ccc-test|用户ID，格式为username@domain。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|CallContext|Struct| |话务上下文环境。 |
|CallType|String|OUTBOUND|呼叫类型, 最初发起呼叫时的类型。 |
|ChannelContexts|Array of ChannelContext| |通话上下文。 |
|AssociatedData|Map|无|随路数据。 |
|CallType|String|OUTBOUND|呼叫类型, 最初发起呼叫时的类型。 |
|ChannelFlags|String|\[\]|通道标志，比如监听，辅助，静音等。 |
|ChannelId|String|ch:user:1318888888-\>80011474:1609234221870:job-65735740600893440"|通道ID。 |
|ChannelState|String|ANSWERED|状态。 |
|Destination|String|80011474|接收方。 |
|Index|Integer|1|记录这个Channel在通话过程中创建的顺序。 |
|JobId|String|job-65735740600893440|话务ID。 |
|Originator|String|01012345678|发起方。 |
|ReleaseInitiator|String|无|挂断方。 |
|ReleaseReason|String|无|挂断原因。 |
|SkillGroupId|String|skill-group@ccc-test|该通话相关技能组。呼入场景下，技能组由IVR中路由的排队队列指定，在呼出场景下，技能组是座席签入的第一个技能组。 |
|Timestamp|Long|1609234222367|状态数据上次变更时间戳。 |
|UserExtension|String|80011474|该Channel的座席的分机号，如果是客户通道，则userExtension为空。 |
|UserId|String|user-test@ccc-test|该Channel的用户ID，如果是客户通道，则userId为空。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|job-65735740600893440|话务ID。 |
|UserContext|Struct| |用户上下文环境。 |
|BreakCode|String|Warm-up|小休状态码。 |
|DeviceId|String|ACC-YUNBS-1.0.10-bse05179638553000176add4046f|设备标示。 |
|Extension|String|80011474|座席分机号，一共8位 如果一个用户账号有多种设备，则多个设备用一个分机号，且同一时间只有一个设备可用。 |
|Heartbeat|Long|1609234222375|上次操作时间。 |
|InstanceId|String|ccc-test|呼叫中心实例ID。 |
|JobId|String|job-65735740600893440|在呼叫状态时的通话ID。 |
|Mobile|String|13900000001|座席手机号码，场外座席情况下通过此号码联系座席。 |
|OutboundScenario|Boolean|false|仅外呼 |
|Reserved|Long|1609234221864|座席处于预定状态，说明马上有电话给TA. 该参数记录收到预定请求的时间。 |
|SignedSkillGroupIdList|List|\["skill-group@ccc-test"\]|签入的技能组ID列表。 |
|UserId|String|user-test@ccc-test|用户ID，格式为username@domain。 |
|UserState|String|TALKING|座席状态码。 |
|WorkMode|String|ON\_SITE|工作模式。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|Params|List|无|返回参数。 |
|RequestId|String|842399EC-7D32-4472-AD08-9504C3F141FF|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=SendDtmfSignaling
&ChannelId=ch:customer:01089898989->13188888888:1609234221870:job-65735740600893440
&DeviceId=ACC-YUNBS-1.0.10-bse05179638553000176add4046f
&Dtmf=5
&InstanceId=ccc-test
&JobId=:job-65735740600893440
&UserId=user-test@ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>842399EC-7D32-4472-AD08-9504C3F141FF</RequestId>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <UserContext>
        <UserState>TALKING</UserState>
        <InstanceId>ccc-test</InstanceId>
        <DeviceId>ACC-YUNBS-1.0.10-bse05179638553000176add4046f</DeviceId>
        <BreakCode>Warm-up</BreakCode>
        <OutboundScenario>false</OutboundScenario>
        <Mobile>13900000001</Mobile>
        <SignedSkillGroupIdList>["skill-group@ccc-test"]</SignedSkillGroupIdList>
        <Extension>80011474</Extension>
        <UserId>user-test@ccc-test</UserId>
        <Heartbeat>1609234222375</Heartbeat>
        <WorkMode>ON_SITE</WorkMode>
        <JobId>job-65735740600893440</JobId>
        <Reserved>1609234221864</Reserved>
    </UserContext>
    <CallContext>
        <InstanceId>ccc-test</InstanceId>
        <CallType>OUTBOUND</CallType>
        <JobId>job-65735740600893440</JobId>
        <ChannelContexts>
            <Destination>80011474</Destination>
            <ChannelState>ANSWERED</ChannelState>
            <CallType>OUTBOUND</CallType>
            <Index>1</Index>
            <SkillGroupId>skill-group@ccc-test</SkillGroupId>
            <ChannelId>ch:user:1318888888-&amp;gt;80011474:1609234221870:job-65735740600893440"</ChannelId>
            <Timestamp>1609234222367</Timestamp>
            <Originator>1012345678</Originator>
            <ChannelFlags>[]</ChannelFlags>
            <UserId>user-test@ccc-test</UserId>
            <UserExtension>80011474</UserExtension>
            <JobId>job-65735740600893440</JobId>
        </ChannelContexts>
    </CallContext>
</Data>
<Code>OK</Code>
```

`JSON`格式

```
{
    "RequestId": "842399EC-7D32-4472-AD08-9504C3F141FF",
    "HttpStatusCode": 200,
    "Data": {
        "UserContext": {
            "UserState": "TALKING",
            "InstanceId": "ccc-test",
            "DeviceId": "ACC-YUNBS-1.0.10-bse05179638553000176add4046f",
            "BreakCode": "Warm-up",
            "OutboundScenario": false,
            "Mobile": 13900000001,
            "SignedSkillGroupIdList": "[\"skill-group@ccc-test\"]",
            "Extension": 80011474,
            "UserId": "user-test@ccc-test",
            "Heartbeat": 1609234222375,
            "WorkMode": "ON_SITE",
            "JobId": "job-65735740600893440",
            "Reserved": 1609234221864
        },
        "CallContext": {
            "InstanceId": "ccc-test",
            "CallType": "OUTBOUND",
            "JobId": "job-65735740600893440",
            "ChannelContexts": {
                "Destination": 80011474,
                "ChannelState": "ANSWERED",
                "CallType": "OUTBOUND",
                "Index": 1,
                "SkillGroupId": "skill-group@ccc-test",
                "ChannelId": "ch:user:1318888888-&amp;gt;80011474:1609234221870:job-65735740600893440\"",
                "Timestamp": 1609234222367,
                "Originator": 1012345678,
                "ChannelFlags": "[]",
                "UserId": "user-test@ccc-test",
                "UserExtension": 80011474,
                "JobId": "job-65735740600893440"
            }
        }
    },
    "Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.ChannelId|The specified channel %s does not exist in call %s.|通话中不存在指定的Channel信息。|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|
|404|NotExists.JobId|The call %s does not exist.|指定的通话信息不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

