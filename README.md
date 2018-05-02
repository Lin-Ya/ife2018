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
