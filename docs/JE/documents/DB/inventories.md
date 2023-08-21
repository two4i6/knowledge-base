# inventories

|表头|参数名称|类型|必填|默认|描述|CHECK|
|-|-|-|-|-|-|-|
|id|编号|uuid||auto|商品编号|
|created_at|创建时间|timestamptz||now()|词条创建时间戳
|updated_at|更新时间|timestamptz|x|now()|词条更新时间戳
|deleted_at|删除时间|timestamptz|||删除记录时间戳
|product_id|产品编号|uuid|x||库存对应产品的编号|
|value|库存数量|number|x|0|库存数量|
|metadata|其他信息||x||不需要检索的信息|


## metadata
``` json
{
    "promotion_value": 0
}
```
