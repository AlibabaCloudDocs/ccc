API变更内容（2.x版本） 
===================================



为了方便1.0用户更好地体验和迁移到2.0，这里列出了2.0API相对于1.0的改动。

此文档目前仍在更新中。

配置 
-----------------------



|---------------------------------|--------------------|------|----------------------------------|
| 1.0                             | 2.0                | 是否上线 | 说明                               |
| GetConfig                       | ListConfigItems    | 是    | 2.0 中配置项的获取由该接口统一负责。             |
| ListConfig                      | ListConfigItems    | 是    | 2.0 中配置项的获取由该接口统一负责。             |
| GetServiceExtensions            |                    |      | 2.0 中取消该接口，不再使用路由点这个概念。          |
| RefreshToken                    |                    |      | 2.0 中取消，使用GetLoginDetails代替。     |
| RequestLoginInfo                | GetLoginDetails    | 是    | 2.0 返回值做了调整，具体参考API文档。           |
| LaunchAppraise                  |                    |      | 即将发布                             |
| LaunchShortMessageAppraise      | SendSmsMessage     |      | 即将发布                             |
| GetTURNCredentials              | GetTurnCredentials | 是    | 2.0 入参UserId改为选填，默认返回当前接口调用者的信息。 |
| GetTURNServerList               | GetTurnServerList  | 是    | 出入参无变化。                          |
| ListTrunkProviders              |                    |      | 近期发布                             |
| ListTrunksOfSkillGroup          |                    |      | 近期发布                             |
| ModifyPrimaryTrunksOfSkillGroup |                    |      | 近期发布                             |
| DisableTrunkProviders           |                    |      | 近期发布                             |



联系流 
------------------------



|--------------------------------------|------------------|---|--------------------------------------|
| ListIvrTrackingDetail                |                  |   | 即将发布                                 |
| CreateContactFlow                    |                  |   | 暂不开放，IVR相关的操作目前仅支持在云呼工作台进行。          |
| CommitContactFlowVersionModification |                  |   | 暂不开放，IVR相关的操作目前仅支持在云呼工作台进行。          |
| GetRoutePoint                        |                  |   | 2.0 中取消该接口，不再使用路由点这个概念。              |
| ListContactFlows                     | ListContactFlows | 是 | 2.0 改为分页查询，入参新增了Type字段，支持了根据IVR类型查询。 |
| PublishContactFlowVersion            |                  |   | 暂不开放，IVR相关的操作目前仅支持在云呼工作台进行。          |



权限 
-----------------------



|-----------|-----------|---|--------------|
| ListRoles | ListRoles | 是 | 2.0 返回值做了精简。 |



号码管理 
-------------------------



|-------------------------------|---------------------------|---|--------------------------------------------------------------------------------------------------------|
| AddPhoneNumber                | AddPhoneNumbers           | 是 | 2.0 支持批量导入，传入String类型的NumberList，格式\["num1", "num2"\]                                                  |
| RemovePhoneNumber             | RemovePhoneNumbers        | 是 | 2.0 支持批量删除，传入String类型的NumberList                                                                       |
| ModifyPhoneNumber             | ModifyPhoneNumber         | 是 | 2.0 移除了号码对应技能组的修改，由AddPhoneNumberToSkillGroups和RemovePhoneNumberFromSkillGroups负责。接口返回值做了精简，只返回接口调用状态。 |
| ListPhoneNumbers              | ListPhoneNumbers          | 是 | 2.0 入参新增了SearchPattern字段，支持了根据号码模糊查询。                                                                  |
| GetNumberRegionInfo           | GetNumberLocation         | 是 | 无变化                                                                                                    |
| PickGlobalOutboundNumbers     | PickOutboundNumbers       | 是 | 无变化                                                                                                    |
| AddBulkPhoneNumbers           | AddPhoneNumbers           | 是 | 2.0 号码入参形式改变，修改为传入String类型的NumberList，格式\["num1", "num2"\]                                             |
| CallOnlinePrivacyNumber       |                           |   | 2.0 中取消。此为虚拟号码相关接口，目前与云呼对接的号码供应商已不再提供虚拟号码业务。                                                           |
| ListOutboundPhoneNumberOfUser | ListOutboundNumbersOfUser | 是 | 2.0 入参新增了SkillGroupIdList字段，支持了根据技能组列表查询。                                                              |
| ModifyPrivacyNumberCallDetail |                           |   | 2.0 中取消。此为虚拟号码相关接口，目前与云呼对接的号码供应商已不再提供虚拟号码业务。                                                           |



呼叫 
-----------------------



|--------------------|--------------------|---|-------------------|
| StartBack2BackCall |                    |   | 即将发布              |
| DialEx             | MakePredictiveCall |   | 近期发布，目前仅支持转接到IVR。 |



技能组管理 
--------------------------



|---------------------------------|---------------------------------------------------------|---|-------------------------------------------------------------------------------------------------------------------------------------------|
| CreateSkillGroup                | CreateSkillGroup                                        | 是 | 2.0 入参做了精简，区分了Name与DisplayName，简单说DisplayName为展示名，可以包含中文。Name是SkillGroupId的组成部分，不支持中文。                                                    |
| DeleteSkillGroup                | DeleteSkillGroup                                        | 是 | 2.0 入参新增了force参数，当为false时，如果技能组有绑定的号码或坐席则无法删除。                                                                                            |
| ModifySkillGroup                | ModifySkillGroup                                        | 是 | 2.0 移除了技能组对绑定号码和坐席的修改，由AddNumbersToSkillGroup \& RemovePhoneNumbersFromSkillGroup 以及 AddUsersToSkillGroup \& RemoveUsersFromSkillGroup负责。 |
| ListSkillGroups                 | ListSkillGroups                                         | 是 | 2.0 改为分页查询，入参新增了SearchPattern字段，支持了根据name或displayName模糊查询。技能组所绑定的号码信息请调用ListPhoneNumbersOfSkillGroup查看。                                   |
| ListSkillGroupsOfUser           | ListSkillLevelsOfUser                                   | 是 | 2.0 改为分页查询，入参新增了SearchPattern字段，支持了根据name或displayName模糊查询；新增IsMember字段，支持查询未与该用户绑定的技能组。技能组所绑定的号码信息请调用ListPhoneNumbersOfSkillGroup查看。      |
| ListUsersOfSkillGroup           | ListUserLevelsOfSkillGroup                              | 是 | 2.0 入参新增了SearchPattern字段，支持了根据坐席的用户名或姓名模糊查询；新增IsMember字段，支持查询未与该技能组绑定的用户。用户的详细信息请调用GetUser查看。                                             |
| ModifySkillGroupOutboundNumbers | AddNumbersToSkillGroup RemovePhoneNumbersFromSkillGroup | 是 | 2.0 修改技能组外呼号码由2个接口负责。                                                                                                                     |
| RemoveUsersFromSkillGroup       | RemoveUsersFromSkillGroup                               | 是 | 2.0 入参改为传入UserIdList，类型为String，格式\["uid01", "uid02"\]                                                                                     |
| ListTransferableSkillGroups     | ListBriefSkillGroups                                    | 是 | 2.0 改为分页查询，入参新增了SearchPattern字段，支持了根据name或displayName模糊查询。                                                                                |



客服 
-----------------------



|------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| CreateUser             | CreateUser                                                                                                                                                                                                                    | 是 | 2.0 技能组和等级传参有变化，原来是两个对立的List,现在需要SkillLevelList, 类型为String。格式参考API文档。WorkMode 参数新增，表示离线坐席还是在线。接口返回值添加了其他的用户详细信息。                                                                                |
| RemoveUsers            | RemoveUsers                                                                                                                                                                                                                   | 是 | 2.0 入参改为传入UserIdList，类型为String，格式\["uid01","uid02"\]                                                                                                                                            |
| ModifyUser             | ModifyUser  ModifySkillLevelsOfUser  AddSkillGroupsToUser  RemoveSkillGroupsFromUser  AddPersonalNumbersToUser  RemovePersonalNumbersFromUser | 是 | 2.0 ModifyUser新增WorkMode参数。对应技能组的添加和移除由AddSkillGroupsToUser和RemoveSkillGroupsFromUser负责。修改坐席技能等级由ModifySkillLevelsOfUser负责。添加移除个人专属号码由AddPersonalNumbersToUser和RemovePersonalNumbersFromUser负责。 |
| GetUser                | GetUser                                                                                                                                                                                                                       | 是 | 2.0 支持根据UserId或者Extension分机号获取用户信息，用户对应的技能组信息请调用ListSkillLevelsOfUser查看。                                                                                                                        |
| GetUserByExtension     | GetUser                                                                                                                                                                                                                       | 是 | 2.0 支持根据UserId或者Extension分机号获取用户信息，用户对应的技能组信息请调用ListSkillLevelsOfUser查看。                                                                                                                        |
| ListUsers              | ListUsers                                                                                                                                                                                                                     | 是 | 2.0 入参新增了SearchPattern字段，支持根据loginName, displayName查询。                                                                                                                                          |
| FindUsers              | ListUsers                                                                                                                                                                                                                     | 是 | 2.0 入参新增了SearchPattern字段，支持根据loginName, displayName查询。                                                                                                                                          |
| AssignUsers            | AssignUsers                                                                                                                                                                                                                   | 是 | 2.0 入参改为传入RamIdList，类型为String，格式\["ramId01", "ramId02"\]，同时传入WorkMode指定坐席的工作模式。                                                                                                                 |
| ListRealTimeAgent      | ListRealtimeAgentStates                                                                                                                                                                                                       | 是 | 2.0 改为分页查询，入参新增了多个字段，支持了根据技能组，坐席，状态列表查询。                                                                                                                                                        |
| ResetUserStatus        | ResetAgentState                                                                                                                                                                                                               | 是 | 2.0 入参改为DeviceId，DeviceId由ListDevices接口获取。                                                                                                                                                      |
| ListAgentEvents        | ListAgentStateLogs                                                                                                                                                                                                            |   | 即将发布                                                                                                                                                                                            |
| ModifySkillGroupOfUser | AddSkillGroupsToUser RemoveSkillGroupsFromUser                                                                                                                                                                                | 是 | 2.0 修改用户绑定的技能组由2个接口负责。                                                                                                                                                                          |
| ListInstancesOfUser    | ListInstancesOfUser                                                                                                                                                                                                           | 是 | 2.0 返回值做了精简，只返回实例信息。相关的用户信息，号码信息等请调用GetInstance接口。                                                                                                                                              |



录音 
-----------------------



|---------------------------|------------------------------------------------------------|---|--------------------------------------------------------------------------|
| DownloadRecording         | GetMonoRecording                                           | 是 | 2.0 入参由FileName改为ContactId，通过ListCallDetailRecords获取通话ID，即可直接下载录音。       |
| ListRecordingsByContactId |                                                            | 是 | 2.0 该接口废弃。FileName和Url由对应的录音接口提供，其他信息请调用ListCallDetailRecords等获取。        |
| DownloadAllTypeRecording  | GetMonoRecording  GetMultiChannelRecording |   |                                                                          |
| ListRecordingOfDualTrack  | GetMultiChannelRecording                                   | 是 | 2.0 入参改为掺入ContactId，返回值做了精简，只返回文件名和Url。其他相关信息请调用ListCallDetailRecords获取。 |



报表 
-----------------------



|-------------------------------------------|-----------------------------|---|-------------------------------------------------------------------------------------|
| ListCallDetailRecords                     | ListCallDetailRecords       | 是 | 2.0 录音信息需要调用录音相关接口，满意度相关信息后续会支持。                                                    |
| GetConversationDetailByContactId          |                             |   | 待开发。只有开通了智能质检或实时语音文本流的用户才可以正常调用该接口。                                                 |
| ListRecentCallRecords                     | ListRecentCallDetailRecords | 是 | 无变化                                                                                 |
| GenerateAgentStatisticReport              | ListHistoricalAgentReport   | 是 | 2.0 入参改为AgentIdList即UserIdList，类型为String，格式\["uid01", "uid02"\]。返回参数格式调整，具体参考API文档。 |
| GetInstanceSummaryReport                  |                             |   | 即将发布                                                                                |
| GetInstanceSummaryReportByInterval        |                             |   | 即将发布                                                                                |
| GetInstanceSummaryReportSinceMidnight     |                             |   | 即将发布                                                                                |
| ListAgentStates                           | ListRealtimeAgentStates     | 是 | 2.0 新增入参AgentName，支持根据AgentName即坐席姓名模糊查询。                                           |
| ListAgentStateLogs                        | ListAgentStateLogs          |   | 即将发布                                                                                |
| ListAgentSummaryReports                   | ListHistoricalAgentReport   | 是 | 2.0 入参改为AgentIdList即UserIdList，类型为String，格式\["uid01", "uid02"\]。                    |
| ListAgentSummaryReportsByInterval         |                             |   | 即将发布                                                                                |
| GetAgentData                              | ListHistoricalAgentReport   | 是 | 2.0 参数AgentIdList指定单个坐席时等价于GetAgentData。                                            |
| ListAgentSummaryReportsSinceMidnight      | ListHistoricalAgentReport   | 是 | 2.0 StartTime，StopTime为选填项，不填默认查询当天的数据。                                             |
| ListSkillGroupStates                      |                             |   | 即将发布                                                                                |
| ListSkillGroupSummaryReports              |                             |   | 即将发布                                                                                |
| ListSkillGroupSummaryReportsByInterval    |                             |   | 即将发布                                                                                |
| ListSkillGroupSummaryReportsSinceMidnight |                             |   | 即将发布                                                                                |
| ListCallMeasureSummaryReports             |                             |   | 即将发布                                                                                |
| ListCallEventDetailByContactId            |                             |   | 即将发布                                                                                |
| GetCallMeasureSummaryReport               |                             |   | 即将发布                                                                                |



问题排查 
-------------------------



|-------------------------|---|---|-----------------|---|
| AddAgentDevice          |   |   | 由于架构调整，2.0 中取消。 |   |
| ModifyAgentDevice       |   |   | 由于架构调整，2.0 中取消。 |   |
| ListAgentDevices        |   |   | 由于架构调整，2.0 中取消。 |   |
| GetRecordOssUploadParam |   |   | 由于架构调整，2.0 中取消。 |   |
| SaveWebRTCStats         |   |   | 近期发布            |   |



实例管理 
-------------------------



|-------------|-------------|---|---------------------------|
| GetInstance | GetInstance | 是 | 2.0 返回参数结构做了调整，详情参考API文档。 |



满意度 
------------------------



|---------------------|------------------|---|------------------------------|
| CreateVoiceAppraise |                  |   | 近期发布                         |
| ListVoiceAppraise   | ListContactFlows | 是 | 2.0 中查看IVR包括满意度IVR，统一由该接口负责。 |



短信 
-----------------------



|----------------------------|-----------------|---|----------------------|
| GetSmsConfig               | ListConfigItems | 是 | 2.0 中配置项的获取由该接口统一负责。 |
| SendPredefinedShortMessage | SendSmsMessage  |   | 即将发布                 |



