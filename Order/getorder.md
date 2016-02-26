#### GetOrder

获取具体订单。

#### 请求语法

```
GET /Order/{$OrderId} HTTP/1.1
Content-Type: application/json
Date: UTC Date
OperatorId:-1

```

#### 请求元素(Request Elements)

|名称|类型|	描述|是否可选|
| ------------- |:-------------:| -------------| ------------- |
|OrderId|String|订单号|必选|

#### 响应元素(Response Elements)
|名称|  描述|
| ------------- | -------------|
|OrderId|订单号|
|OrderType|订单类型*见表订单类型(OrderType)*|
|ProductId|产品ID|
|ProductCategoryId|产品类型，对应产品服务的一级产品/产品分类如CEC、RDS、SDN、SPARK、CDN等产品线|
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
|State|订单状态*见表订单状态(State)*|
|IsCancel|订单取消状态*见表订单取消状态(IsCancel)*|
|CouponInfo|优惠信息|
|RoomId|机房ID|
|IsDel|云主机是否已删除 0:未删除；1:已删除|
|PayType|支付类型*见表订单支付类型(PayType)*|
|PayState|支付状态 *见表订单支付状态(PayState)*|
|ChildOrder|子订单|
|&nbsp;&nbsp;&nbsp;&nbsp;OrderId|子订单订单号|
|&nbsp;&nbsp;&nbsp;&nbsp;NoBillMoney|子订单未开票金额|
|&nbsp;&nbsp;&nbsp;&nbsp;BillMoney|子订单已开票金额|
|&nbsp;&nbsp;&nbsp;&nbsp;Virtual_money|子订单优惠入款金额|
|&nbsp;&nbsp;&nbsp;&nbsp;Money|子订单 总计,实际收入|
|&nbsp;&nbsp;&nbsp;&nbsp;ExpectMoney|子订单 预计收入|
|&nbsp;&nbsp;&nbsp;&nbsp;OrderType|子订单类型 见订单类型(OrderType)|
|&nbsp;&nbsp;&nbsp;&nbsp;State|子订单状态 0正常 1已作废|
|&nbsp;&nbsp;&nbsp;&nbsp;UserID|所属用户|
|&nbsp;&nbsp;&nbsp;&nbsp;BeginTime|创建时间|
|&nbsp;&nbsp;&nbsp;&nbsp;EndTime|到期时间|


#### 错误码
|错误码(ErrorCode)|描述(ErrorMessage)|Http状态码|语义|
| ------------- |-------------| -------------| ------------- |
|OrderIdNotExsit|OrderId{$OrderId} is not exsit. |404 |找不到OrderId对应的记录|



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
:1-;2-待结算;3-待支付;4-已支付;5-支付失败;-6待生效

#### 请求示例

##### Request
```
GET /Order/1 HTTP/1.1
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
                "CreateTime":1456419600,
                "PayTime":0,
                "EffectTime":1456419600,
                "EndTime":1461600000,
                "BuyYear":1,
                "Months":2,
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
                "PayState":0,
                'ChildOrder':[
                    {
                        "OrderId":"1111",
                        "NoBillMoney":"6.00",
                        "BillMoney":"6.00",
                        "Virtual_money":"6.00",
                        "Money":"6.00",
                        "ExpectMoney":"10.00",
                        "OrderType":1,
                        "State":0,
                        "UserID":1,
                        "BeginTime":1456419600,
                        "EndTime":"1456786799,
                    },
                     {
                        "OrderId":"1111",
                        "NoBillMoney":"31.00",
                        "BillMoney":"31.00",
                        "Virtual_money":"0.00",
                        "Money":"0.00",
                        "ExpectMoney":"10.00",
                        "OrderType":1,
                        "State":0,
                        "UserID":1,
                        "BeginTime":1456786801,
                        "EndTime":1459461599,
                    },
                     {
                        "OrderId":"1111",
                        "NoBillMoney":"31.00",
                        "BillMoney":"31.00",
                        "Virtual_money":"6.00",
                        "Money":"6.00",
                        "ExpectMoney":"10.00",
                        "OrderType":1,
                        "State":0,
                        "UserID":1,
                        "BeginTime":1459461601,
                        "EndTime":1461600000,
                    }
                ]
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
                "PayState":0,
                'ChildOrder':[]
            }
         ]
	
	}
```

