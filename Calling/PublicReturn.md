#### 返回结果

调用 API 服务后返回数据采用统一的JSON格式，返回的 HTTP 状态码如下：  

-  2xx 代表调用成功；
-  4xx 代表客户端请求失败，如参数错误，URL不正确等；
-  5xx 代表服务端失败。

*<font size=5>公共返回</font>*

用户发送的每次接口调用请求，无论成功与否，系统都会返回一个唯一识别码 RequestId 给用户。

|名称|类型|	描述|
| ------------- |:-------------:|:-------------|
|RequestId|String|请求的唯一识别码|

*<font size=5>成功结果</font>*

```
    JSON示例：

    {
        "RequestId": "4C467B38-3910-447D-87BC-AC049166F216",
        /* 返回结果数据 */
    }
```

*<font size=5>失败结果</font>*

调用接口出错后，将不会返回结果数据。调用方可根据每个接口对应的错误码以及下述的公共错误码来定位错误原因。 当调用出错时，HTTP 请求返回一个 4xx 或 5xx 的 HTTP 状态码。返回的消息体中是具体的错误代码及错误信息。

```
 返回JSON示例
	{
	    "RequestId": "4C467B38-3910-447D-87BC-AC049166F216",
	    "ErrorCode": "MissingParam",
        "ErrorMessage":"The input parameter 'UserId' that is mandatory for processing this request is not supplied"
	}

```

*<font size=5>公共错误码</font>*

|错误码(ErrorCode)|描述(ErrorMessage)|Http状态码|语义|
| ------------- | ------------- |:-------------| ------------- |
|MissingParam|The parameter "${Param}" that is mandatory for processing this request is not supplied.|400|缺少必要的参数|
|InvalidParam|The parameter "${Param}" is invalid: ${Detail info}.|400|无效的参数，参数格式不正确或数值不正确|
|SessionTimedout|The operator[OperatorId = ${OperatorId}] is not logged in or session is timeout.|403|操作人员未登录或者登录超时|
|AccessDenied|The operator[OperatorId = ${OperatorId}] is not permitted for ${Operation}|403|操作人员无此操作的权限|


