# transactions

|表头|参数名称|类型|必填|默认|描述|CHECK|
|-|-|-|-|-|-|-|
|id|编号|uuid||auto|交易编号|
|created_at|创建时间|timestamptz||now()|词条创建时间戳
|updated_at|更新时间|timestamptz|x|now()|词条更新时间戳
|deleted_at|删除时间|timestamptz|||删除记录时间戳
|amount|金额|numeric|x||订单金额(包含优惠)|
|method|支付方式|int4|x|0: cash <br> 1: bank_card <br> 2: shou_qian_ba
|discounts|折扣|jsonb[]||{}|折扣详情
|third_party_transaction_id|第三方交易回执码|text||
|metadata|其他信息||x||不需要检索的信息|


## metadata
``` json
{
    "note": null
}
```