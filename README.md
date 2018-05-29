# ife2018
百度前端技术学院2018学期学习仓库

## CSS学院
### 01.制作一个简单的菜单动画效果
![效果图](https://ws4.sinaimg.cn/large/006tKfTcgy1fqwr6d6wbmg303e03bk9t.gif)

需要用到CSS transition 、transform以及js的事件处理。通过点击按钮，切换目标节点的class从而切换样式（改变样式的任务尽量交给CSS来完成）。
html
```
<div class="tag active">
    <span>前端学院</span>
</div>
<button id=btn>切换样式</button>
<script>
    document.getElementById('btn').addEventListener('click', () => {
        document.querySelector('.tag').classList.toggle('active')
    })
    </script>
```

css
```
.tag {
    margin: 20px;
}
button {
    margin: 20px;
}

span {
    position: relative;
    transition: all .3s;
}
span::after {
    content: '';
    position: absolute;
    bottom: -30%;
    width: 0;
    left: 50%;
    transform: translateX(-50%);
    margin: 0 auto;
    display: block;
    border-bottom: 2px solid #088fc0;
    transition: all .3s;
    
}
.active span {
    color: #088fc0;
}
.active span::after {
    width: 110%;
}
```
### 02.初步接触CSS 2D变形
[预览地址](https://lin-ya.github.io/ife2018/CSS%E5%AD%A6%E9%99%A2/02/demo.html)
这个需要对css transform里面的各个子属性进行了解，通过这个练习可以得知以后能将里面的各个子属性进行配合一起实现各种不同形状的几何图形（不仅仅是几何图形）。
```css
    #box1 {
        transform: skewX(30deg);
    }
    #box2 {
        transform: scaleX(.5);
    }
    #box3 {
        transform: rotate(45deg);
    }
    #box4 {
        transform: translate(10px , 20px);
    }
    #box5 {
        transform: skewX(30deg) scaleX(.5) rotate(45deg) translate(10px , 20px);
    }
```

### 03.CSS transition 和 CSS transform 配合制作动画
[预览地址](https://lin-ya.github.io/ife2018/CSS学院/03/demo.html)
顾名思义，这是一个需要你用到transition和transform来实现的动画。transition可以定义transform变形的delay time。而transform则是实现动画变化的结果。
![效果图](http://imageshack.com/a/img923/1072/zIXvAR.gif)
```css
* {
    /*这里我设置得比较粗暴。。*/
    transition: all 2.5s;
}

.face:hover~.ear-wrap .ear {
    transform: rotate(-20deg);
}

.face:hover~.ear-wrap .ear.right {
    transform: rotate(20deg);
}

.face:hover .eye-wrap .eye .eye-core {
    height: 60px;
}

.face:hover .eye-wrap .eye .eye-bottom {
    margin-top: 33px;
}

.face:hover .eye-wrap .eye .face-red {
    opacity: .6;
}

.face:hover .mouth {
    border-radius: 0% 40% 50% 50%;
}

.face:hover .mouth.right {
    border-radius: 40% 0% 50% 50%;
}
```

### 04.3D 空间的卡片翻转动效
要完成卡片翻转的效果，这次我用到transform和backface-visibility属性，前者使用里面的rotateY实现围绕Y轴旋转自定义角度，后者用于隐藏（展示）被旋转的元素的背面。