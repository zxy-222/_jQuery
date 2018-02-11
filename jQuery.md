## jQuery

- #### 第二章——选择器

  - ##### 1、CSS选择器

    - ***标签选择器、ID选择器、类选择器、交集选择器、后代选择器、通配选择器***

  - ##### 2、jQuery选择器

    - ***1、基本选择器***

      | 选择器                    | 描述                  | 返回   | 示例                                       |
      | ---------------------- | ------------------- | ---- | ---------------------------------------- |
      | \#id                   | 根据给定的id匹配一个元素       | 单个元素 | $('#test')选取id为test的元素                   |
      | .class                 | 根据给定的类名匹配元素         | 集合元素 | $('.test')选取class为test的元素                |
      | element                | 根据给定的元素名匹配元素        | 集合元素 | $('p')选取所有的p元素                           |
      | *                      | 匹配所有元素              | 集合元素 | $('*')选取所有的元素                            |
      | selector1、...selectorN | 将每一个选择器匹配到元素合并后一起返回 | 集合元素 | $('div,span,p.myClass')选取所有div和span和拥有class为myClass的p标签的一组元素 |

    - ##### 2、层次选择器

      | 选择器                      | 描述                           | 返回   | 示例                                      |
      | ------------------------ | ---------------------------- | ---- | --------------------------------------- |
      | $('ancestor descendant') | 选取ancestor元素里的所有descendant元素 | 集合元素 | $('div span')选取div里的所有的span元素           |
      | $('parent > child')      | 选取parent元素下的child元素          | 集合元素 | $('div>span')选取div元素下元素名为span的元素        |
      | $('prev +next')          | 选取紧接在prev元素后的next元素          | 集合元素 | $('.one +div')选取class为one的下一个div同辈元素    |
      | $('prev~siblings')       | 选取prev元素之后的所有siblings元素      | 集合元素 | $('.two~div')选取class为two的元素后面的所有div同辈元素 |

    - 可以使用***next()***方法来代替***$('prev+next')***选择器

    - 可以使用***nextAll()***方法来代替***$('prev~siblings')***选择器

    - ***siblings()***与***$('prev~siblings')***的区别：

      - ***$('prev~siblings')***选择器只能选择***'prev'***元素后面的同辈***div***元素
      - ***siblings()***方法与前后位置无关，只要是同辈节点就能匹配

    - ##### 3、过滤选择器

      - ***1、基本过滤选择器***

        | 选择器            | 描述                        | 返回   | 示例                                       |
        | -------------- | :------------------------ | ---- | ---------------------------------------- |
        | :first         | 选取第一个元素                   | 单个元素 | $('div:first')选取所有div中第一个div元素           |
        | :last          | 选取最后一个元素                  | 单个元素 | $('div:last')选取所有div中最后一个div元素           |
        | :not(selector) | 去除所有与给定选择器匹配的元素           | 集合元素 | $('input:not(.myClass)')选取class不是myClass的input元素 |
        | :even          | 选取索引是偶数的所有元素，索引从0开始       | 集合元素 | $('input:even')选取索引是偶数的input元素           |
        | :odd           | 选取索引是奇数的所有元素，索引从0开始       | 集合元素 | $('input:odd')选取索引是奇数的input元素            |
        | :eq(index)     | 选取索引等于index的元素(index从0开始) | 单个元素 | $('input:eq(1)')选取索引是1的input元素           |
        | :gt(index)     | 选取索引大于index的元素(index从0开始) | 集合元素 | $('input:gt(1)')选取索引大于1的input元素(不包括1)    |
        | :lt(index)     | 选取索引小于index的元素(index从0开始) | 集合元素 | $('input:lt(1)')选取索引小于1的input元素(不包括1)    |
        | :header        | 选取所有的标题元素，例如h1,h2,h3等     | 集合元素 | $(':header')选取网页中所有的h1,h2,.....          |
        | :animated      | 选取当前正在执行动画的所有元素           | 集合元素 | $('div:animated')选取正在执行动画的div元素          |
        | :focus         | 选取当前获取焦点的元素               | 集合元素 | $(':focus')选取当前获取焦点的元素                   |

      - ***2、内容过滤选择器***

        | 选择器              | 描述                 | 返回   | 示例                                     |
        | ---------------- | ------------------ | ---- | -------------------------------------- |
        | :containes(text) | 选取含有文本内容为'text'的元素 | 集合元素 | $('div:contains('我')'),选取含有文本'我'的div元素 |
        | :empty           | 选取不包含子元素或者文本的空元素   | 集合元素 | $('div:empty')选取不包含子元素(包括文本)的div空元素    |
        | :has(selector)   | 选取含有选择器所匹配的元素的元素   | 集合元素 | $('div:has(p)')选取含有p元素的div元素           |
        | :parent          | 选取含有子元素或者文本的元素     | 集合元素 | $('div:parent')选取拥有子元素(包括文本)的div元素     |

      - ***3、可见性过滤选择器***

        | 选择器      | 描述         | 返回   | 示例                           |
        | -------- | ---------- | ---- | ---------------------------- |
        | :hidden  | 选取所有不可见的元素 | 集合元素 | $(':hidden')选取所有不可见的元素       |
        | :visible | 选取所有可见的元素  | 集合元素 | $('div:visible')选取所有可见的div元素 |

      - ***4、属性过滤选择器***

        | 选择器                                     | 描述                                       | 返回   | 示例                                       |
        | --------------------------------------- | ---------------------------------------- | ---- | ---------------------------------------- |
        | [attribute]                             | 选取拥有此属性的元素                               | 集合元素 | $('div[id]')选取拥有属性id的元素                  |
        | [attribute=value]                       | 选取属性的值为value的元素                          | 集合元素 | $('div[title=test]')选取属性title为'test'的div元素 |
        | [attribute!=value]                      | 选取属性的值不等于value的元素                        | 集合元素 | $('div[title!=test]')选取属性title不为'test'的div元素 |
        | [attribute^=value]                      | 选取属性以value开始的元素                          | 集合元素 | $('div[title^=test]')选取属性title以'test'开始的div元素 |
        | [attribute$=value]                      | 选取属性以value结束的元素                          | 集合元素 | $('div[title\$=test]')选取属性以title以'test'结尾的div元素 |
        | [attribute*=value]                      | 选取属性的值含有value的元素                         | 集合元素 | $('div[title*=test]')选取属性title含有test的div元素 |
        | [attribute\|=value]                     | 选取属性等于给定字符串为或以该字符串为前缀(该字符串后跟一个连字符"_")的元素 | 集合元素 | $('div[title\|="en"]')选取属性以title等于en或以en为前缀的(该字符串后跟一个连字符"_")div元素 |
        | [attribute~=value]                      | 选取属性用空格分隔的值中包含一个给定值的元素                   | 集合元素 | $('div[title~="uk"]')选取属性title用空格分隔的值中包含字符uk的元素 |
        | \[attribute1]\[attribute2]\[attributeN] | 用属性选择器合并成一个复合属性选择器，满足多个条件                | 集合元素 | $('div[id]\[title\$="test"]')选取拥有属性id，并且属性title以”test“结尾的div元素 |

      - ***5、子元素过滤选择器***

        | 选择器                        | 描述                                   | 返回   | 示例                                       |
        | -------------------------- | ------------------------------------ | ---- | ---------------------------------------- |
        | :nth-child(index/even/odd) | 选取每个父元素下的第index个子元素或者奇偶元素(index从1开始) | 集合元素 | 为每一个父元素匹配子元素                             |
        | :first-child               | 选取每个父元素的第一个子元素                       | 集合元素 | :first只返回单个元素,:first-child为每个父元素匹配第一个子元素 |
        | :last-child                | 选取每个父元素的最后一个子元素                      | 集合元素 | :last只返回单个元素,:last-child为每个父元素匹配最后一个子元素  |
        | :only-child                | 如果某个元素是它父元素中唯一的子元素，那么将会被匹配           | 集合元素 | $('ul li:only-child')在ul中选取唯一的子元素的li元素   |

        - 1、:nth-child(even)能选取每个父元素下的索引值是偶数的元素
        - 2、:nth-child(odd)能选取每个父元素下的索引值是奇数的元素
        - 3、:nth-child(2)能选取每个父元素下的索引值等于2的元素
        - 4、:nth-child(3n)能选取每个父元素下的索引值是3的倍数的元素(n从1开始)
        - 5、:nth-child(3n+1)能选取每个父元素下的索引值是(3n+1)的元素

      - ***6、表单对象属性过滤选择器***

        | 选择器       | 描述                  | 返回   | 示例                                       |
        | --------- | ------------------- | ---- | ---------------------------------------- |
        | :enabled  | 选取所有可用元素            | 集合元素 | $("#form1 :enabled")选取id为form1的表单内的所有可用的元素 |
        | :disabled | 选取所有不可用元素           | 集合元素 | $("#form :disabled")选取id为form2的表单内的所有不可用的元素 |
        | :checked  | 选取所有被选中的元素(单选框、复选框) | 集合元素 | $("input:checked")选取所有被选中的input元素        |
        | :selected | 选取所有被选中的选项元素(下拉列表)  | 集合元素 | $("select option:selected")选取所有被选中的选项元素  |

    - ##### 4、表单选择器

      | 选择器       | 描述                                | 返回   | 示例                                       |
      | --------- | --------------------------------- | ---- | ---------------------------------------- |
      | :input    | 选取所有的input、textarea、select、button | 集合元素 | $(':input')选取所有的input、select、textarea、button |
      | :text     | 选取所有的单行文本框                        | 集合元素 | $(':text')选取所有单行文本框                      |
      | :password | 选取所有的密码框                          | 集合元素 | $(':password')选取所有的密码框                   |
      | :radio    | 选取所有的单选框                          | 集合元素 | $(':radio)选取所有的单选框                       |
      | :checkbox | 选取所有的复选框                          | 集合元素 | $(':checkbox')选取所有的复选框                   |
      | :submit   | 选取所有的提交按钮                         | 集合元素 | $(':submit')选取所有的提交按钮                    |
      | :image    | 选取所有的图像按钮                         | 集合元素 | $(':image')选取所有的图像按钮                     |
      | :reset    | 选取所有的重置按钮                         | 集合元素 | $(':reset')选取所有的重置按钮                     |
      | :button   | 选取所有的按钮                           | 集合元素 | $(':button')选取所有的按钮                      |
      | :file     | 选取所有的上传域                          | 集合元素 | $(':file')选取所有的上传域                       |
      | :hidden   | 选取所有的不可见元素                        | 集合元素 | $(':hidden')选取所有不可见元素                    |

- #### 第三章 —— jQuery中的DOM操作

  - ##### 1、DOM操作的分类

    - ***1、DOM Core —— javascript中的getElementById()、getElementByTagName()、getAttribute()、setAttribute()***
    - ***2、HTML-DOM***
    - ***3、CSS-DOM***

  - ##### 2、jQuery中的DOM操作

    - **1、查找结点**

      - ***1、查找元素节点***

        ```
        var $li = $("ul li:eq(1)"); //获取<ul>里第2个<li>节点
        ```

      - ***2、查找属性节点***

        - 利用jQuery选择器查找到需要的元素之后，可以使用attr()方法来获取它的各种属性值

          ```
          var $para = $("p"); //获取<p>节点
          var p_txt= $para.attr("title");//获取<p>元素节点属性title
          ```

    - **2、创建节点**

      - ***1、创建元素节点***

        - 1、$(html)方法会根据传入的HTML标记字符串，创建一个DOM对象，并将这个对象生成一个jQuery对象后返回。

        - 2、然后使用jQuery中的append()方法

          ```
          var $li = $("<li></li>");
          $("ul").append($li)
          ```

      - ***2、创建文本节点***

        - 1、创建文本节点就是创建节点时直接把文本内容写出来

          ```
          var $li = $("<li>我是文本节点</li>");
          $("ul").append($li)
          ```

      - ***3、创建属性节点***

        - 创建属性节点与创建文本节点类似，也是直接再创建元素节点时一起创建

          ```
          var $li = $("<li title="属性节点">我是文本节点</li>");
          $("ul").append($li)
          ```

    - **3、插入节点**

      - ***动态创建HTML元素并没有实际用处，还需要将新创建的元素插入文档中***

      - ***插入节点的方法***

        | 方法            | 描述                | 示例                                    |
        | ------------- | ----------------- | ------------------------------------- |
        | append()      | 向每个匹配的元素内部追加内容    | $("A").append("B");向A标签中添加B标签         |
        | appendTo()    | 将所有匹配的元素追加到指定的元素中 | $("B").append("A");将B标签添加到A标签中        |
        | prepend()     | 向每个匹配的元素内部前置内容    | $("A").prepend("B");向A标签中添加B标签中最前面    |
        | prependTo()   | 将所有匹配的元素前置到指定的元素中 | $("B").append("A");将B标签添加到A标签中最前面     |
        | after()       | 在每个匹配的元素之后插入内容    | $("A").after("B");向A标签后面添加B标签         |
        | insertAfter() | 将所有匹配的元素插入到指定元素后面 | $("B").insertAfter("A");将B标签添加到A标签后面  |
        | before()      | 在每个匹配的元素之前插入内容    | $("A").before"B");向A标签前面添加B标签         |
        | insertBefore  | 将所有匹配的元素插入到指定元素前面 | $("B").insertBefore("A");将B标签添加到A标签前面 |

    - **4、删除节点**

      - ***删除节点的三种方法：remove()、detach()、empty()***

      - ***1、remove()方法***

        - 当某个节点使用remove()方法删除后,该节点所包含的所有后代节点将同时被删除。这个方法返回值是一个指向已被删除的节点的引用

          ```
          var $li = $("ul li:eq(0)").remove();//获取ul中第一个li元素节点后，将它从网页中删除
          $li.appendTo("ul")；//把删除的li元素节点有重新添加到ul中
          ```

      - ***2、detach()方法***

        - detach()和remove()一样，也是从DOM中去掉所有匹配的元素。但这个方法不会把匹配的元素从jQuery对象中删除，因而可以在以后可再使用这些匹配的元素。而且所有绑定的事件、附加的数据等都会保留下来。

          ```
          $("ul li").click(function(){
            alert($(this).html())
          })
          var $li = $("ul li:eq(0)").detach();//删除元素
          $li.appendTo("ul"); //重新追加此元素，之前绑定的点击事件还在。若使用remove()方法删除元素的话，那么它之前绑定的事件将失效
          ```

      - ***3、empty()方法***

        - 严格的说，empty()方法不是删除节点，而是清空节点，它能清空元素中的所有后代节点

          ```
          $("ul li：eq(0)").empty()；//获取ul中的第一个li，将li中的元素清空
          ```

    - **5、复制节点**

      - ***复制节点后，被复制的新元素不具有任何行为***

        ```
        $("ul li").click(function(){
          $(this).clone().appendTo("ul");//复制当前单击的节点，并将其追加到ul元素中
        })
        //若需要新元素也具有新功能（本例是点击事件）则
        $(this).clone(true).appendTo(); // 即在clone中添加参数true
        ```

    - **6、替换节点**

      - ***替换节点方法：replaceWidth()和replaceAll()***

      - ***1、replaceWidth()方法的作用是将所有匹配的元素都替换成指定的HTML或者DOM***

        ```
        例：<p>p元素</p>
        replaceWidth()
        $("p").replaceWidth("<div>div元素</div>")；//将p元素以及其内容替换成div元素和内容；
        replaceAll()和replaceWidth()一样，只是颠倒一下
        $("<div>div元素</div>").replaceAll("p")；//将p元素以及其内容替换成div元素和内容；
        ```

    - **7、包裹节点**

      - ***1、wrap()方法***

        ```
        $("p").wrap("<div></div>");//用div标签把p标签包裹起来
        结果：<div><p>p标签</p></div>
        //每个p元素都会有一个div元素包裹
        ```

      - ***2、wrapAll()方法***

        ```
        $("p").wrapAll("<div></div>");//用div标签把p标签包裹起来
        结果：<div>
        		<p></p>
        		<p></p>
        	 </div>
        //该方法会将所有匹配的元素用一个元素包裹     
        ```

      - ***3、wrapInner()方法***

        ```
        $("li").wrapInner("<div></div>");
        结果：<li><div>li标签<div>></li>
        ```

    - **8、属性操作**

      - ***jQuery中，用attr()方法来获取和设置元素属性，removeAttr()方法来删除元素属性***

      - ***1、获取和设置属性***

        ```
        //获取属性
        var $p = $("p");            //获取p节点
        var p_txt = $p.attr("title")；//获取p元素节点属性title

        //设置属性
        $("p").attr("title","your title")
        //设置多个属性
        $("p").attr({"title":"your title","name":"test"})
        ```

      - ***2、删除属性***

        ```
        $("p").removeAttract("title");//删除p元素的属性title
        ```

      - ***3、prop()和removeProp()***

        - ***prop()***——用来获取在匹配元素集中第一个元素的属性值
        - ***removeProp()***——为匹配的元素删除设置的属性

    - **9、样式操作**

      - ***1、获取样式和设置样式***

        ```
        HTML代码
        <p class="myClass" title="p标签">这是p元素</p>

        //使用attr()方法获取p元素的class
        var p_class = $("p").attr("class"); //获取p元素的class

        //也可以使用attr()方法设置p元素的class
        $("p").attr("class","x"); //设置p元素的class为"x"
        运行代码后：<p class="x title="p标签">这是p元素</p>
        //该方法是将原来的class(myClass)替换为新的class(x)
        ```

      - ***2、追加样式***

        - ***addClass()方法用来追加样式***

          ```
          $("p").addClass("y");  //给p元素追加 "y"类
          ```

        - ***attr()***和***addClass()***的区别

          | 方法         | add Class()               | attr()                   |
          | ---------- | ------------------------- | ------------------------ |
          | 用途         | 追加样式                      | 设置样式                     |
          | 对同一个网页元素操作 | <p&gt;test<p&gt;          | <p&gt;test<p&gt;         |
          | 第1次使用方法    | $("p").addClass("x")      | $("p").attr("class","x") |
          | 第1次结果      | \<p class="x">test\</p>   | \<p class="x">test\</p>  |
          | 再次使用方法     | $("p").addClass("y")      | $("p").attr("class","y") |
          | 最终方法       | \<p class="x y">test\</p> | \<p class="y">test\</p>  |

      - ***3、移除样式***

        - ***removeClaas()***方法移除类名

          ```
          $("p").removeClass("x");

          //若要删除多个类，则需要使用多次removeClass();
          $("p").removeClass("x").removeClass("y");

          //当然也可以以空格的方式删除多个class
          $("p").removeClass("x y");

          //若括号里没参数，则删除全部类
          $("p").removeClass();  //移除p元素的所有class
          ```

      - ***4、切换样式***

        - ***toggle()***  ——交替执行代码

      - ***5、判断是否含有某个样式***

    - **10、设置和获取HTML、文本和值**

    - **11、遍历节点** 

    - **12、CSS-DOM操作**