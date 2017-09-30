# 3.1 Elemet.js 

## Table

### 表格属性
+ max-height
+ default-sort

### 表格事件
+ sort-change  当表格的排序条件发生变化的时候会触发该事件 {column, prop, order} 

### 列属性
+ prop 对应列内容的字段名
+ label 显示的标题
+ render-header 列标题 Label 区域渲染使用的 Function
+ sortable 如果设置为 'custom'，需要监听 Table 的 sort-change 事件
+ formatter 用来格式化内容 Function(row, column, cellValue)
+ show-overflow-tooltip 当内容过长被隐藏时显示 tooltip Boolean

### 自定义排序方法
#### 自定义合计行固定首航排序
+ 注意:将xxx换成相关属性名
+ Code:
``` js 
sortChange(param) {
    let prop = param.prop;
    let order = param.order;
    let totalObj;
    if (this.tableData.length > 0) {
        for (let i = 0; i < this.tableData.length; i++) {
            if (this.tableData[i]['xxx'] === '合计') {
                totalObj = this.tableData.splice(i, 1)[0];
            }
        }
        this.tableData = this.tableData.sort(function (a, b) {
            let temp_a = a[prop];
            let temp_b = b[prop];
            temp_a = temp_a !== '-' ? temp_a : -Number.MAX_VALUE;
            temp_b = temp_b !== '-' ? temp_b : -Number.MAX_VALUE;
            return order === 'descending' ? temp_b - temp_a : temp_a - temp_b;
        });
        this.tableData.splice(0, 0, totalObj);
    }
    return this.tableData;
  }
```