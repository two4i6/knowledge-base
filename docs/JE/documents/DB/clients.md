# clients

|表头|参数名称|类型|必填|默认|描述|CHECK|
|-|-|-|-|-|-|-|
|id|编号|uuid||auto|程序编号|
|created_at|创建时间|timestamptz||now()|词条创建时间戳
|updated_at|更新时间|timestamptz|x|now()|词条更新时间戳
|type|客户种类|int4|x|0|0: 一般客户<br>1: 企业客户 <br>2: 供货商
|client_group_id||uuid|x||
|user_id|用户id|uuid|x||用户的唯一id
|family_id|家庭id|uuid|||
|metadata|其他信息||x|{}|不需要检索的信息|!=null|

## 家庭

# client_groups

|表头|参数名称|类型|必填|默认|描述|CHECK|
|-|-|-|-|-|-|-|
|id|编号|uuid||auto|程序编号|
|created_at|创建时间|timestamptz||now()|词条创建时间戳
|updated_at|更新时间|timestamptz|x|now()|词条更新时间戳
|metadata|其他信息||x|{}|不需要检索的信息|!=null|
