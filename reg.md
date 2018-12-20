#### 1、手机号码中间4位的更换

用到了圆括号的分组

```javascript
'18911112421'.replace(/(\d{3})\d{4}(\d{4})/, '$1****$2');
//返回
"189****2421"
```

#### 2、必须包含数字和字母的6位或7位组合

用到了向后查找  

```javascript
// ?!^/d+$ 向后查找必须有一个数字
var reg = /(?!^\d+$)(?!^[a-zA-Z]+$)^[0-9a-zA-Z]{6,7}$/;	
reg.test("12312312"); //false
reg.test("1a2321"); //true
reg.test("aaaaaa"); //false
```
#### 3、必须包含数字和字母的6位或7位组合

正则的小括号和$1在nginx中配置

```javascript
location ~ ^/shanhaohui/(.*) {
            proxy_set_header X-Real-IP $remote_addr;
            proxy_set_header Host $http_host;
            proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_http_version 1.1;
            proxy_pass http://192.168.1.52:18282/$1;
            proxy_redirect off;
    }
```

