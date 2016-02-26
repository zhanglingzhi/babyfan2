#### ListOrder

可根据条件查询订单记录，查询条件见参数，若不指定任何条件，则查询所有订单记录。  
查询结果以创建时间降序排序。查询可分页。不指定分页参数则不分页。
包年包月和按量只会在参数上进行区分

#### 请求语法

```
GET /Order HTTP/1.1
或
GET /Order?OrderID={$OrderID}&UserID={$UserID} HTTP/1.1
Content-Type: application/json
Date: UTC Date
OperatorId:123


```

#### 请求元素(Request Elements)

|名称|类型|	描述|是否可选|
| ------------- |:-------------:| -------------| ------------- |
|IsUsage|integer|是否按量订单，1：是，0或空值：否；不传该字段则不对该字段做筛选 |可选|
|IsCancel|integer|取消状态 0：未取消 1：已取消 2：申请取消；默认0 未取消（正常状态) ；不传该字段则不对该字段做筛选|可选|
|OrderId|String|订单ID|可选|
|UserId|Integer|订单所属用户ID|可选|
|TrackerUser|String|跟踪销售|可选|
|CreateTime|String|下单时间|可选|
|RoomId|Integer|机房|可选|
|ProductId|Integer|产品型号|可选|
|ProductCategoryId|String|产品类型，对应产品服务的一级产品/产品分类如CEC、RDS、SDN、SPARK、CDN等产品线|可选|
|State|String|订单状态|可选|
|OrderType|String|订单类型|可选|
|OpUser|String|下单用户|可选|
|PageNo|Integer|第几页，分页参数，首页从1开始，若不传分页参数，则全部取出|可选|
|PageSize|Integer|每页几条记录，分页参数，若不传分页参数，则全部取出|可选|



##### 订单状态(State)
|id|名称| |id|名称|
| --- |--|--| --- |--|
|1|处理完成| |2|尚未处理|
|3|正在处理| |4|处理失败|
|5|申请取消| | | | |


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


#### 响应元素(Response Elements)
|名称|  描述|
| ------------- | -------------|
|OrderId|订单ID|
|OrderType|订单类型|
|ProductId|产品ID|
|ProductType|产品类型|
|UserId|所属用户|
|OpUser|操作用户|
|PayUser|付款用户|
|TrackerUser|跟踪销售|
|CreateTime|下单时间|
|PayTime|付款时间|
|EffectTime|生效时间|
|EndTime|到期时间|
|BuyYear|购买年限|
|Months|月份数,用于生成子订单数|
|YearType|年限类型:1-年;2-月;3-天;5-半年;|
|Fee|费用（按量，元/小时）|
|Price|单价（包年包月）|
|TotalPrice|总价|
|RelatedId|关联ID 若开通云服务器 则关联ID为云服务器的vm_id|
|OtherRelatedId|附属ID记录购买附属产品时附属产品的关联号|
|State|订单状态1:处理完成2 :尚未处理3:正在处理4:处理失败5:申请取消|
|IsPay|结算状态 1已结算 2未结算 3已返款|
|IsCancel|是否已取消 0:未取消；1:已取消|
|CouponInfo|优惠信息|
|RoomId|机房ID|
|IsDel|云主机是否已删除 0:未删除；1:已删除|
|PayType|支付类型:1-预付;2-后付;3-按量付|
|PayState|支付状态:1-待下单;2-待结算;3-待支付;4-已支付;5-支付失败;-6待生效|

#### 请求示例

##### Request
```
GET /Order?UserID=1 HTTP/1.1
Date: 2016-01-01T12:00:00 +0800
OperatorId:1

```
##### Response

```
	json
	{
	    "RequestId": "15AfIrB84GDewQk1ymwD",
        "TotalCount":2
        "Data":[
            {
                "OrderId":"1",
                "OrderType":1,
                "ProductId":2,
                "ProductType":3,
                "UserId":1,
                "OpUser":0,
                "PayUser":0,
                "TrackerUser":0,
                "CreateTime":0,
                "PayTime":0,
                "EffectTime":0,
                "EndTime":0,
                "BuyYear":0,
                "Months":0,
                "YearType":0,
                "Fee":"0.00000",
                "Price":"0.00",
                "TotalPrice":"0.00",
                "RelatedId":0,
                "OtherRelatedId":"",
                "State":0,
                "IsPay":0,
                "IsCancel":0,
                "CouponInfo":"",
                "RoomId":0,
                "IsDel":0,
                "PayType":0,
                "PayState":0
            },
            {
                "OrderId":"2",
                "OrderType":1,
                "ProductId":2,
                "ProductType":3,
                "UserId":1,
                 "OpUser":0,
                "PayUser":0,
                "TrackerUser":0,
                "CreateTime":0,
                "PayTime":0,
                "EffectTime":0,
                "EndTime":0,
                "BuyYear":0,
                "Months":0,
                "YearType":0,
                "Fee":"0.00000",
                "Price":"0.00",
                "TotalPrice":"0.00",
                "RelatedId":0,
                "OtherRelatedId":"",
                "State":0,
                "IsPay":0,
                "IsCancel":0,
                "CouponInfo":"",
                "RoomId":0,
                "IsDel":0,
                "PayType":0,
                "PayState":0
            }
         ]
	
	}
```

