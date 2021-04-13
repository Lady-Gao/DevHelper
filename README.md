```js
 <DevHelper  :loadpath='loadpath' :listAPI='listAPI'  :listsocketAPI='listsocketAPI' ></DevHelper>
```
### 快捷键打开
> window + s

### loadpath
> 文件上传地址
```JS
loadpath:'https://ip/upload'
```

### listAPI
> 后台调试 地址数组
```JS
 listAPI:{
         defaultUrl:'http://10.10.12.163:18000',//默认选中
         list:[
            {label:'person1',value:'http://10.10.11.172:18000'},
            {label:'person2',value:'http://10.10.12.163:18000'},
            {label:'person3',value:'http://10.10.11.69:18000'},
                ...
        ],
       },
```
### listsocketAPI    
> socket 地址数组
```JS
 listsocketAPI:{
         defaultUrl:'http://10.10.12.163:9099',//默认选中
         list:[
            {label:'socket1',value:'http://10.10.11.172:9099'},
            {label:'socket2',value:'http://10.10.12.163:9099'},
            {label:'socket3',value:'http://10.10.11.69:9099'},
                ...
        ],
       },
```
