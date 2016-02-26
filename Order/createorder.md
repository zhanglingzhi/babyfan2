#### AddOrder

创建订单，自动生成子订单。

#### 请求语法

```
POST /Order HTTP/1.1
Accept: application/json
Date: UTC Date
OperatorId:123

{
  "OrderType":12,
  "ProductId":20,
  "ProductCategoryId":2,
  "UserId":50,
  "OpUser":100,
  "CreateTime":1456392166,
  "EffectTime":1456392166,
  "EndTime":1456397166,
  "BuyYear":2,
  "Months":0,
  "YearType":2,
  "Fee":"23.56",
  "Price":"25.21",
  "TotalPrice":"50.42",
  "AllPrice":"48.32",
  "RelatedId":0,
  "OtherRelatedId":0,
  "RoomId":5,
  "PoolId":4,
  "IsTest":0,
  "OrderInfo":"{}",
  "PayType":1
  "PayState":1
}
```

#### 请求元素(Request Elements)

|**名称**|**类型**|	**描述**|**是否可选**|
| ------------- |:-------------:|:-------------| ------------- |
|OrderType|Integer|订单类型 *见表订单类型(OrderType)*|必选|
|ProductId|Integer|产品ID|必选|
|ProductCategoryId|Integer|产品类型，对应产品服务的一级产品/产品分类如CEC、RDS、SDN、SPARK、CDN等产品线|必选|
|UserId|Integer|所属用户|必选|
|OpUser|Integer|操作用户|必选|
|CreateTime|Integer|下单时间|必选|
|EffectTime|Integer|操作人的UserId|必选|
|EndTime|Integer|生效时间|必选|
|BuyYear|Integer|购买年限|必选|
|Months|Integer|月份数,用于生成子订单数|必选|
|YearType|Integer|年限类型:1-年;2-月;3-天;5-半年;|必选|
|Fee|Float|费用（按量，元/小时）|必选|
|Price|Float|单价（包年包月）|必选|
|TotalPrice|Float|总价|必选|
|AllPrice|Float|优惠后价格|必选|
|RelatedId|Integer|关联ID 若开通云服务器 则关联ID为云服务器的vm_id|必选|
|OtherRelatedId|String|附属ID记录购买附属产品时附属产品的关联号|必选|
|CouponInfo|String|优惠信息|可选|
|RoomId|Integer|机房ID|必选|
|PoolId|Integer|集群ID|可选|
|IsTest|Integer|是否试用 0:正式；1:试用|必选|
|OrderInfo|String|订单信息|必选|
|PayType|Integer|订单支付类型 *见表订单支付类型(PayType)*|必选|
|PayState|Integer|支付状态 *见表订单支付状态(PayState)*|必选|



#### 响应元素(Response Elements)
|**名称**|**描述**|
| ------------- |:-------------:|
|OrderID|订单号 |
|OrderType|订单类型 *见表订单类型(OrderType)*|
|ProductId|产品ID|
|ProductCategoryId|产品类型|
|UserId|所属用户|
|OpUser|操作用户|
|CreateTime|下单时间|
|EffectTime|操作人的UserId|
|EndTime|生效时间|
|BuyYear|购买年限|
|Months|月份数,用于生成子订单数|
|YearType|年限类型:1-年;2-月;3-天;5-半年;|
|Fee|费用（按量，元/小时）|
|Price|单价（包年包月）|
|TotalPrice|总价|
|AllPrice|优惠后价格|
|RelatedId|关联ID 若开通云服务器 则关联ID为云服务器的vm_id|
|OtherRelatedId|附属ID记录购买附属产品时附属产品的关联号|
|CouponInfo|优惠信息|
|RoomId|机房ID|
|PoolId|集群ID|
|IsTest|是否试用 0:正式；1:试用|
|OrderInfo|订单信息|
|PayType|订单支付类型 *见表订单支付类型(PayType)*|
|PayState|支付状态 *见表订单支付状态(PayState)*|



 
#### 错误码
|**错误码(ErrorCode)**|**描述(ErrorMessage)**|**Http状态码**|**语义**|
| ------------- |-------------| -------------| ------------- |
|MissingParam|The parameter "${param}" that is mandatory for processing this request is not supplied.. |404 |缺少参数|
|SessionTimedout|The creator ${creatorId} is not logged in or session is timeout. |403 |会话超时|
|AccessDenied|The creator ${creatorId} is not permitted for AddOrder. |403 |无权访问|


#####订单类型(OrderType)
|id|名称| |id|名称|
| --- |--|--| --- |--|
|1|产品购买||2|产品续费|
|3|产品升级||4|正式开通|
|5|延迟测试||6|被封IP续费|
|7|被封IP更换||8|产品试用|
|9|订单取消||10|赔偿或赠送|
|11|产品录入||12|弹性运能升级|
|13|日付购买||14|弹性运能转主运能|
|15|克隆虚拟机| | | | |

##### 订单状态(State)
|id|名称| |id|名称|
| --- |--|--| --- |--|
|1|处理完成| |2|尚未处理|
|3|正在处理| |4|处理失败|


##### 订单取消状态(IsCancel)
|id|名称| |id|名称|
| --- |--|--| --- |--|
|0|未取消| |1|已取消|
|2|申请取消| |3|已驳回|


##### 订单支付类型(PayType)
|id|名称| |id|名称|
| --- |--|--| --- |--|
 |1|已取消| |2|按量付|
 
 
##### 订单支付状态(PayState)
|id|名称| |id|名称|
| --- |--|--| --- |--|
|1|待下单| |2|待结算|
|3|待支付| |4|已支付|
|5|支付失败| |6|待生效|



#### 请求示例

##### Request
```
POST /Order HTTP/1.1
Date: Fri, 24 Dec 2015 03:15:40 GMT

{
  "OrderType":12,
  "ProductId":20,
  "ProductCategoryId":2,
  "UserId":50,
  "OpUser":100,
  "CreateTime":1456392166,
  "EffectTime":1456392166,
  "EndTime":1456397166,
  "BuyYear":2,
  "Months":0,
  "YearType":2,
  "Fee":"23.56",
  "Price":"25.21",
  "TotalPrice":"50.42",
  "AllPrice":"48.32",
  "RelatedId":0,
  "OtherRelatedId":0,
  "CouponInfo":"{}",
  "RoomId":5,
  "PoolId":4,
  "IsTest":0,
  "OrderInfo":"{}",
  "PayType":1
  "PayState":1
}
```

##### Response

```json
{
 
  "OrderId":123,
  "OrderType":12,
  "ProductId":20,
  "ProductCategoryId":2,
  "UserId":50,
  "OpUser":100,
  "CreateTime":1456392166,
  "EffectTime":1456392166,
  "EndTime":1456397166,
  "BuyYear":2,
  "Months":0,
  "YearType":2,
  "Fee":"23.56",
  "Price":"25.21",
  "TotalPrice":"50.42",
  "AllPrice":"48.32",
  "RelatedId":0,
  "OtherRelatedId":0,
  "CouponInfo":"{}",
  "RoomId":5,
  "PoolId":4,
  "IsTest":0,
  "OrderInfo":"{}",
  "PayType":1
  "PayState":1
  }
```

