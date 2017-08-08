# jquery banner滑块导航条幻灯片图片轮播切换Carousel1

效果如下:
![](images/img.gif)

all code:
```
<!DOCTYPE html>
<html lang="en">
<head>
	<meta charset="UTF-8">
    <title>jquery banner滑块导航条幻灯片图片轮播切换</title>
    <meta name="description" content="jquery banner幻灯片，设置滑块导航条当鼠标滑过导航条时，导航标签滑动展示，同时切换相应的大图片。支持轮播图片切换的幻灯片特效。" />
	<style>
		*{margin:0;padding:0;list-style-type:none;}
		a,img{border:0;}
		body{font:12px/180% Arial, Helvetica, sans-serif, "新宋体";}
		/* changeBox_a1 */
		.changeBox_a1{position:relative;height:397px;width:732px;overflow:hidden;margin:30px auto;}
		.changeBox_imgs{position:relative;height:354px;width:732px;overflow:hidden;clear:both;}
		.changeBox_imgs_list{position:absolute;width:9999px;}
		.changeBox_imgs_list li{float:left;height:354px;width:732px;}
		/* ul_change */
		.ul_change,.ul_change .arrow_bar{background:url(images/bannerTag.gif) no-repeat;}
		.ul_change{position:relative;width:1000px;height:43px;left:0px;bottom:0px;background-position:0 0;}
		.ul_change .arrow_bar{position:absolute;width:181px;height:34px;background-position:-3px -46px;color:#565253;z-index:8;top:3px;left:3px;cursor:pointer;}
		.ul_change li{display:block;_display:inline-block;float:left;position:relative;width:181px;height:40px;line-height:40px;padding-top:3px;z-index:9;margin:0 84px 0 3px;text-align:center;color:#8F8F8F;font-size:14px;font-weight:bolder;font-family:'微软雅黑','宋体';cursor:pointer;}
	</style>
</head>
<body>
<div id="change_1" class="changeBox_a1">
	<div class="changeBox_imgs">
		<ul class="changeBox_imgs_list">
			<li><a href="javascript:void(0)" target="_blank"><img width="732" height="354" alt="户外摄影" src="images/banner1.jpg" /></a></li>
			<li><a href="javascript:void(0)" target="_blank"><img width="732" height="354" alt="户外摄影" src="images/banner2.jpg" /></a></li>
			<li><a href="javascript:void(0)" target="_blank"><img width="732" height="354" alt="户外摄影" src="images/banner3.jpg" /></a></li>
		</ul>
	</div>
	<ul class="ul_change">
		<li id="changeBox_arrow_bar" class="arrow_bar"></li>
		<li class="tagLi3" idx="1">户外摄影</li>
		<li class="tagLi2" idx="2">户外摄影</li>
		<li class="tagLi1" idx="3">户外摄影</li>
	</ul>     
</div>
</body>
</html>
<script src="js/jquery-1.4.2.min.js"></script>
<script>
	function BannerImages(){
		var b = $("#changeBox_arrow_bar"),
				c = $("ul.ul_change li:not(.arrw_bar)"),
				e = $("ul.changeBox_imgs_list"),
				d = true,
				f = 1;
		var a = function(){
			var j = (732 * f - 732),
					j = j == 0 ? 0 : -j,i = 500;
			e.animate({ left: j + "px" }, i)
		};
		e.find("img").hover(function(){
			clearInterval(h)
		},function(){
			g()
		});
		c.click(function(){
			var j = $(this), i = j.position().left + 3;
			f = j.attr("idx");
			a();
			b.animate({ left: i + "px" },500,function(){
				d = true
			})
		}).mouseover(function(){
			if(!d){
				return
			}
			clearInterval(h);
			d = false;
			$(this).click()
		}).mouseout(function(){
			if(!d){
				return
			}
			g()
		});
		var h = null;
		var g = function(){
			h = setInterval(function(){
				f++;
				if (f > 3){
					f = 1
				}
				c.eq(f).click()
			}, 4000)
		};
		g()
	}
	$(document).ready(function(){
		BannerImages();//Banner滑动效果
	});
</script>






```
