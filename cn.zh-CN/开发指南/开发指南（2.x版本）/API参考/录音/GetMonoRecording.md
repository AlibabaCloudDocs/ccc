# GetMonoRecording

调用GetMonoRecording获取合成录音。

## 调试

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=CCC&api=GetMonoRecording&type=RPC&version=2020-07-01)

## 请求参数

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|Action|String|是|GetMonoRecording|系统规定参数。取值：GetMonoRecording。 |
|ContactId|String|是|job-65382141036893491|通话ID。 |
|InstanceId|String|是|ccc-test|呼叫中心实例ID。 |

## 返回数据

|名称|类型|示例值|描述|
|--|--|---|--|
|Code|String|OK|响应码。 |
|Data|Struct| |数据。 |
|FileName|String|job-65382141036893491.wav|文件名称。 |
|FileUrl|String|http://ccc-v2-online.oss-cn-shanghai.aliyuncs.com/ccc-record/job-65382141036893491.wav?Expires=1610910578&OSSAccessKeyId=KZEA4GDDtCg431rmXTiEhr1q&Signature=4bXjOtUYgXl2z9iWpk3tXxS8SGY%3D|文件下载地址。 |
|HttpStatusCode|Integer|200|HTTP状态码。 |
|Message|String|无|响应信息。 |
|RequestId|String|EEEE671A-3E24-4A04-81E6-6C4F5B39DF75|请求ID。 |

## 示例

请求示例

```
http(s)://[Endpoint]/?Action=GetMonoRecording
&ContactId=job-65382141036893491
&InstanceId=ccc-test
&<公共请求参数>
```

正常返回示例

`XML`格式

```
<RequestId>EEEE671A-3E24-4A04-81E6-6C4F5B39DF75</RequestId>
<Message>无</Message>
<HttpStatusCode>200</HttpStatusCode>
<Data>
    <FileUrl>http://ccc-v2-online.oss-cn-shanghai.aliyuncs.com/ccc-record/job-65382141036893491.wav?Expires=1610910578&amp;OSSAccessKeyId=KZEA4GDDtCg431rmXTiEhr1q&amp;Signature=4bXjOtUYgXl2z9iWpk3tXxS8SGY%3D</FileUrl>
    <FileName>job-65382141036893491.wav</FileName>
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
		"FileUrl": "http://ccc-v2-online.oss-cn-shanghai.aliyuncs.com/ccc-record/job-65382141036893491.wav?Expires=1610910578&OSSAccessKeyId=KZEA4GDDtCg431rmXTiEhr1q&Signature=4bXjOtUYgXl2z9iWpk3tXxS8SGY%3D",
		"FileName": "job-65382141036893491.wav"
	},
	"Code": "OK"
}
```

## 错误码

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|NotExists.InstanceId|The specified instance %s does not exist.|指定的呼叫中心实例不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/CCC)查看更多错误码。

