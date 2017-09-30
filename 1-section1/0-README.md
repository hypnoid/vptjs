# 2. SetData
 这一章中，主要记录了自己开发过程中，为前后台对接过程中的数据处理写的常用方法。

### 获取后台参数
``` js
getData(brandId) {
  axios.get('/xxx/yyy', 
  {params: {paramname: paramname}}
  ).then(resp => {
      let result = resp.data.result;
      if (resp.data.code == 200) {
          // this.setData(result);
      }
  }).catch(err => {
      console.log(err);
  })
}
```
### 数据处理

``` js
isDefine(param) {
    return param !== undefined && param !== null;
},
getStr(param,reStr){
    let re = this.isDefine(param) ? param : '-';
    if(reStr){
        re=this.isDefine(param) ? param : reStr
    }
    return re;
},
getNum(param,reStr) {
   let re = this.isDefine(param) ? param : '-';
   if(reStr){
      re=this.isDefine(param) ? param : reStr
   }
   return re;
},
setDate(str, begin, end, suffix) {
let newStr= this.setStr(str);
newStr = (newStr !== '-' ? newStr.substring(index1, index2) - 0 : '-') + suffix;
if(suffix){
    newStr += suffix;
}
return newStr;
},
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
},
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