# Prorest

> Prorest是一套promise风格restful式的API方法封装，对API返回格式严格要求进行的回调处理


####感受一下promise与restful的碰撞吧

```
var $http = new Prorestful({
        baseUrl: './'
    })

    function test(){
        // 提供GET、POST、PUT和DELETE四个请求方法
        // 返回promise对象，可以在其他地方继续执行回调
        var testAPI = $http.GET("test.json")
        

        // 请求完成后可以在其他地方执行成功的回调
        testAPI.success(function(data){
            console.log('返回status为1,接口请求成功',data)
        })

        // 也可以执行失败的回调
        testAPI.error(function(){
            console.log('返回status为0,接口请求失败',data)
        })
    }
```

####前提是接口返回格式是严格要求的

你可以根据实际接口格式修改源码对回调的判断，在源代码的第40行修改
```
{
  "status": 1,    
  "data":{},     
  "error":0,
  "info":""        
}

```

> 从严格意义上来说这不算真正的promise和restful,只是把他们的特点写法结合一下而已。