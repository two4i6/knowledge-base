# products

|表头|参数名称|类型|必填|默认|描述|CHECK|
|-|-|-|-|-|-|-|
|id|编号|uuid||auto|商品编号|
|created_at|创建时间|timestamptz||now()|词条创建时间戳
|updated_at|更新时间|timestamptz|x|now()|词条更新时间戳
|deleted_at|删除时间|timestamptz|||删除记录时间戳
|name|名称|text|x||商品名称|
|catalog|分类|text|x||商品分类|
|business_id|企业id|uuid|||企业唯一id
|metadata|其他信息||x||不需要检索的信息|


## metadata
``` json
{
    "unit": 0,
    "decimal": 0,
    "price": 0,
    "brand": null,
    "description": null,
    "tag": null
}
```
### units
``` json
{
    "0": "pcs",
    "1": "sets",
    "2": "packages",
    "3": "l",
    "4": "ml",
    "5": "kg" 
}
```