# eloquent_javascript

## tl;dr
"Eloquent JavaScript: A Modern Introduction to Programming" の個人的まとめです。

<div class="amazlet-box" style="margin-bottom:0px;"><div class="amazlet-image" style="float:left;margin:0px 12px 1px 0px;"><a href="http://www.amazon.co.jp/exec/obidos/ASIN/B00QL616UU/kun432-22/ref=nosim/" name="amazletlink" target="_blank"><img src="https://images-fe.ssl-images-amazon.com/images/I/51PGqcewmqL._SL160_.jpg" alt="Eloquent JavaScript: A Modern Introduction to Programming" style="border: none;" /></a></div><div class="amazlet-info" style="line-height:120%; margin-bottom: 10px"><div class="amazlet-name" style="margin-bottom:10px;line-height:120%"><a href="http://www.amazon.co.jp/exec/obidos/ASIN/B00QL616UU/kun432-22/ref=nosim/" name="amazletlink" target="_blank">Eloquent JavaScript: A Modern Introduction to Programming</a><div class="amazlet-powered-date" style="font-size:80%;margin-top:5px;line-height:120%">posted with <a href="http://www.amazlet.com/" title="amazlet" target="_blank">amazlet</a> at 17.04.22</div></div><div class="amazlet-detail">No Starch Press (2014-12-05)<br /></div><div class="amazlet-sub-info" style="float: left;"><div class="amazlet-link" style="margin-top: 5px"><a href="http://www.amazon.co.jp/exec/obidos/ASIN/B00QL616UU/kun432-22/ref=nosim/" name="amazletlink" target="_blank">Amazon.co.jpで詳細を見る</a></div></div></div><div class="amazlet-footer" style="clear: left"></div></div>

## まとめ

### 2. Program Structure

#### Excercise

##### Looping a triangle

```javascript
var str = "";
while(str.length < 7){
    str += "#";
    console.log(str);
}
```

##### FizzBuzz

```javascript
for (var i = 1; i <= 100; i++){
    if (i % 15 == 0) console.log("FizzBuzz");
    else if (i % 3 == 0) console.log("Fizz");
    else if (i % 5 == 0) console.log("Buzz");
    else console.log("");
}
```

#### Chess board

```javascript
var size = 8;
for (var i = 1; i <= size; i++){
    var str = "";
    if (i % 2) {
        for (var j = 1; j <= size; j++){
            if (j % 2) str += "#";
            else str += " ";
        }
    } else {
        for (var j = 1; j <= size; j++){
            if (j % 2) str += " ";
            else str += "#";
        }
    }
    console.log(str);
}
```

美しくないので、少し変えてみる

```javascript
var size = 8;
for (var i = 1; i <= size; i++){
    var str = "";
    for (var j = 1; j <= size; j++){
        str += getColor(i, j);
    }
    console.log(str);
}

function getColor(x, y){
    var str = "";
    if (x % 2) {
        str = y % 2 ? "#" : " ";
    } else {
        str = y % 2 ? " " : "#";
    }
    return str;
}
```

### 3. Functions

#### Excercise

##### Minimum

```js
var min = function (a, b) {
    return a < b ? a : b; 
};
```

##### Recursion

```js
var isEven = function (i) {
    var num = i;
    if (num == 0){
        return true;
    } else if (num == 1) {
        return false;
    } else {
        return isEven(num - 2);
    }
};
```

テスト

```
> isEven(50);
true
> isEven(75);
false
> isEven(-1);
RangeError: Maximum call stack size exceeded
    at isEven (repl:1:29)
    at isEven (repl:8:8)
    at isEven (repl:8:8)
    at isEven (repl:8:8)
    at isEven (repl:8:8)
    at isEven (repl:8:8)
    at isEven (repl:8:8)
    at isEven (repl:8:8)
    at isEven (repl:8:8)
    at isEven (repl:8:8)
```

-1以下だと無限になってしまうので修正

```js
var isEven = function (i) {
    var num = i;
    if (num == 0){
        return true;
    } else if (num == 1) {
        return false;
    } else {
        if(num > 0) { 
            return isEven(num - 2);
        } else {
            return isEven(num + 2);
        }
    }
};
```

結果

```
> isEven(50);
true
> isEven(75);
false
> isEven(1);
false
> isEven(0);
true
> isEven(-1);
false
> isEven(-50);
true
> isEven(-75);
false
```

絶対値とかにすればいいのかなと思うけど、%2でできることをわざわざこんなふうにやってるのだから、あんまり美しくないけどまあいいか。

##### Bean counting 

```js
var countBs = function (s) {
    var count = 0;
    for (var i = 0; i < s.length; i++) {
        if (s[i] == "B") count++;
    }
    return count;
};
```

```js
var countChar = function (s,c) {
    var count = 0;
    for (var i = 0; i < s.length; i++) {
        if (s[i] == c) count++;
    }
    return count;
};
```