# 预授权流水记录查询

## 接口名
{api_domain}/api/v1/pre-auth/query-trans
## 请求类型
application/json
## 访问方式
POST
### 请求参数


| 参数 | 参数名称 | 类型 | 必填 | 描述 | 范例 |
| --- | --- | --- | --- | --- | --- |
| terminal\_sn | 收钱吧终端ID | String\(32\) | 特殊可选 | 收钱吧终端ID，不超过32位的纯数字 | "00101010029201012912" |
| auth\_sn | 收钱吧预授权唯一订单号 | String\(16\) | 特殊可选 | 收钱吧系统内部唯一预授权订单号 | "7894259245320979"|
| client\_auth\_sn | 商户系统预授权订单号 | String\(32\) | 特殊可选 | 必须在商户系统内唯一；且长度不超过32字节 | "1077735255938023" |
**auth\_sn与client\_auth\_sn不能同时为空，优先按照auth\_sn查找订单，如果没有，再按照client\_auth\_sn查询**


### 返回参数说明

| 参数 | 参数名称 | 类型 | 必填 | 描述 | 范例 |
| --- | --- | --- | --- | --- | --- |
| terminal\_sn | 终端号 | String\(32\) | Y | 收钱吧终端ID | "01939202039923029" |
| auth\_sn | 收钱吧预授权唯一订单号 | String\(16\) | Y | 收钱吧系统内部唯一预授权订单号 | "7894259245320979"|
| subject | 预授权订单标题 | String\(32\) | Y | 订单标题 | "千里香馄饨订单" |
| payway | 支付方式 | String\(2\) | Y | 一级支付方式，取值见附录《支付方式列表》 | "1" |
| payer\_user\_id | 付款方ID | String\(64\) | Y | 支付平台对应唯一用户ID | "2088402019148643" |
| payer\_logon\_id | 付款方账号 | String\(128\) | Y | 支付平台对应付款方账号 | "134**3920" |
| trans | 预授权资金操作流水记录 | Array | Y | 预授权资金操作流水记录数组 | [] |
| request\_no | 收钱吧操作流水号 | String\(20\) | Y | 收钱吧本次操作流水号 | "15154048770704543281" |
| client\_trans\_no | 商户系统操作请求流水号 | String\(36\) | Y | 必须在商户系统内唯一；且长度不超过36字节 | "201802091001001" |
| request\_type | 资金操作流类型 | String\(20\) | Y | 目前支持： FREEZE:冻结  UNFREEZE:解冻  PAY:支付 REFUND:退款 | "FREEZE" |
| amount | 该笔操作流水对应的金额 | String\(10\) | Y | 操作流水request\_no对应的金额 | "100" |
| status | 操作流水状态 | String\(32\) | Y | 当前流水操作状态 | "SUCCESS" |
| request\_create\_time | 查询request\_no操作流水创建时间 | String\(13\) | Y | 时间戳 | "1449646835244" |
| request\_finish\_time | 查询request\_no操作流水完成时间 | String\(13\) | Y | 时间戳 | "1449646835244" |
| operator | 执行上次业务操作的操作员 | String\(32\) | Y | 操作员 | Obama |



