# Javascript技巧

### 1. Javascript数组转换为CSV格式

	<p id="sports">basketball,badminton,jogging</p>

```javascript
var sportsArr = ['basketball', 'badminton', 'jogging'];
var csv = sportsArr.valueOf();
document.getElementById('sports').innerHTML = csv;
```
或者
```javascript
var sports = ['basketball', 'badminton', 'jogging'];
var csv = sports.join(',');
```

### 2. 将CSV格式重新转换回Javscript数组
```javascript
var csv = 'basketball,badminton,jogging';
var sportsArr = csv.split(',');
```

### 3. 移除数组中的某个元素
```javascript
删除数组中第二个元素
var sportsArr = ['basketball', 'badminton', 'jogging'];
sportsArr.splice(1, 1);
```
### 4. 产生1到N的随机数
```javascript
var random = Math.floor(Math.random() * N + 1);
```

### 5. 去掉数组中的重复元素
```javascript
function removeDuplicates(arr) {
    var tempObj = {};
    for (var i = 0; i < arr.length; i++) {
        tempObj[arr[i]] = true;
    }
  
    var tempArr = [];
    for (var key in tempObj) {
        tempArr.push(key);
    }
    return tempArr;
}
```

### 6. 去掉字符串前后多余的空格
```javascript
if (!String.prototype.trim) {
    String.prototype.trim=function() {
       return this.replace(/^\s+|\s+$/g, '');
    };
}
```