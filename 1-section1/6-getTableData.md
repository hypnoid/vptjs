# 2.6 getTableData

### 参数

+ list : [{key:value,...},...]
+ paramList : [{[key,type],}] 传入需要设置的参数列表，同时传入一个0或者1的type参数,分别代表字符串还是数字

### 返回

返回一个整理好的[]。

其中每个数字参数都被保留两位小数，字符串参数原样返回。

而未定义的参数全部被赋值reStr或者默认的'-'。

### 代码

``` js
getTableData(list, paramList,reStr){
  let dest = [];
  list.forEach((item) => {
    let tempObj = {};
    paramList.forEach((param) => {
      let paramName = param[0];
      let type = param[1];
      if (type === 0) {
        tempObj[paramName] = this.setStr(item[paramName],reStr);
      } else {
        tempObj[paramName] = this.setNum(item[paramName],reStr);
      }
    });
    dest.push(tempObj)
  });
  return dest;
}
```

### 用法
``` js
let dataList=[
{ITEM_ID:'NAME1',ITEM_NUM1:21212.212121},
{ITEM_ID:'NAME2',ITEM_NUM1:212121},
];
let tableData = getTableData(dataList, [
  ['ITEM_NAME', 0],
  ['ITEM_NUM1', 1],
  ['ITEM_NUM2', 1],
],'--');
tableData => 
[
{ITEM_ID:'NAME1',ITEM_NUM1:21212.21,ITEM_NUM2:'--'},
{ITEM_ID:'NAME1',ITEM_NUM1:21212,ITEM_NUM2:'--'},
]
```