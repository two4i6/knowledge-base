# businesses
|表头|参数名称|类型|必填|默认|描述|CHECK|
|-|-|-|-|-|-|-|
|id|编号|int8||auto|程序编号|
|created_at|创建时间|timestamptz||now()|词条创建时间戳
|updated_at|更新时间|timestamptz|x|now()|词条更新时间戳
|deleted_at|删除时间|timestamptz|||删除记录时间戳
|name|名称|text|x||商店名称
|app_permissions|apps访问权限|int8[]|x|[]|可以访问的app编号|
|client_group_id|客户群租|
|metadata|其他信息||x||不需要检索的信息|

## metadata
``` json
{   "type": null,
    "contact": {
        "phone": null,
        "email": null,
        "website": null,
        "address": null,
        "city": null,
        "state": null,
        "country": null,
        "latitude": null,
        "longitude": null
    }
}
```

## 权限模式
假设现在有business A, B, C， 其中 B 和 C 隶属于 A，如下
```
    A
   / \
  B   C
```

A，B，C分别拥有独立的app访问权限，但B和C的权限不能多于A，如下
```
                        A (0, 1, 2, 3, 4, 5, 6)
                       / \
                      B   C
               (0, 1, 2)  (0, 5, 6)
```

A，B，C分别拥有独立的数据访问权限，假如访问products这个表时, B和C都只能访问标有他们business id的数据，而 A可以同时访问A，B，C 的数据。
```
A -> from products select * where product.business_id = A 
        or product.business_id = B 
        or product.business_id = C

B -> from products select * where product.business_id = B

C -> from products select * where product.business_id = C
```



## 页面逻辑
```
host\business\$business_id\$app_id
pages\business\[businessId]\[appId]
```

## access policies
```
// 员工只可以访问所属的business的词条
SELECT ->  authenticated -> id IN (select business_id from employees where employees.user_id = auth.uid()) 
```