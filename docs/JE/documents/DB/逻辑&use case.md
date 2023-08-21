# 数据库逻辑
## 油品采购
```
                      |---无---创建供应商---|
预购   clients(供应商)--|                   |---选择与供应商有关的商品ids    
                      |---有--------------|            |                   
                                                      |
                                            创建 order(type: purchase)
                                            

                                                    



入库    insert inventories_detail(type: 油)---link(optional)--->相关 order 记录order和供应商信息在metadata中
                        |
                        |
                        |              |---无---insert inventories记录
        select inventories 有相关记录---|
                                       |---有---update inventories记录
                                                    
```

## 商品采购
```
                      |---无---创建供应商---|
预购   clients(供应商)--|                   |---选择与供应商有关的商品ids    
                      |---有--------------|            |                   
                                                      |
                                            创建 order(type: purchase)
                                            

                                                    



入库    insert inventories_detail(type: 商品)---link(optional)--->相关 order/供应商 记录order/供应商信息在metadata中
                        |
                        |
                        |              |---无---insert inventories记录
        select inventories 有相关记录---|
                                       |---有---update inventories记录
                                                    
```