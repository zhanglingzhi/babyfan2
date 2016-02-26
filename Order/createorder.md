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
  "ProductType":2,
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
|OrderType|Integer|订单类型 |必选|
|ProductId|Integer|产品ID|必选|
|ProductType|Integer|产品类型|必选|
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
|PayType|Integer|支付类型:1-预付;2-后付;3-按量付|必选|
|PayState|Integer|支付状态:1-待下单;2-待结算;3-待支付;4-已支付;5-支付失败;-6待生效|必选|



#### 响应元素(Response Elements)
|**名称**|**描述**|
| ------------- |:-------------:|
|OrderID|订单号 |
|OrderType|订单类型 |
|ProductId|产品ID|
|ProductType|产品类型|
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
|PayType|支付类型:1-预付;2-后付;3-按量付|
|PayState|支付状态:1-待下单;2-待结算;3-待支付;4-已支付;5-支付失败;-6待生效|


#### 错误码
|**错误码(ErrorCode)**|**描述(ErrorMessage)**|**Http状态码**|**语义**|
| ------------- |-------------| -------------| ------------- |
|MissingParam|The parameter "${param}" that is mandatory for processing this request is not supplied.. |404 |缺少参数|
|SessionTimedout|The creator ${creatorId} is not logged in or session is timeout. |403 |会话超时|
|AccessDenied|The creator ${creatorId} is not permitted for AddOrder. |403 |无权访问|



#### 请求示例

##### Request
```
POST /AddOrder HTTP/1.1
Date: Fri, 24 Dec 2015 03:15:40 GMT

{
  "OrderType":12,
  "ProductId":20,
  "ProductType":2,
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
  "ProductType":2,
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

