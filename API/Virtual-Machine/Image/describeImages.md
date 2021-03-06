# describeImages


## 描述
查询镜像信息列表。<br>
通过此接口可以查询到京东云官方镜像、第三方镜像、私有镜像、或其他用户共享给您的镜像。<br>
此接口支持分页查询，默认每页20条。


## 请求方式
GET

## 请求地址
https://vm.jdcloud-api.com/v1/regions/{regionId}/images

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**ids**|String[]|False||镜像ID列表，如果指定了此参数，其它参数可为空|
|**imageSource**|String|False||镜像来源，如果没有指定ids参数，此参数必传；取值范围：public、shared、thirdparty、private|
|**pageNumber**|Integer|False|1|页码；默认为1|
|**pageSize**|Integer|False|20|分页大小；默认为20；取值范围[10, 100]|
|**platform**|String|False||操作系统平台，取值范围：Windows Server、CentOS、Ubuntu|
|**rootDeviceType**|String|False||镜像支持的系统盘类型，[localDisk,cloudDisk]|
|**status**|String|False||<a href="https://www.jdcloud.com/help/detail/3871/isCatalog/1">参考镜像状态</a>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**images**|[Image[]](##Image)|镜像详情|
|**totalCount**|Integer|总数量|
### <a name="Image">Image</a>
|名称|类型|描述|
|---|---|---|
|**architecture**|String|镜像架构 i386, x86_64|
|**createTime**|String|创建时间|
|**dataDisks**|[InstanceDiskAttachment[]](##InstanceDiskAttachment)|打包镜像数据盘映射信息|
|**desc**|String|镜像描述|
|**imageId**|String|镜像ID|
|**imageSource**|String|镜像来源 jcloud：官方镜像 marketplace：镜像市场镜像 self：用户自己的镜像 shared：其他用户分享的镜像|
|**name**|String|镜像名称|
|**osType**|String|镜像的操作系统类型，[windows, linux]|
|**osVersion**|String|操作系统版本号|
|**platform**|String|操作系统发行版，[suse, debian, ubuntu, centos, windows-server]|
|**progress**|String|镜像复制时的进度，单位为百分比，例如：80|
|**rootDeviceType**|String|镜像支持的系统盘类型。localDisk：支持本地盘系统盘。cloudDisk：支持云盘系统盘|
|**sizeMB**|Integer|镜像本身大小|
|**snapshotId**|String|云硬盘做系统盘的快照id，创建云主机时，默认使用此快照创建系统盘|
|**status**|String|<a href="https://www.jdcloud.com/help/detail/3871/isCatalog/1">参考镜像状态</a>|
|**systemDisk**|[InstanceDiskAttachment](##InstanceDiskAttachment)|系统盘配置|
|**systemDiskSizeGB**|Integer|镜像系统盘大小|
### <a name="InstanceDiskAttachment">InstanceDiskAttachment</a>
|名称|类型|描述|
|---|---|---|
|**autoDelete**|Boolean|随云主机一起删除，删除主机时自动删除此磁盘，默认为true，本地盘(local)不能更改此值。<br>如果云主机中的数据盘(cloud)是包年包月计费方式，此参数不生效。<br>如果云主机中的数据盘(cloud)是共享型数据盘，此参数不生效。<br>|
|**cloudDisk**|[Disk](##Disk)|云硬盘配置|
|**deviceName**|String|数据盘逻辑挂载点，取值范围：vda,vdb,vdc,vdd,vde,vdf,vdg,vdh,vdi|
|**diskCategory**|String|磁盘分类，取值为本地盘(local)或者数据盘(cloud)。<br>系统盘支持本地盘(local)或者云硬盘(cloud)。系统盘选择local类型，必须使用localDisk类型的镜像；同理系统盘选择cloud类型，必须使用cloudDisk类型的镜像。<br>数据盘仅支持云硬盘(cloud)。<br>|
|**localDisk**|[LocalDisk](##LocalDisk)|本地磁盘配置|
### <a name="Disk">Disk</a>
|名称|类型|描述|
|---|---|---|
|**attachments**|[DiskAttachment[]](##DiskAttachment)|挂载信息|
|**az**|String|云硬盘所属AZ|
|**charge**|[Charge](##Charge)|云硬盘计费配置信息|
|**createTime**|String|创建云硬盘时间|
|**description**|String|云硬盘描述，允许输入UTF-8编码下的全部字符，不超过256字符。|
|**diskId**|String|云硬盘ID|
|**diskSizeGB**|Integer|磁盘大小，单位为 GiB|
|**diskType**|String|磁盘类型，取值为 ssd 或 premium-hdd|
|**multiAttachable**|Boolean|云盘是否支持多挂载|
|**name**|String|云硬盘名称，只允许输入中文、数字、大小写字母、英文下划线“_”及中划线“-”，不允许为空且不超过32字符。|
|**snapshotId**|String|创建该云硬盘的快照ID|
|**status**|String|云硬盘状态，取值为 creating、available、in-use、extending、restoring、deleting、deleted、error_create、error_delete、error_restore、error_extend 之一|
|**tags**|[Tag[]](##Tag)|Tag信息|
### <a name="DiskAttachment">DiskAttachment</a>
|名称|类型|描述|
|---|---|---|
|**attachTime**|String|挂载时间|
|**attachmentId**|String|挂载ID|
|**diskId**|String|云硬盘ID|
|**instanceId**|String|挂载实例的ID|
|**instanceType**|String|挂载实例的类型，取值为 vm、nc|
|**status**|String|挂载状态，取值为 "attaching", "attached", "detaching", "detached"|
### <a name="Charge">Charge</a>
|名称|类型|描述|
|---|---|---|
|**chargeExpiredTime**|String|过期时间，预付费资源的到期时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ，后付费资源此字段内容为空|
|**chargeMode**|String|支付模式，取值为：prepaid_by_duration，postpaid_by_usage或postpaid_by_duration，prepaid_by_duration表示预付费，postpaid_by_usage表示按用量后付费，postpaid_by_duration表示按配置后付费，默认为postpaid_by_duration|
|**chargeRetireTime**|String|预期释放时间，资源的预期释放时间，预付费/后付费资源均有此值，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStartTime**|String|计费开始时间，遵循ISO8601标准，使用UTC时间，格式为：YYYY-MM-DDTHH:mm:ssZ|
|**chargeStatus**|String|费用支付状态，取值为：normal、overdue、arrear，normal表示正常，overdue表示已到期，arrear表示欠费|
### <a name="Tag">Tag</a>
|名称|类型|描述|
|---|---|---|
|**key**|String|Tag键|
|**value**|String|Tag值|
### <a name="LocalDisk">LocalDisk</a>
|名称|类型|描述|
|---|---|---|
|**diskSizeGB**|Integer|磁盘大小|
|**diskType**|String|磁盘类型，取值范围{premium-hdd, ssd}|

## 返回码
|返回码|描述|
|---|---|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**503**|Service unavailable|
|**200**|OK|
|**500**|Internal server error|
