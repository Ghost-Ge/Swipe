## Usage
Swipe only needs to follow a simple pattern. Here is an example:

``` html
<div id='slider' class='swipe'>
  <div class='swipe-wrap'>
    <div></div>
    <div></div>
    <div></div>
  </div>
</div>
```

Above is the initial required structure– a series of elements wrapped in two containers. Place any content you want within the items. The containing div will need to be passed to the Swipe function like so:

``` js
window.mySwipe = Swipe(document.getElementById('slider'));
```

I always place this at the bottom of the page, externally, to verify the page is ready.

Also Swipe needs just a few styles added to your stylesheet:

``` css
.swipe {
  overflow: hidden;
  visibility: hidden;
  position: relative;
}
.swipe-wrap {
  overflow: hidden;
  position: relative;
}
.swipe-wrap > div {
  float:left;
  width:100%;
  position: relative;
}

分页圆点
.slider-pager li {
  display: inline-block;
  width: 10px;
  height: 10px;
  border-radius: 10px;
  background: #DDD;
  box-shadow: inset 0 1px 3px black,0 0 1px 1px #202020;
  margin: 0 2px;
  cursor: pointer;
}
.slider-pager li.on {
  box-shadow: inset 0 1px 3px -1px #28b4ea, 0 1px 2px rgba(0,0,0,.5);
  background-color: #1293dc;
  background-image: -webkit-gradient(linear, left top, left bottom, color-stop(0%, #1293dc), color-stop(100%, #0f6297));
  background-image: -webkit-linear-gradient(top, #1293dc, #0f6297);
  background-image: -moz-linear-gradient(top, #1293dc, #0f6297);
  background-image: -ms-linear-gradient(top, #1293dc, #0f6297);
  background-image: -o-linear-gradient(top, #1293dc, #0f6297);
  background-image: linear-gradient(top, #1293dc, #0f6297)
}
```

## Config Options

Swipe can take an optional second parameter– an object of key/value settings:

- **startSlide** Integer *(default:0)* - index position Swipe should start at

-	**speed** Integer *(default:300)* - speed of prev and next transitions in milliseconds.

- **auto** Integer - begin with auto slideshow (time in milliseconds between slides)

- **continuous** Boolean *(default:true)* - create an infinite feel with no endpoints

- **disableScroll** Boolean *(default:false)* - stop any touches on this container from scrolling the page

- **stopPropagation** Boolean *(default:false)* - stop event propagation
 
-	**callback** Function - runs at slide change.

- **transitionEnd** Function - runs at the end slide transition.

### Example

``` html

<div id="slider" class="swipe">
  <div class="swipe-wrap">
    <div style="background:green"></div>
    <div style="background:blue"></div>
    <div style="background:yellow"></div>
  </div>
  <nav>
    <ul class="slider-pager">
      <li class="on"></li>
      <li></li>
      <li></li>
    </ul>
  </nav>
</div>

```

``` js

window.mySwipe = new Swipe(document.getElementById('slider'), {
  startSlide: 2, // 开始的索引
  speed: 400,
  auto: 3000, //自动播放时间
  continuous: true, //是否可以循环滑动
  disableScroll: false, //停止触摸滚动页面
  stopPropagation: false,
  callback: function(index, elem) {
    $(elem).parents('.swipe').find(".slider-pager").find('i').eq(index).addClass('on').siblings().removeClass('on');
  },
  transitionEnd: function(index, elem) {}
});

```

## Swipe API

Swipe exposes a few functions that can be useful for script control of your slider.

`prev()` slide to prev

`next()` slide to next

`getPos()` returns current slide index position

`getNumSlides()` returns the total amount of slides

`slide(index, duration)` slide to set index position (duration: speed of transition in milliseconds)

## Browser Support
Swipe is now compatible with all browsers, including IE7+. Swipe works best on devices that support CSS transforms and touch, but can be used without these as well. A few helper methods determine touch and CSS transition support and choose the proper animation methods accordingly.

## Who's using Swipe
<img src='http://swipejs.com/assets/swipe-cnn.png' width='170'>
<img src='http://swipejs.com/assets/swipe-airbnb.png' width='170'>
<img src='http://swipejs.com/assets/swipe-nhl.png' width='170'>
<img src='http://swipejs.com/assets/swipe-htc.png' width='170'>
<img src='http://swipejs.com/assets/swipe-thinkgeek.png' width='170'>
<img src='http://swipejs.com/assets/swipe-snapguide.png' width='170'>

Shoot me a [note](mailto:brad@birdsall.co) if you want your logo here

## License
Copyright (c) 2013 Brad Birdsall Licensed under the [The MIT License (MIT)](http://opensource.org/licenses/MIT).
