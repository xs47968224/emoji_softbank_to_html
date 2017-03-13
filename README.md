# emoji_softbank_to_html
jQuery 识别 emoji softbank 编码并转html


===============

我的情况：
 + 微信公众号开发时，读取用户昵称，部份用户昵称中添加emoji表情，存储到utf8数据库中，是无法插入数据的，因为本案中base64_encode处理存储，能读取出来，但还是无法识别的编码
 + Unified 编码的 css 样式和图片是在其它git项目中找到的: [https://github.com/iamcal/php-emoji](https://github.com/iamcal/php-emoji)
 + 由于不太适配自己的项目，太过复杂，如果硬加到自己的项目中，改动太多，成本太高，看到项目中有CSS和原图，自己考虑了下，还是觉得前端处理更恰当。

---------------

适用情况:
 + web页面中存在 softbank emoji 表情编码，前端无法正常显示emoji

---------------

原理：(通过原理，你可以改写成其它编码转 unified, 最终输出emoji表情图片)
 + 1. 找到 emoji Softbank 编码 对应 Unified 编码 [http://www.oicqzone.com/tool/emoji/](http://www.oicqzone.com/tool/emoji/)：随便找了个站，从这上面找到300多个对应表情。
 + 2. 如果需要其它对应编码关系，也可以写个脚本把[http://www.oicqzone.com/tool/emoji/](http://www.oicqzone.com/tool/emoji/)页面中你所需要的对应关系抓下来，然后改写 emojiConvert.js 中的数组 key
 + 3. 通过jQuery正则识别Softbank emoji 表情编码，并将编码转换能指定样式的html

---------------

PS:
 + 包里有emoji.png,是表情包原图，由于原文件7M多，太大，转了一张小一点的jpg图片，如果觉得精度不够，需要其它尺寸，请自行使用原图转换

---------------
使用
 + 在需要转换emoji编码的html外套上加上 class="emoji_nickname" 或 其它你想设置的样式标签, 具体参考 test.html 中代码
```html
 <!-- jQuery (necessary for Bootstrap's JavaScript plugins) -->
 <script src="https://cdn.bootcss.com/jquery/1.12.4/jquery.min.js"></script>
 <!--emoji Convert-->
 <link href="emoji.css" rel="stylesheet">
 <script src="emojiConvert.js"></script>
 <script type="text/javascript">
 	jQuery(document).ready(function($) {
 		// 查找指定样式标签，检测 softbank 编码
 		$('.emoji_nickname').emojiConvert();
 	});
 </script>
```
---------------

