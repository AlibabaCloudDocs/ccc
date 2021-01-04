# 根据通话ID获取通话操作日志

调用ListCallEventDetailByContactId根据通话ID获取通话的详细操作日志。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListCallEventDetailByContactId&type=RPC&version=2017-07-05)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListCallEventDetailByContactId|系统规定参数。取值：**ListCallEventDetailByContactId**。 |
|ContactId|String|是|1096645650|通过指定的**contactId**来查询某一通电话的记录，contactId可以通过软电话SDK发生通话时获取到。 |
|InstanceId|String|是|9cfad875-6260-4a53-ab6e-b13e3fb31f7d|呼叫中心实例ID |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码 |
|Data|Struct| |获取到的通话详单 |
|CallType|String|Outbound|呼叫类型 |
|Callee|String|13501215646|被叫号码 |
|Caller|String|80315543|主叫号码 |
|Events|Array of CallEventDetail| |对象列表 |
|CallEventDetail| | | |
|AgentName|String|cloudcallcenter|坐席名 |
|CallMode|String|Outbound|通话类型 |
|DetailData|Struct| |动态添加所需的详细信息 |
|EventType|String|agent|事件类型 包括：ivr、queue、agent。 |
|HangUper|String|byeSystem|被求助者，求助内部坐席，对应坐席名称；求助外部的话，记录外部号码。 |
|Helper|String|xme|挂机者 |
|SatisfactionalResearch|String|不满意|满意度调查 |
|SkillGroup|String|测试|技能组 |
|Duration|Integer|9|持续时间 |
|Event|String|Dial|事件描述。

 包括：

 -   **IVR事件**：EnterIVR （进入IVR）；
-   **队列事件**：EnterQueue（进入队列）、ACDOverflow（队列溢出）、AbandonedRing（振铃放弃）、NormalEnd（队列中正常结束）、AbandonedInQueue（进入放弃队列）、WaitingInQueue（进入等待队列）；
-   **坐席事件**：Ring（振铃）、Talk（通话）、GiveUp（放弃）、End（结束）、Handle（挂断）、CallForHelp（发起求助）、CallForHelpSuccess（求助成功）、SetUpMeeting（会议建立）、Dial（拨号）、LaunchTransfer（转接）。 |
|Status|String|Dialing|状态 |
|TimeStamp|String|1555492246000|事件发生时间 |
|PrivacyNumber|String|12345677|虚拟号码 |
|ReleaseAgent|String|agent|挂断方,customer：用户挂机；agent：坐席挂机，同时提醒，目前有部分数据为兼容，如出现特殊数据请反馈给云呼技术值班同学进行挂断方的定位。 |
|ReleaseReason|String|487-Request Terminated|挂断原因 |
|StartTime|String|1555492246000|呼叫时间 |
|HttpStatusCode|Integer|200|HTTP状态码 |
|Message|String|无|响应信息 |
|RequestId|String|7BEEA660-A45A-45E3-98CC-AFC65E715C23|请求ID |
|Success|Boolean|true|是否成功 |

## 示例

请求示例

```
http(s)://ccc.cn-shanghai.aliyuncs.com/?Action=ListCallEventDetailByContactId
&ContactId=1096645650
&InstanceId=9cfad875-6260-4a53-ab6e-b13e3fb31f7d
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListCallEventDetailByContactIdResponse>
      <Data>
            <Caller>80315543</Caller>
            <Callee>13501215646</Callee>
            <CallType>Outbound</CallType>
            <ReleaseAgent>agent</ReleaseAgent>
            <ReleaseReason>487-Request Terminated</ReleaseReason>
            <Events>
                  <CallEventDetail>
                        <TimeStamp>1555492246000</TimeStamp>
                        <Status>Dialing</Status>
                        <AgentName>cloudcallcenter</AgentName>
                        <Event>Dial</Event>
                        <Duration>9</Duration>
                        <DetailData>
                              <EventType>agent</EventType>
                        </DetailData>
                        <CallMode>Outbound</CallMode>
                  </CallEventDetail>
                  <CallEventDetail>
                        <TimeStamp>1555492259000</TimeStamp>
                        <Status>Handling</Status>
                        <AgentName>cloudcallcenter</AgentName>
                        <Event>End</Event>
                        <Duration>16</Duration>
                        <DetailData>
                              <HangUper>byeSystem</HangUper>
                              <EventType>agent</EventType>
                        </DetailData>
                        <CallMode>Outbound</CallMode>
                  </CallEventDetail>
                  <CallEventDetail>
                        <TimeStamp>1555492259000</TimeStamp>
                        <AgentName>cloudcallcenter</AgentName>
                        <Event>Handle</Event>
                        <Duration>0</Duration>
                        <DetailData>
                              <EventType>agent</EventType>
                        </DetailData>
                        <CallMode>Outbound</CallMode>
                  </CallEventDetail>
            </Events>
            <StartTime>1555492246000</StartTime>
      </Data>
      <HttpStatusCode>200</HttpStatusCode>
      <RequestId>7BEEA660-A45A-45E3-98CC-AFC65E715C23</RequestId>
      <Success>true</Success>
      <Code>OK</Code>
</ListCallEventDetailByContactIdResponse>
```

`JSON` 格式

```
{
    "Data":{
        "Caller":"80315543",
        "Callee":"13501215646",
        "CallType":"Outbound",
        "ReleaseAgent":"agent",
        "ReleaseReason":"487-Request Terminated",
        "Events":{
            "CallEventDetail":[
                {
                    "TimeStamp":"1555492246000",
                    "Status":"Dialing",
                    "AgentName":"cloudcallcenter",
                    "Event":"Dial",
                    "Duration":9,
                    "DetailData":{
                        "EventType":"agent"
                    },
                    "CallMode":"Outbound"
                },
                {
                    "TimeStamp":"1555492259000",
                    "Status":"Handling",
                    "AgentName":"cloudcallcenter",
                    "Event":"End",
                    "Duration":16,
                    "DetailData":{
                        "HangUper":"byeSystem",
                        "EventType":"agent"
                    },
                    "CallMode":"Outbound"
                },
                {
                    "TimeStamp":"1555492259000",
                    "AgentName":"cloudcallcenter",
                    "Event":"Handle",
                    "Duration":0,
                    "DetailData":{
                        "EventType":"agent"
                    },
                    "CallMode":"Outbound"
                }
            ]
        },
        "StartTime":"1555492246000"
    },
    "HttpStatusCode":200,
    "RequestId":"7BEEA660-A45A-45E3-98CC-AFC65E715C23",
    "Success":true,
    "Code":"OK"
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

