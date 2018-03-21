# Dom知识结构

## 节点操作

### 子节点

#### childNodes

##### 元素.childNodes--------元素的所有子节点，包含文本节点，元素节点

##### 元素.childNodes[0]--------第一个节点，包含文本，元素节点

#### children

##### 元素节点的集合，所有浏览器下都是元素节点，有一点需要注意的是：

###### 标准下包含非法嵌套的元素节点

###### 非标准下不包含非法嵌套的元素节点

#### 第一个子节点

##### firstChild

##### firstElementChild

##### 兼容写法

###### var oFirst=元素.firstElementChild||元素.firstChild;

###### 举例：给oUl的第一个元素加上红色背景

```
var oFirst=oUl.firstElementChild||oUl.firstChild;

if(oUl.children[0]){
	oFirst.style.backgrund='red';
}
```

###### 注意点：需要判断第一个元素是否存在

#### 最后一个子节点

##### lastChild

##### lastElementChild

##### 兼容写法

###### var oLast=元素.lastElementChild||元素.lastChild

###### 举例：还给oUl的最后一个元素加上共色背景

```
  var oLast=oUl.lastElementChild||oUl.lastChild;

oLast.style.background='red';
```

###### 注意点：需要判断最后一个元素是否存在

### 兄弟节点

#### 上一个兄弟节点

##### previousSibling

##### previousElementSibling

##### 兼容写法

###### var oPrev=元素.previousElementSibling||元素.previousSibling

###### 举例：给上一个元素添加红色背景

```
var oPrev=oLast.previousElementSibling||oLast.previousSibling;

oPrev.style.background='red';
```

###### 注意点：需要判断上一个元素是否存在

###### 元素.previousSibling含文本节点，所有oPrev要判断节点类型

#### 下一个兄弟节点

##### nextSibling

##### nextElementSibling

##### 兼容写法

###### var oNext=元素.nextElementSibling||元素.nextSibling

###### 举例：给下一个元素添加红色背景

```
var oNext=oFirst.nextElementSibling||oFirst.nextSibling

oNext.style.background='red';
```

###### 注意：需要判断上一个元素是否存在

###### 元素.nextSibling含文本节点，所有oNext要判断节点类型

### 父节点

#### 普通父节点

##### parentNode

###### 注意：元素节点，无兼容问题

#### 定位父节点

##### offsetParent

###### 注意：如果没有定位父级，默认定位父级为body，ie7以下为html

### 其他

#### 常用节点类型三个

##### 元素节点

###### 元素.NodeType返回值是1

##### 属性节点

###### 元素.NodeType返回值是2

##### 文本节点

###### 元素.NodeType返回值是3

#### nodeType

##### 元素.nodeType 返回数字，代表节点类型

#### nodeValue

##### 元素.nodeValue 节点值

###### 一般针对文本节点，针对元素节点返回的都是null，举例看备注

```
<!DOCTYPE html>
<html>
	<head>
		<meta charset="UTF-8">
		<title></title>
		<script>
			window.onload=function(){
				var oUl=document.querySelector("ul");
				var aLi=document.querySelectorAll("li");
				
				console.log(oUl.childNodes[0].nodeValue)//111
				console.log(oUl.childNodes[1].nodeValue)//null
				
			}
		</script>
	</head>
	<body>
		<ul>111
			<li>111</li>
			<li>222</li>
			<li>333</li>
			<li>444</li>
		</ul>
	</body>
</html>
```

#### nodeName

##### 元素.nodeName 节点名称

#### attributes

##### 元素.attributes 元素的属性列表集合

##### 元素.attributes[0] 单个属性

###### 元素.attributes[0].name------代表元素第0个属性的名称

###### 元素.attributes[0].value------代表元素第0个属性的值

## 定位属性

### offsetLeft、offsetTop

#### ie7及以下

##### 如果元素自身无定位，那么元素.offsetLeft/offsetTop是到body的距离

##### 如果元素自身有定位，那么元素.offsetLeft/offsetTop就是到定位父级的距离，如果没定位父级，就是到html的距离

#### 其他

##### 到定位父级的距离

### offsetParent

#### 元素的定位父级节点

### 注意：如果上面两个都没有找到定位父级，则

#### 以上offsetLeft、offsetTop是到html

#### 以上offsetParent是到body

## 样式相关

### 样式宽高

#### 元素.style.width

##### 注意：只能获取行间样式的宽高

##### 注意：含单位

### 可视宽高

#### 元素.clientWidth

##### 可视宽=样式宽+padding

##### 注意：不含单位

### 占位宽高

#### 元素.offsetWidth

##### 占位宽=样式宽+padding+border=可视宽+border

##### 注意：不含单位

## 元素的操作

### 创建元素

#### var oLi=document.creatElement('li')

### 添加元素

#### 从前面添加

##### 父级.appendChild(要添加的元素)

#### 从后面添加

##### 父级.insertBefore(要添加的元素，被插入的元素)

##### 注意1：这里有两个参数的

##### 注意2：在IE下，第二个参数的节点不存在会报错，在其他浏览器下，第二个参数的节点不存在，则会以appendChild的形式添加

##### 兼容版

###### 被插入的元素?父级.insertBefore(要添加的元素,被插入的元素):父级.appendChild(要添加的元素)

```
被插入的元素?父级.insertBefore(要添加的元素,被插入的元素):父级.appendChild(要添加的元素);
```
>即如下：
```
if(被插入的元素){
	父级.insertBefore(要添加的元素,被插入的元素)；
}else{
	父级.appendChild(要添加的元素);
}
```

### 删除元素

#### 父级.removeChild(要删除的元素);

### 剪切并替换元素

#### 父级.replaceChild(新节点，被替换的节点)

### 克隆节点(元素)

#### 要克隆的元素.cloneNode(false)

##### 注意：这个表示只克隆元素本身，不克隆元素里面的内容

##### 举例：oUl.cloneNode(false),就只克隆<ul></ul>

#### 要克隆的元素.cloneNode(true)

##### 注意：这个表示不仅克隆元素本身，还克隆元素内部的内容，克隆的范围类似outerHTML

##### 举例：oUl.cloneNode(true);克隆的是<ul><li></li>...</ul>

## 元素属性操作

### 获取属性

#### 获取指定元素的指定属性

##### 元素.getAttribute(属性名称);

##### 举例：oText.getAttribute('value')

### 设置属性

#### 给制定元素的属性设置值

##### 元素.setAttribute(属性名称，属性值)

##### 举例：oText.setAttribute('value','hello')

### 移除属性

#### 移除制定元素的制定属性

##### 元素.removeAttribute(属性名称)

##### 举例：oText.removeAttribute('value')

### 注意点：如果有自定义属性 _name_='w3c'

#### 注意点1：用.和[]无法再标准下操作自定义属性，但是用getAttribute可以操作元素的自定义属性

#### 注意点2：oImg.src和oImg[src]只可写，不可读，但是oImg.Attribute('src')可读，即可以作为判断条件（ie7以上可读）

### class相关

#### 移除class

#### 添加class

## 表单与表格

### 表格的五脏六腑

#### 表格头（只有一个）：tHead

##### 举例：oTab.tHead.style.background='red';

#### 表格正文（可以有多个）：tBodies

##### 举例：oTab.tBodies[0].rows[0].cells[0].innerHTML='1'

#### 表格尾部（只有一个）：tFoot

##### 举例：oTab.tFoot.style.background='red';

#### 表格行列

##### 行：rows

###### 举例：oTab.tBodies[0].rows.style.backgroud='red';

###### 举例：oTab.tBodies[0].rows[0].style.backgroud='red';

##### 列：cells

###### 举例：oTab.tBodies[0].cells.style.backgroud='red';

###### 举例：oTab.tBodies[0].rows[0].style.backgroud='red';

##### 举例：oTab.tBodies[0].rows[0].cells[0].style.backgroud='red';

### 表单的五脏六腑

#### 表单的操作

##### 操作一个表单只要操作其name就可以了

##### 举例：见备注

```
var oForm=document.getElementById('form1');

alert(oForm.usernamen.value);
```

#### 表单的事件

##### onchange事件

###### 当值发生改变的时候触发

####### 注意：是焦点离开的时候才会触发

###### 举例：见备注

```
oForm.username.onchange=function(){
	alert(this.value);
}
```

##### onsubmit事件

###### 点击提交直接跳转到提交页

###### 阻止提交

####### 在onsubmit时间中庸return false阻止默认提交，详见备注

```
<body>
  <form action="https://www.baidu.com/search/" method="post">
    <input type="text" name="username" id="username" value="" />
    <input type="submit" value="提交" name="submit11"/>
  </form>
</body>
```

####### 注意点：提交的是oForm，不是oForm.name,注意看备注

```
oForm.onsubmit=function(){
if (oForm.username.value==''){
alert(1);
return false;
}
}

注意：onsubmit的是oForm
```

##### 注意点

###### 注意1：当input为radio单选的时候，name都为同一个，比如说name=‘sex’，这时候oForm.sex是不对的，要用for等遍历所有的sex[I]

###### select

####### 注意；详见备注

```
<body>
  <form id="form1">
    <select name="city">
      <option value="北京">北京</option>
      <option value="上海">上海</option>
      <option value="杭州">杭州</option>
    </select>
  </form>
</body>

<script type="text/javascript">
  window.onload=function(){
    var oForm=document.querySelector("#form1");
    oForm.city.onchange=function(){
    alert(this.value);
    }
  }
</script>
```
