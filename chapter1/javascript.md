判断为空，value==“”。

正则一般直接查就行。

js事件：写函数前要确定事件，例如onclick onload  onsubmit等。

---

```js
案例1：表单校验。
步骤分析
第一步：确定事件(onsubmit)并为其绑定一个函数
第二步：书写这个函数(获取用户输入的数据)
第三步：对输入的数据进行判断(非空)
第四步：如果输入的内容为空，给出错误提示信息(alert),不让表单提交
第五步：如果输入的内容合法，让表单提交。
Html部分代码：
为表单绑定一个事件
<formaction="#"method="get"onsubmit="returncheckForm()">
对需要校验的输入项目定义id
<inputtype="text"name="user"id="user"/>
Javascript部分代码
<script type="text/javascript">
    function checkForm(){
        /*校验用户名*/
        //alert("aa");
        //获取用户输入的数据
        var uValue =  document.getElementById("user").value;
        //alert(uValue);
        if(uValue==""){
            //给出错误提示信息
            alert("用户名不能为空！");
            return flase;
        }

        /*校验邮箱*/
        var Evalue = document.getElementById("email").value;
        if(!/^([a-zA-Z0-9_-])+@([a-zA-Z0-9_-])+(.[a-zA-Z0-9_-])+/.test(Evalue)){
        //给出错误提示信息
            alert("邮箱格式不正确！");
            return false;
        }
    }
</script>
```

---

```js
案例2：轮播图效果。
2.技术分析
获取元素document.getElementById(“id名称”)
事件(onload)
定时操作：setInterval(“
changeImg()
”,
3000
);
3.步骤分析
第一步：确定事件(页面加载事件onload)并为其绑定一个函数
第二步：书写这个函数(设置一个定时操作);
第三步：书写定时操作里面的函数
第四步：获取图片的位置
第五步：为该图片设置src属性值。
4.代码实现
Javascript部分代码：

<script>
    function init(){
        setInterval("changeImg()",3000);
    }

    var i=1;
    function changeImg(){
        i++;
        var imgEl = document.getElementById("img1");
        imgEl.src="../img/"+i+".jpg";
        if(i==3){
            i=0;
        }
    }

</script>

Html部分代码：
确定事件：onload加在body里面！
<bodyonload="init()">
给指定的图片位置定义一个id
<imgsrc="../img/1.jpg"width="1300px"id="img1"/>
```

---

```js
案例3：定时弹出广告
2.技术分析
获取图片的位置(document.getElementById(“”))
隐藏图片：display：none
定时操作：setInterval(“显示图片的函数”，3000);

3.步骤分析
第一步：确定事件(页面加载事件onload)并为其绑定一个函数init()
第二步：在init函数中设置一个显示图片的定时操作。
第三步：书写显示图片的函数(获取图片元素，设置其display属性为block)
第四步：设置一个隐藏图片的定时操作
第五步：书写隐藏图片的函数(获取图片元素，设置其display属性为none)

4.代码实现
Javascript部分代码：
<script type="text/javascript">
    var time;
    function init(){
        //设置显示图片的定时操作
        time = setInterval("showAd()",3000);
    }

    //显示图片的函数
    function showAd(){
        //获取广告图片的
        var imgEl = document.getElementById("img1");
        //设置图片的属性(display)让其显示
        imgEl.style.display="block";

        //清除显示图片的定时操作
        clearInterval(time);

        //设置隐藏广告图片的定时操作
        time = setInterval("hiddenAd()",3000);
    }

    //书写隐藏广告图片的函数
    function hiddenAd(){
        //获取广告图片并设置隐藏的属性
        document.getElementById("img1").style.display="none";
        //清除隐藏图片的定时操作
        clearInterval(time);
    }
</script>

Html部分代码：
<img src="../img/f001a62f-a49d-4a4d-b56f-2b6908a0002c_g.jpg" width="1300px" style="display: none;" id="img1"/>

确定事件(<body onload="init()">)
```

---

```
案例4：表单校验升级版
2.技术分析
使用事件(聚焦事件onfocus和离焦事件onblur),之前使用onsubmit也需要！
使用<span></span>
向页面指定位置写入内容：innerHTML属性(该属性的值存在覆盖现象)
3.步骤分析
第一步：确定事件(给出提示信息使用聚焦事件，给出校验结果信息使用离焦事件)并为其绑定函数
第二步：聚焦事件绑定的函数中(获取span给出提示信息)
第三步：离焦事件绑定的函数中(获取用户输入的内容进行判断)
第四步：如果失败，在span位置给出错误提示信息，如果成功，让span内容为空。
4.代码实现
Javascript部分代码：
<sctript>
	function showTips(id,info){
		//获取span元素，给出提示信息
		document.getElementById(id+"span").innerHTML="<font color='gray'>"+info+"</font>";
	}
	
	function check(id,info){
		//获取用户输入的数据
		var uValue = document.getElementById(id).value;
		//进行判断
		if(uValue==""){
			//在span位置给出错误提示信息
			document.getElementById(id+"span").innerHTML="<font color='red'>"+info+"</font>";
		}else{
			document.getElementById(id+"span").innerHTML="";
		}
	}
	
</script>

Html部分代码
<input type="text" name="user" id="user" onfocus="showTips('user','用户名必须以字母开头！')" onblur="check('user','用户名不能为空！')"/><span id="userspan"></span>


```









