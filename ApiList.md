API概览
=======

### 订单相关接口

|API|描述|
| ------------- | ------------- |
|[ListOrder](Order/listorder.md)|查询检索订单列表|
|[GetOrder](Order/getorder.md)|查看订单详情|
|[AddOrder](Order/createorder.md)|提交生成订单|
|[ModifyOrder](Order/modifyorder.md)|修改订单状态/开通后填入关联产品ID等|
|[DeleteOrder](Order/deleteorder.md)|删除订单//TODO用户控制台没有删除功能|
|[BatchCancelOrder](Order/batchcancelorder.md)|批量取消订单（与单个订单取消限制条件不一样，用于72小时内退款，暂时用不到|

### 订单取消规则设置相关接口

|API|描述|
| ------------- | ------------- |
|[CreateRule](Rule/createrule.md)|创建订单取消规则|
|[ModifyRule](Rule/modifyrule.md)|修改订单取消规则|
|[ListRule](Rule/listrule.md)|查看订单取消规则列表|
|[GetRule](Rule/getrule.md)|查看订单取消规则详情|

