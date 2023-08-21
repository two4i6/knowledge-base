# apps

|表头|参数名称|类型|必填|默认|描述|CHECK|
|-|-|-|-|-|-|-|
|id|编号|int8||auto|程序编号|
|created_at|创建时间|timestamptz||now()|词条创建时间戳
|updated_at|更新时间|timestamptz|x|now()|词条更新时间戳
|layout|路由路径|text|x|"store"|"store"<br>"company"<br>"public"|
|catalog||int8|x|0|0: 通用<br>1: 销售运营<br>2: 库存管理<br>3: 采购管理<br>4: 客户关系<br>5: 财务管理<br>6: 人事管理|
|metadata|其他信息||x|{"maintenance": false, <br> "subscribable": false}|不需要检索的信息|!=null|

## apps 目录
```json
{
    "0": "仪表盘",
    "1": "企业列表",
    "2": "员工列表",
    "3": "商品库存",
    "4": "销售终端",
    "5": "订单列表",
    "6": "加油站销售终端",
    "7": "客户列表",
    "8": "油气库存"
}
```

## access policies
```
// 只有员工可以访问apps词条
SELECT -> authenticated
```