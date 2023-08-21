# TABLE 与 APPS 的对应权限
|APP\TABLE|apps|businesses|companies|staffs|clients|client_points|orders|payments|products|
|-|-|-|-|-|-|-|-|-|-|
|全体|r(local)|r(local)|r(local)|
|#1 店铺/部门||ru(global)|
|#2 企业|||ru(global)|
|#3 员工||||rwu(global)|
|#4 商品|||||||||rwu(local)|
|#5 油品|||||||||ruw(local)|
|#6 订单|||||||rw(refund)(local)|rw(refund)(local)|
|#7 商品POS||||r(local)|r(global)|rwu(global)|rwu(local)|rw(local)|r(local)|
|#8 油品POS||||r(local)|r(global)|rwu(global)|rwu(local)|rw(local)|r(local)|
|#9 客户|||||rwu(global)|rwu(global)|rw(refund)(global)|rw(refund)(global)|
||||

> r: 可读
> 
> w: 可写
>
> u: 可更新
>
> (local): 当前店铺的数据
>
> (global): 全公司的数据

# TABLE 简介

# clients
|表头|id|create_at|update_at|family_master|user_id|company_id|metadata|
|-|-|-|-|-|-|-|-|
|||||
|类型|text(uuid)|timestamptz|timestamptz|text(uuid)|text(uuid)|int8|jsonb|
|foreign||||clients->id|auth->user->id|companies->id|
|默认|id+|now()|now()||||{}|
|必填|||x|x|x|x|x|x|

metadata
``` json
{
    "contact": {
        "name": string,
        "birthday": string,
        "plate": string,
        "wechat": string,
    }
    "remark": string,
}
```