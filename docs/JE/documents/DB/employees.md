# employees
|表头|参数名称|类型|必填|默认|描述|CHECK|
|-|-|-|-|-|-|-|
|id|编号|uuid||auto|员工编号|
|created_at|创建时间|timestamptz||now()|词条创建时间戳
|updated_at|更新时间|timestamptz|x|now()|词条更新时间戳
|deleted_at|删除时间|timestamptz|||删除记录时间戳
|name|名称|text|x||商店名称
|app_permissions|apps访问权限|int8[]|x|[]|可以访问的app编号|
|user_id|用户id|uuid|x||用户唯一id
|business_id|企业id|uuid|||企业唯一id
|metadata|其他信息||x||不需要检索的信息|


## metadata
``` json
{
    "position": null,
    "department": null, 
    "contact": {
        "avatar": null,
        "phone": null,
        "email": null,
        "address": null,
        "city": null,
        "state": null,
        "country": null,
        "birthday": null
    }
}
```

## access policies
```
// 员工只登陆用户可以访问
SELECT -> authenticated -> (user_id = auth.uid())
```