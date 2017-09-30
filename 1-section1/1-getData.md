# 2.1 getData

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