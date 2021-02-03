API概述
=====

我们为您汇总了云呼叫中心 CCC 所有可调用 API，具体接口信息请参阅相关文档。由于文档更新可能延迟，你可以使用[可视化调试API控制台](https://api.aliyun.com/new#/?product=CCC) ，帮您快速调试。

**认证方式说明如下：**

**BEARERTOKEN** ：即为通过API URL 发起 HTTP/HTTPS GET请求，详情查看 [调用方式](http://help.aliyun-inc.com/dochelp/~~85147~~);

**AK** ：即阿里云通用的，通过AccessKey调用SDK，来访问API。

配置相关接口 {#LtHrC}
---------------

|                                                               接口                                                               |        描述         |      认证方式      |
|--------------------------------------------------------------------------------------------------------------------------------|-------------------|----------------|
| [GetConfig](https://help.aliyun.com/document_detail/63027.html?spm=a2c4g.11186623.6.619.35a14641j8KIUz)                        | 获取配置              | BEARERTOKEN/AK |
| [ListConfig](https://help.aliyun.com/document_detail/70128.html?spm=a2c4g.11186623.6.620.4bb12c61y129rP)                       | 批量获取配置            | BEARERTOKEN/AK |
| [GetServiceExtensions](https://help.aliyun.com/document_detail/63028.html?spm=a2c4g.11186623.6.621.439e372dnPikys)             | 获取服务号码            | BEARERTOKEN/AK |
| [RefreshToken](http://help.aliyun-inc.com/dochelp/~~63029~~)                                                                   | 刷新令牌              | BEARERTOKEN/AK |
| [RequestLoginInfo](https://help.aliyun.com/document_detail/63030.html?spm=a2c4g.11186623.6.623.a6f8238fqoIrXr)                 | 登陆信息              | BEARERTOKEN/AK |
| [LaunchAppraise](https://help.aliyun.com/document_detail/71562.html?spm=a2c4g.11186623.6.624.25bae285IXWCUV)                   | 发送语音满意度           | BEARERTOKEN/AK |
| [LaunchShortMessageAppraise](https://help.aliyun.com/document_detail/88312.html?spm=a2c4g.11186623.6.625.3cff6dd10e1eHa)       | 发送短信满意度           | BEARERTOKEN/AK |
| [GetTURNCredentials](https://help.aliyun.com/document_detail/131786.html?spm=a2c4g.11186623.6.626.6da35624R2qXd4)              | 获取语音专线的用户名密码      | BEARERTOKEN/AK |
| [GetTURNServerList](https://help.aliyun.com/document_detail/131791.html?spm=a2c4g.11186623.6.627.75f98b98KGPBMX)               | 获取语音专线列表          | BEARERTOKEN/AK |
| [ListTrunkProviders](https://help.aliyun.com/document_detail/198048.html?spm=a2c4g.11186623.6.628.58bc5b8c702OGn)              | 查询指定用户下正在使用的供应商信息 | BEARERTOKEN/AK |
| [ListTrunksOfSkillGroup](https://help.aliyun.com/document_detail/198042.html?spm=a2c4g.11186623.6.629.4d81129fQVgPNW)          | 查询用户技能组下中继线路配置信息  | BEARERTOKEN/AK |
| [ModifyPrimaryTrunksOfSkillGroup](https://help.aliyun.com/document_detail/198051.html?spm=a2c4g.11186623.6.630.5a995806ijA6Y9) | 修改技能组线路中继配置信息     | BEARERTOKEN/AK |
| [DisableTrunkProviders](https://help.aliyun.com/document_detail/198036.html?spm=a2c4g.11186623.6.631.7fc2794bAYEsSk)           | 注销供应商             | BEARERTOKEN/AK |

联系流相关接口 {#feooS}
----------------

|                                                                 接口                                                                  |    描述     |      认证方式      |
|-------------------------------------------------------------------------------------------------------------------------------------|-----------|----------------|
| [ListIvrTrackingDetail](https://help.aliyun.com/document_detail/109327.html?spm=a2c4g.11186623.6.633.1433258ahokp3F)                | 获取IVR轨迹   | BEARERTOKEN/AK |
| [CreateContactFlow](https://help.aliyun.com/document_detail/198022.html?spm=a2c4g.11186623.6.634.71406df3BEpXfi)                    | 创建联系流     | BEARERTOKEN/AK |
| [CommitContactFlowVersionModification](https://help.aliyun.com/document_detail/198019.html?spm=a2c4g.11186623.6.635.5d222cee4VTq59) | 提交联系流改动   | BEARERTOKEN/AK |
| [GetRoutePoint](https://help.aliyun.com/document_detail/135292.html?spm=a2c4g.11186623.6.636.4a4731afoWjZxw)                        | 获取联系流的路由点 | BEARERTOKEN/AK |
| [ListContactFlows](https://help.aliyun.com/document_detail/63032.html?spm=a2c4g.11186623.6.637.1db920d3WLDbvG)                      | 获取IVR流程列表 | BEARERTOKEN/AK |
| [PublishContactFlowVersion](https://help.aliyun.com/document_detail/92782.html?spm=a2c4g.11186623.6.638.60e16232t9KboZ)             | 发布IVR流程   | BEARERTOKEN/AK |

权限相关接口 {#UpnLe}
---------------

|                                                   接口                                                    |  描述  |      认证方式      |
|---------------------------------------------------------------------------------------------------------|------|----------------|
| [ListRoles](https://help.aliyun.com/document_detail/63034.html?spm=a2c4g.11186623.6.640.46627a013KoHiG) | 角色列表 | BEARERTOKEN/AK |

号码管理相关接口 {#AYDpZ}
-----------------

|                                                             接口                                                              |      描述       |      认证方式      |
|-----------------------------------------------------------------------------------------------------------------------------|---------------|----------------|
| [AddPhoneNumber](https://help.aliyun.com/document_detail/63036.html?spm=a2c4g.11186623.6.642.60b148961Xi9es)                | 新增号码          | BEARERTOKEN/AK |
| [RemovePhoneNumber](https://help.aliyun.com/document_detail/63039.html?spm=a2c4g.11186623.6.643.3cf71575HItSLK)             | 删除号码          | BEARERTOKEN/AK |
| [ModifyPhoneNumber](https://help.aliyun.com/document_detail/63038.html?spm=a2c4g.11186623.6.644.1bc7235duP1wi8)             | 修改号码          | BEARERTOKEN/AK |
| [ListPhoneNumbers](http://help.aliyun-inc.com/dochelp/~~63037~~)                                                            | 电话列表          | BEARERTOKEN/AK |
| [GetNumberRegionInfo](https://help.aliyun.com/document_detail/70127.html?spm=a2c4g.11186623.6.646.2d965136nzjoNm)           | 获取号码归属地       | BEARERTOKEN/AK |
| [PickGlobalOutboundNumbers](https://help.aliyun.com/document_detail/70126.html?spm=a2c4g.11186623.6.647.6d20af708N0Wcn)     | 按照被叫归属地自主选择号码 | BEARERTOKEN/AK |
| [PickLocalNumber](https://help.aliyun.com/document_detail/198052.html?spm=a2c4g.11186623.6.648.6d2270c2igswK5)              | 本地号码优先策略      | BEARERTOKEN/AK |
| [PickOutboundNumbers](https://help.aliyun.com/document_detail/198053.html?spm=a2c4g.11186623.6.649.1df52783b9QZ1f)          | 获取外呼号码        | BEARERTOKEN/AK |
| [AddBulkPhoneNumbers](https://help.aliyun.com/document_detail/111185.html?spm=a2c4g.11186623.6.650.6f1b5dbakKfbYg)          | 批量新增号码        | BEARERTOKEN/AK |
| [CallOnlinePrivacyNumber](https://help.aliyun.com/document_detail/94807.html?spm=a2c4g.11186623.6.651.47c46f30JzPklS)       | 虚拟号码外呼        | BEARERTOKEN/AK |
| [ListOutboundPhoneNumberOfUser](https://help.aliyun.com/document_detail/92453.html?spm=a2c4g.11186623.6.652.561e5e572Ax72v) | 获取坐席外呼号码      | BEARERTOKEN/AK |
| [ModifyPrivacyNumberCallDetail](https://help.aliyun.com/document_detail/94928.html?spm=a2c4g.11186623.6.653.77b22cb7NxlAcE) | 更新话务ID        | BEARERTOKEN/AK |

呼叫相关接口 {#y8rnQ}
---------------

|                                                        接口                                                        |  描述  |      认证方式      |
|------------------------------------------------------------------------------------------------------------------|------|----------------|
| [StartBack2BackCall](https://help.aliyun.com/document_detail/74265.html?spm=a2c4g.11186623.6.655.4e543db6EiISsO) | 双呼   | BEARERTOKEN/AK |
| [DialEx](https://help.aliyun.com/document_detail/142649.html?spm=a2c4g.11186623.6.656.b2223d44Jja6Uf)            | 后台外呼 | BEARERTOKEN/AK |

技能组相关接口 {#eNXn5}
----------------

|                                                               接口                                                               |       描述        |      认证方式      |
|--------------------------------------------------------------------------------------------------------------------------------|-----------------|----------------|
| [CreateSkillGroup](https://help.aliyun.com/document_detail/63041.html?spm=a2c4g.11186623.6.658.39f0573aNjucHZ)                 | 创建技能组           | BEARERTOKEN/AK |
| [DeleteSkillGroup](https://help.aliyun.com/document_detail/63043.html?spm=a2c4g.11186623.6.659.31b33a88NcPD3y)                 | 删除技能组           | BEARERTOKEN/AK |
| [ModifySkillGroup](https://help.aliyun.com/document_detail/63047.html?spm=a2c4g.11186623.6.660.410a6665PESE5M)                 | 修改技能组           | BEARERTOKEN/AK |
| [ListSkillGroups](https://help.aliyun.com/document_detail/63044.html?spm=a2c4g.11186623.6.661.2cc7d126dVuIXg)                  | 获取技能组列表         | BEARERTOKEN/AK |
| [ListSkillGroupsOfUser](https://help.aliyun.com/document_detail/63045.html?spm=a2c4g.11186623.6.662.56f75549fT7Fyu)            | 坐席相关联技能组列表      | BEARERTOKEN/AK |
| [ListUsersOfSkillGroup](https://help.aliyun.com/document_detail/63046.html?spm=a2c4g.11186623.6.663.3cdb31bepPO3n4)            | 技能组相关联客服列表      | BEARERTOKEN/AK |
| [ModifySkillGroupOutboundNumbers](https://help.aliyun.com/document_detail/117079.html?spm=a2c4g.11186623.6.664.2e01110bGsQadX) | 修改技能组外呼号码       | BEARERTOKEN/AK |
| [RemoveUsersFromSkillGroup](https://help.aliyun.com/document_detail/95881.html?spm=a2c4g.11186623.6.665.7d792cc9CfXR8H)        | 从技能组中删除坐席       | BEARERTOKEN/AK |
| [ListTransferableSkillGroups](https://help.aliyun.com/document_detail/198016.html?spm=a2c4g.11186623.6.666.63dc66d2DI3Qkg)     | 获取呼叫中心实例的可转接技能组 | BEARERTOKEN/AK |

坐席相关接口 {#n4asg}
---------------

|                                                          接口                                                          |      描述       |      认证方式      |
|----------------------------------------------------------------------------------------------------------------------|---------------|----------------|
| [CreateUser](https://help.aliyun.com/document_detail/63049.html?spm=a2c4g.11186623.6.668.71204a53ISSxLl)             | 新增客服          | BEARERTOKEN/AK |
| [RemoveUsers](https://help.aliyun.com/document_detail/63054.html?spm=a2c4g.11186623.6.669.741a5704YD3JzF)            | 移除客服          | BEARERTOKEN/AK |
| [ModifyUser](https://help.aliyun.com/document_detail/63053.html?spm=a2c4g.11186623.6.670.30913ad6BQ75XR)             | 修改客服          | BEARERTOKEN/AK |
| [GetUser](https://help.aliyun.com/document_detail/63051.html?spm=a2c4g.11186623.6.671.60cc3e34qFWJ3T)                | 客服信息          | BEARERTOKEN/AK |
| [ListUsers](https://help.aliyun.com/document_detail/63052.html?spm=a2c4g.11186623.6.672.4f755ccbVmqXu1)              | 获取客服列表        | BEARERTOKEN/AK |
| [AssignUsers](https://help.aliyun.com/document_detail/63050.html?spm=a2c4g.11186623.6.673.79021ebckwiThl)            | 导入客服          | BEARERTOKEN/AK |
| [ListRealTimeAgent](https://help.aliyun.com/document_detail/70131.html?spm=a2c4g.11186623.6.674.3cb972f6y8tWWG)      | 获取客服实时数据列表    | BEARERTOKEN/AK |
| [ResetUserStatus](https://help.aliyun.com/document_detail/134877.html?spm=a2c4g.11186623.6.675.22a722b37LlhlN)       | 重置异常坐席状态      | BEARERTOKEN/AK |
| [FindUsers](https://help.aliyun.com/document_detail/92787.html?spm=a2c4g.11186623.6.676.37f91fd9KgENp0)              | 查询客服信息。       | BEARERTOKEN/AK |
| [ListAgentEvents](https://help.aliyun.com/document_detail/111186.html?spm=a2c4g.11186623.6.677.3dda2958Sc2t3o)       | 查询坐席日志信息      | BEARERTOKEN/AK |
| [ModifySkillGroupOfUser](https://help.aliyun.com/document_detail/92785.html?spm=a2c4g.11186623.6.678.723b45fcQZGRam) | 修改坐席从属的技能组    | BEARERTOKEN/AK |
| [GetUserByExtension](https://help.aliyun.com/document_detail/197951.html?spm=a2c4g.11186623.6.679.5d271e13GOKicd)    | 通过分机号获取客服信息   | BEARERTOKEN/AK |
| [ListInstancesOfUser](https://help.aliyun.com/document_detail/198027.html?spm=a2c4g.11186623.6.680.29be6c09hovvt7)   | 获取当前用户所属的呼叫中心 | BEARERTOKEN/AK |

录音相关接口 {#WzhE9}
---------------

|                                                            接口                                                            |     描述     |      认证方式      |
|--------------------------------------------------------------------------------------------------------------------------|------------|----------------|
| [DownloadRecording](https://help.aliyun.com/document_detail/65295.html?spm=a2c4g.11186623.6.682.3ff322beFomIzr)          | 下载录音       | BEARERTOKEN/AK |
| [ListRecordingsByContactId](https://help.aliyun.com/document_detail/198091.html?spm=a2c4g.11186623.6.683.70345d34yD9QV5) | 根据话务ID查询录音 | BEARERTOKEN/AK |
| [DownloadAllTypeRecording](https://help.aliyun.com/document_detail/127210.html?spm=a2c4g.11186623.6.684.6e9d1d6dAYYoSX)  | 下载双轨录音     | BEARERTOKEN/AK |
| [ListRecordingOfDualTrack](https://help.aliyun.com/document_detail/98949.html?spm=a2c4g.11186623.6.685.2c86187fXjUDkz)   | 获取通话的双轨录音  | BEARERTOKEN/AK |

报表相关接口 {#23QYj}
---------------

|                                                                   接口                                                                    |       描述       |      认证方式      |
|-----------------------------------------------------------------------------------------------------------------------------------------|----------------|----------------|
| [ListCallDetailRecords](https://help.aliyun.com/document_detail/65296.html?spm=a2c4g.11186623.6.687.539d2ca8msMnQ1)                     | 获取通话详单         | BEARERTOKEN/AK |
| [GetConversationDetailByContactId](https://help.aliyun.com/document_detail/91384.html?spm=a2c4g.11186623.6.688.37ff53c6idWYZt)          | 获取通话文本信息       | BEARERTOKEN/AK |
| [ListRecentCallRecords](https://help.aliyun.com/document_detail/88589.html?spm=a2c4g.11186623.6.689.4ed51a014d2AP4)                     | 坐席工作台获取通话记录    | BEARERTOKEN/AK |
| [GenerateAgentStatisticReport](https://help.aliyun.com/document_detail/73242.html?spm=a2c4g.11186623.6.690.677a4c51xKqQ4I)              | 坐席报表数据         | BEARERTOKEN/AK |
| [GetInstanceSummaryReport](https://help.aliyun.com/document_detail/92457.html?spm=a2c4g.11186623.6.691.816c46f3ooCQWa)                  | 实例汇总报表         | BEARERTOKEN/AK |
| [GetInstanceSummaryReportByInterval](https://help.aliyun.com/document_detail/92459.html?spm=a2c4g.11186623.6.692.8194687fJiaPuH)        | 实例分段汇总报表       | BEARERTOKEN/AK |
| [GetInstanceSummaryReportSinceMidnight](https://help.aliyun.com/document_detail/92458.html?spm=a2c4g.11186623.6.693.2a5f6d76QLCrQ8)     | 实例当日汇总报表       | BEARERTOKEN/AK |
| [ListAgentStates](https://help.aliyun.com/document_detail/90007.html?spm=a2c4g.11186623.6.694.4db51d0ayx4Z2B)                           | 获取坐席状态         | BEARERTOKEN/AK |
| [ListAgentStateLogs](https://help.aliyun.com/document_detail/198023.html?spm=a2c4g.11186623.6.695.36851d4976opy6)                       | 查询坐席状态日志       | BEARERTOKEN/AK |
| [ListAgentSummaryReports](https://help.aliyun.com/document_detail/92428.html?spm=a2c4g.11186623.6.696.1c6b10aaRmQTXu)                   | 坐席汇总报表         | BEARERTOKEN/AK |
| [ListAgentSummaryReportsByInterval](https://help.aliyun.com/document_detail/92437.html?spm=a2c4g.11186623.6.697.4aa04204bbJs9v)         | 坐席的分段汇总报表      | BEARERTOKEN/AK |
| [ListAgentSummaryReportsSinceMidnight](https://help.aliyun.com/document_detail/92442.html?spm=a2c4g.11186623.6.698.17ab2710Tl2XDR)      | 查询坐席指标的当天汇总报表  | BEARERTOKEN/AK |
| [ListSkillGroupStates](https://help.aliyun.com/document_detail/92452.html?spm=a2c4g.11186623.6.699.67163320wATQOi)                      | 技能组瞬时状态列表      | BEARERTOKEN/AK |
| [ListSkillGroupSummaryReports](https://help.aliyun.com/document_detail/92450.html?spm=a2c4g.11186623.6.700.34b37ff6izdr3o)              | 技能组汇总报表        | BEARERTOKEN/AK |
| [ListSkillGroupSummaryReportsByInterval](https://help.aliyun.com/document_detail/92451.html?spm=a2c4g.11186623.6.701.3b3f6a9aCsfQeO)    | 技能组的分段汇总报表     | BEARERTOKEN/AK |
| [ListSkillGroupSummaryReportsSinceMidnight](https://help.aliyun.com/document_detail/92432.html?spm=a2c4g.11186623.6.702.63804395HhwzHq) | 技能组当天汇总报表      | BEARERTOKEN/AK |
| [ListCallMeasureSummaryReports](https://help.aliyun.com/document_detail/95671.html?spm=a2c4g.11186623.6.703.31a73440FhGrPf)             | 查询计量数据列表       | BEARERTOKEN/AK |
| [ListCallEventDetailByContactId](https://help.aliyun.com/document_detail/116011.html?spm=a2c4g.11186623.6.704.2c2974562Kc3KF)           | 根据通话ID获取通话操作日志 | BEARERTOKEN/AK |
| [GetCallMeasureSummaryReport](https://help.aliyun.com/document_detail/95670.html?spm=a2c4g.11186623.6.705.7c165709w9FQCF)               | 查询计量数据列表       | BEARERTOKEN/AK |

问题排查相关接口 {#MH1VU}
-----------------

|------------------------------------------------------------------------------------------------------------------------|--------------|----------------|
| 接口                                                                                                                     | 描述           | 认证方式           |
| [AddAgentDevice](https://help.aliyun.com/document_detail/120933.html?spm=a2c4g.11186623.6.707.5b9d395eCBMGMX)          | 保存坐席设备信息     | BEARERTOKEN/AK |
| [ModifyAgentDevice](https://help.aliyun.com/document_detail/120934.html?spm=a2c4g.11186623.6.708.4fefd94eo24k2e)       | 修改坐席登录状态     | BEARERTOKEN/AK |
| [ListAgentDevices](https://help.aliyun.com/document_detail/120935.html?spm=a2c4g.11186623.6.709.1130274f2iMYDC)        | 获取坐席设备信息     | BEARERTOKEN/AK |
| [GetRecordOssUploadParam](https://help.aliyun.com/document_detail/120936.html?spm=a2c4g.11186623.6.710.b3814846Z7G8Na) | 获取录音上传参数     | BEARERTOKEN/AK |
| [SaveWebRTCStats](https://help.aliyun.com/document_detail/122120.html?spm=a2c4g.11186623.6.711.28475886OrUL9u)         | 保存WebRTC统计信息 | BEARERTOKEN/AK |

实例管理相关接口 {#yzeIR}
-----------------

|-----------------------------------------------------------------------------------------------------------|------------|----------------|
| 接口                                                                                                        | 描述         | 认证方式           |
| [GetInstance](https://help.aliyun.com/document_detail/92736.html?spm=a2c4g.11186623.6.713.79b911b3CCXsGU) | 获取呼叫中心实例详情 | BEARERTOKEN/AK |

满意度相关接口 {#Iztly}
----------------

|--------------------------------------------------------------------------------------------------------------------|---------|----------------|
| 接口                                                                                                                 | 描述      | 认证方式           |
| [CreateVoiceAppraise](https://help.aliyun.com/document_detail/111567.html?spm=a2c4g.11186623.6.715.7d275785AdKcRJ) | 开通语音满意度 | BEARERTOKEN/AK |
| [ListVoiceAppraise](https://help.aliyun.com/document_detail/111569.html?spm=a2c4g.11186623.6.716.39802ac2NRhXMu)   | 语音满意度   | BEARERTOKEN/AK |

短信相关接口 {#zA1g4}
---------------

|--------------------------------------------------------------------------------------------------------------------------|--------|----------------|
| 接口                                                                                                                       | 描述     | 认证方式           |
| [GetSmsConfig](https://help.aliyun.com/document_detail/89914.html?spm=a2c4g.11186623.6.718.5bdb74567fANny)               | 获取短信配置 | BEARERTOKEN/AK |
| [SendPredefinedShortMessage](https://help.aliyun.com/document_detail/89915.html?spm=a2c4g.11186623.6.719.44332c4f9vfCW8) | 发送短信   | BEARERTOKEN/AK |

