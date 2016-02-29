#### ModifyOrder

* **修改订单价格，对订单进行优惠处理**
* **修改订单状态(如处理中、处理完成、订单设置失败、申请取消)**
* **订单中关联产品ID（用于开通产品成功时）**
* **支付状态（支付完成，支付失败）**
* **订单分解（支付完成时进行）**

 ***备注：订单取消合并进入该接口***


#### 请求语法

```
PUT /V1.0/Order/{$OrderID} HTTP/1.1
Date: GMT Date

{
  "State":Order State,
  "PayState":Order Pay State,
  "RelatedId":Order Relate User Buy Instance Id
}
```

#### 请求元素(Request Elements)

|**名称**|**类型**|	**描述**|**是否可选**|
| ------------- |:-------------:|:-------------| ------------- |
|OrderId|String|订单号|必选|
|TotalPrice|Float|总价|可选|
|State|Integer|订单状态 *见表订单状态(State)*|可选|
|RelatedId|Integer|关联ID 若开通云服务器 则关联ID为云服务器的vm_id|可选|
|PayState|Integer|支付状态 *见表订单支付状态(PayState)*|可选|
|IsCancel|Integer|订单取消状态 *见表订单取消状态(IsCancel)*|可选|
|CancelRejectReason|String|订单取消备注|可选|



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
|EffectTime|生效时间|
|EndTime|到期时间|
|BuyYear|购买年限|
|Months|月份数,用于生成子订单数|
|YearType|年限类型:1-年;2-月;3-天;5-半年;|
|Fee|费用（按量，元/小时）|
|Price|单价（包年包月）|
|TotalPrice|总价|
|AllPrice|优惠后价格|
|RelatedId|关联ID 若开通云服务器 则关联ID为云服务器的vm_id|
|CouponInfo|优惠信息|
|RoomId|机房ID|
|PoolId|集群ID|
|IsTest|是否试用 0:正式；1:试用|
|OrderInfo|订单信息|
|PayType|订单支付类型 *见表订单支付类型(PayType)*|
|PayState|支付状态 *见表订单支付状态(PayState)*|
|CancelRejectReason|订单取消备注|


#### 错误码
|**错误码(ErrorCode)**|**描述(ErrorMessage)**|**Http状态码**|**语义**|
| ------------- |-------------| -------------| ------------- |
|MissingParam|The parameter "${param}" that is mandatory for processing this request is not supplied.. |404 |缺少参数|
|OrderNotFount|The OrderId ${OrderId} not found. |400 |订单不存在|
|SessionTimedout|The creator ${creatorId} is not logged in or session is timeout. |403 |会话超时|
|AccessDenied|The creator ${creatorId} is not permitted for AddOrder. |403 |无权访问|




#####订单类型(OrderType)

|id|名称||id|名称|
|-------------|-------------|-------------|-------------|-------------|
|1|产品购买| |2|产品续费|
|3|产品升级| |4|正式开通|
|5|延迟测试| |6|被封IP续费|
|7|被封IP更换| |8|产品试用|
|9|订单取消| |10|赔偿或赠送|
|11|产品录入| |12|弹性运能升级|
|13|日付购买| |14|弹性运能转主运能|
|15|克隆虚拟机| | | | |

##### 订单状态(State)

|id|名称| |id|名称|
|-------------|-------------|-------------|-------------|-------------|
|1|处理完成| |2|尚未处理|
|3|正在处理| |4|处理失败|


##### 订单取消状态(IsCancel)
|id|名称| |id|名称|
|-------------|-------------|-------------|-------------|-------------|
|0|未取消| |1|已取消|
|2|申请取消| |3|已驳回|


##### 订单支付类型(PayType)
|id|名称| |id|名称|
|-------------|-------------|-------------|-------------|-------------|
|1|包年包月| |2|按量付|
 
 
##### 订单支付状态(PayState)
|id|名称| |id|名称|
|-------------|-------------|-------------|-------------|-------------|
|1|待下单| |2|待结算|
|3|待支付| |4|已支付|
|5|支付失败| |6|待生效|

#### 请求示例

##### Request
```
PUT /V1.0/Order/123 HTTP/1.1
Date: Fri, 24 Dec 2015 03:15:40 GMT

{
  "State":1,
  "PayState":4,
  "RelatedId":50
}
```

##### Response

```
json
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
  "RelatedId":50,
  "CouponInfo":"{}",
  "ZoneId":5,
  "IsTest":0,
  "OrderInfo":"{}",
  "PayType":1
  "PayState":4,
  "CancelRejectReason":""
  }
```

