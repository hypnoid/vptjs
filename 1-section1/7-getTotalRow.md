# 2.7 getTotalRow

### 参数

+ list : [{key:value,...},...]
+ paramList : [{[key],}] 传入需要设置的参数列表

### 返回

返回一个合计行。其中每个数字都被保留两位小数。

### 代码

``` js
getTotalRow(list, paramList) {
    let total = {};
    paramList.forEach((paramName) => {
        total[paramName] = 0;
    });
    list.forEach((item) => {
        paramList.forEach((paramName) => {
            total[paramName] += item[paramName] === '-' ? 0 : item[paramName];
        });
    });
    return total;
}
```

### 用法
``` js
let dataList=[
{ITEM_ID:'NAME1',ITEM_NUM1:1,ITEM_NUM2:11},
{ITEM_ID:'NAME2',ITEM_NUM1:2,ITEM_NUM2:22},
];

let totalRow = getTotalRow(detailTableData, ['ITEM_NUM1','ITEM_NUM2',]);

totalRow => {ITEM_NUM1:3,ITEM_NUM2:33}

```