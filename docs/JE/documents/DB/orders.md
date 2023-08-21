# inventories

|表头|参数名称|类型|必填|默认|描述|CHECK|
|-|-|-|-|-|-|-|
|id|编号|uuid||auto|商品编号|
|created_at|创建时间|timestamptz||now()|词条创建时间戳
|updated_at|更新时间|timestamptz|x|now()|词条更新时间戳
|deleted_at|删除时间|timestamptz|||删除记录时间戳
|amount|金额|numeric|x||订单金额(使用优惠前)|
|type|订单种类|int8|x|0|0: sale <br> 1: purchase <br> 2: refund|
|details|订单详情|jsonb[]|x|[{product: product{}, quantity: 2},{product: product{}, quantity: 1}]|包含商品信息的订单详情
|metadata|其他信息||x||不需要检索的信息|


## metadata
``` json
{
    "note": null
}
```
