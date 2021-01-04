# 获取IVR轨迹

调用ListIvrTrackingDetail获取IVR轨迹,默认查询半个小时之内的数据。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=ListIvrTrackingDetail&type=RPC&version=2017-07-05)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|ListIvrTrackingDetail|系统规定参数。取值：**ListIvrTrackingDetail**。 |
|InstanceId|String|是|317a38bf-4883-4e00-b65d-761f4a8be106|呼叫中心实例ID |
|PageNumber|Integer|是|1|分页页码 |
|PageSize|Integer|是|20|分页大小 |
|ContactId|String|否|3433583180|话务ID |
|StartTime|Long|否|1541732850000|开始时间 |
|StopTime|Long|否|1541932850000|结束时间 |
|CallingNumber|String|否|17600311101|主叫号码 |
|CalledNumber|String|否|057126883102|被叫号码 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码 |
|HttpStatusCode|Integer|200|HTTP状态码 |
|IvrTrackingDetails|Struct| |获取的IVR轨迹 |
|List|Array of IvrTrackingDetail| |对象列表 |
|IvrTrackingDetail| | | |
|CalledNumber|String|057126883102|被叫号码 |
|CallingNumber|String|17600311101|主叫号码 |
|ContactId|String|3433583180|通话ID |
|Description|String|answer|描述信息 |
|DeviceID|String|null|IP地址 |
|FlowName|String|flow/acc2626/xxxx|IVR名称 |
|InputData|String|nui-I1gxblYz\_1\_1200\_当前时间是11:07:39|传入参数 |
|NodeName|String|node24000|节点名称 |
|NodeType|String|waitevent|节点类型\(nodeType\)包含: answer\(开始\) 、waitevent\(等待\)、getAssociateData\(获取随路数据\)、 kvget\(解析随路数据\)、getdigits\(获取收号信息\)、assign\(输出\) 、play\(放音\)、tts\(tts放音\) 、branching\(分支\)、branchitem\(分支项\) 、requestagent\(转人工\)、onesteptransfer\(转外线\) 、http\(函数\)、subflow\(子流程\)、exit\(退出子流程\)、hangup（结束）。 |
|OutputData|String|80206290|传出参数 |
|StartTime|Long|1541732850000|开始时间 |
|Status|String|\_tts\_success|状态 |
|StopTime|Long|1541932850000|结束时间 |
|TenantId|String|acc2626|租户ID |
|PageNumber|Integer|1|当前页码 |
|PageSize|Integer|10|分页大小 |
|TotalCount|Integer|3|对象总数 |
|Message|String|无|响应信息 |
|RequestId|String|2a644ab1-7db5-413c-a744-299247f6537e|请求ID |
|Success|Boolean|true|是否成功 |

## 示例

请求示例

```
http(s)://ccc.cn-shanghai.aliyuncs.com/?Action=ListIvrTrackingDetail
&InstanceId=317a38bf-4883-4e00-b65d-761f4a8be106
&PageNumber=1
&PageSize=20
&<公共请求参数>
```

正常返回示例

`XML` 格式

```
<ListIvrTrackingDetailResponse>
      <requestId>2a644ab1-7db5-413c-a744-299247f6537e</requestId>
      <success>true</success>
      <code>OK</code>
      <message></message>
      <httpStatusCode>200</httpStatusCode>
      <ivrTrackingDetails>
            <totalCount>16</totalCount>
            <pageNumber>1</pageNumber>
            <pageSize>10</pageSize>
            <list>
                  <flowName>flow/acc2626/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K_20181109110118/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K_20181109110118.flow</flowName>
                  <nodeName>node2</nodeName>
                  <nodeType>answer</nodeType>
                  <acid>3433583180</acid>
                  <callingNumber>17600311101</callingNumber>
                  <calledNumber>057126883102</calledNumber>
                  <startTime>2018-11-09 11:07:39.0</startTime>
                  <stopTime>2018-11-09 11:07:39.0</stopTime>
                  <status>_success</status>
                  <inputData></inputData>
                  <outputData></outputData>
                  <description>answer</description>
                  <deviceID></deviceID>
                  <tenantId>acc2626</tenantId>
            </list>
            <list>
                  <flowName>flow/acc2626/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K_20181109110118/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K_20181109110118.flow</flowName>
                  <nodeName>node2000</nodeName>
                  <nodeType>waitevent</nodeType>
                  <acid>3433583180</acid>
                  <callingNumber>17600311101</callingNumber>
                  <calledNumber>057126883102</calledNumber>
                  <startTime>2018-11-09 11:07:39.0</startTime>
                  <stopTime>2018-11-09 11:07:39.0</stopTime>
                  <status>_answer</status>
                  <inputData></inputData>
                  <outputData>80206290</outputData>
                  <description>wait for answer ok</description>
                  <deviceID></deviceID>
                  <tenantId>acc2626</tenantId>
            </list>
      </ivrTrackingDetails>
</ListIvrTrackingDetailResponse>
```

`JSON` 格式

```
{
    "requestId":"2a644ab1-7db5-413c-a744-299247f6537e",
    "success":true,
    "code":"OK",
    "message":null,
    "httpStatusCode":200,
    "ivrTrackingDetails":{
        "totalCount":16,
        "pageNumber":1,
        "pageSize":10,
        "list":[
            {
                "flowName":"flow/acc2626/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K_20181109110118/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K_20181109110118.flow","nodeName":"node2",
                "nodeType":"answer",
                "acid":"3433583180",
                "callingNumber":"17600311101",
                "calledNumber":"057126883102",
                "startTime":"2018-11-09 11:07:39.0",
                "stopTime":"2018-11-09 11:07:39.0",
                "status":"_success",
                "inputData":"",
                "outputData":"",
                "description":"answer",
                "deviceID":null,
                "tenantId":"acc2626"
            },
            {
                "flowName":"flow/acc2626/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K_20181109110118/d278629c-c687-4aa3-b044-4fe9b012e7ef_8Cvg_0mcsm6K_20181109110118.flow","nodeName":"node2000","nodeType":"waitevent","acid":"3433583180",
                "callingNumber":"17600311101",
                "calledNumber":"057126883102",
                "startTime":"2018-11-09 11:07:39.0",
                "stopTime":"2018-11-09 11:07:39.0",
                "status":"_answer",
                "inputData":"",
                "outputData":"80206290",
                "description":"wait for answer ok",
                "deviceID":null,
                "tenantId":"acc2626"
            }]
    }
}
```

## 错误码

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

