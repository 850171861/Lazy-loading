## 什么是懒加载？

#### 图片懒加载是优化技术。图片一般存储在服务器中和普通静态资源一样，是一种网络资源，在被请求时也与普通静态资源一样，当图片单位越大将占用网络的带宽资源越多，当一个页面一次性将整个页面的所有图片加载完，将大大增加页面的首屏加载时间。解决方法，当图片位置在浏览器当前视窗内出现时才加载该图片，达到减少图片请求数的技术就被称为图片懒加载。

## 优化前

#### 打开网页直接加载全部图片(8 张)![16190131421.jpg](http://www.wudongming.com:3001/20210421/081bdbc5-046c-42ef-8f5d-8466623ce8e7.jpg)

## 优化后

#### 打开网页只当前视窗内图片(2 张)

![3.jpg](http://www.wudongming.com:3001/20210421/7bd9e7e6-9989-4737-b215-7395d8ea81b5.jpg)

#### 1、红色为已经请求加载的图片(在当前视窗内)

#### 2、蓝色还没有请求加载的图片

![4.jpg](http://www.wudongming.com:3001/20210421/39f7c0d8-6a59-4d59-802b-c6ea61db8331.jpg)

#### 接下来往向下滚动让未加载的图片出现在当前视窗内进行加载

#### 当前第三张图片已经出现在当前视窗，图片进行了加载

![23.jpg](http://www.wudongming.com:3001/20210421/00567a3e-8ea8-461d-a349-c19ab4c000e6.jpg)
![33.jpg](http://www.wudongming.com:3001/20210421/c766f019-e98f-4bc4-a2f2-778e50f0435f.jpg)

## 现实方法

### 1、获取文档高度

> document.documentElement.clientHeight

### 2、获取 img 的所有元素

> document.querySelectorAll

### 3、获取 img 元素相的位置

> getBoundingClientRect()

### 4、当 img 元素的位置 top 小于当前可见的高度就创建 img 标签

> var img = new Image();

### 5、img 标签在当前的可见的视图高度里添加 src

> img.src = "https://img.png"

### 6、事件在图片加载完成后立即执行

```javascript
img.onload = function () {
  item.src = img.src
}
```

### 7、每次滚动触发 执行以上操作

```javascript
document.addEventListener('scroll', function() {
    这里执行1-6的操作
})
```
