#### DeleteOrder

删除订单，暂不开放，用户控制台不允许删除订单。

#### 请求语法

```
DELETE /Order?OrderId={$OrderId} HTTP/1.1
Date: GMT Date
```

#### 请求元素(Request Elements)

|名称|类型|	描述|是否可选|
| ------------- |:-------------:|:-------------:|:-------------:|
| OrderId|Integer| 订单Id|必须参数|


#### 错误码
|**错误码(ErrorCode)**|**描述(ErrorMessage)**|**Http状态码**|**语义**|
| ------------- |-------------| -------------| ------------- |
|MissingParam|The parameter "${param}" that is mandatory for processing this request is not supplied.. |404 |缺少参数|
|OrderNotFount|The OrderId ${OrderId} not found. |400 |订单不存在|
|SessionTimedout|The creator ${creatorId} is not logged in or session is timeout. |403 |会话超时|
|AccessDenied|The creator ${creatorId} is not permitted for AddOrder. |403 |无权访问|

#### 请求示例

##### Request
```
DELETE /Order?OrderId=123&OperatorId=1 HTTP/1.1
Date: Fri, 24 Dec 2015 03:15:40 GMT
```

##### Response

```json
{
    "RequestId": "O7AfIrB84GFrwQk1ymwD"
}
```

