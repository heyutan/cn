# createInstance


## 描述
创建实例

## 请求方式
POST

## 请求地址
https://ipanti.jdcloud-api.com/v1/regions/{regionId}/instances

|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**regionId**|String|True||所属地域ID|

## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**instanceSpec**|[InstanceSpec](##InstanceSpec)|True||实例规格参数|

### <a name="InstanceSpec">InstanceSpec</a>
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**bp**|Integer|False||保底带宽：单位Gbps|
|**buyType**|Integer|False||购买类型，1->新购 3->升级|
|**bw**|Integer|False||业务带宽：单位Mbps|
|**carrier**|String|False||线路：TELECOM->电信线路 UNICOM->联通线路 CMCC->移动线路|
|**ep**|Integer|False||弹性带宽：单位Gbps|
|**name**|String|False||实例名称|
|**returnUrl**|String|False||支付成功后跳转的页面，控制台交互模式传该字段|
|**timeSpan**|Integer|False||购买时长跨度|
|**timeUnit**|Integer|False||购买时长单位，3->月 4->年|

## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String||
|**result**|[Result](##Result)||


### <a name="Result">Result</a>
|名称|类型|描述|
|---|---|---|
|**orderId**|String||

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
