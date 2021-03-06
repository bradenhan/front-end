# 图片 
#### 切片
切片结果需满足：最大程度的符合设计稿效果；尽可能小的文件大小。
网页中所有和内容无关的装饰性的图片都应该使用背景图片或图片字体；而和内容有关的图片都不得使用背景图。

在切片时，如遇到内容/广告等图片，可以使用公用的示例图片：  
![](https://bradenhan.gitbooks.io/front-end/content/img/photo.jpg)  
http://test.svn.fengniao.com/frontend_svn/fengniao/common-pic/photo.jpg

#### 图片格式 
网页中所有的图片应使用 PNG-8、 PNG-24、 GIF 、 JPEG 和 `base64` 格式。

| 格式 | 扩展名| 特点、使用场景和注意事项 |
| -- | --| -- |  
| `PNG-8` | .png |  默认使用的格式，支持透明，只支持 256 种颜色索引，几乎所有的切片图片都应使用此格式。PNG格式在部分版本 Chrome浏览器下有 BUG，在拼图时有时需要适当留有间距。|
| `PNG-24` | .png  | 支持 8 位 256 级透明度。主要用于有半透明效果的图片。| 
| `GIF` | .gif |  和 PNG-8 类似，但在多数时候文件稍大（像素图通常比 PNG-8 小），而兼容性最好。GIF 支持多帧动画，在需要动画图片时，或同样的图片文件比 PNG-8 尺寸较小时使用此格式。| 
| `JPEG` | .jpg | 不支持透明色。用于色彩较为丰富、需要过渡自然的大幅面Banner。JPEG 是有损压缩格式，因此在输出时请选择一个最能满足设计效果而文件大小又最小的压缩率| 
| `base64` | data:image/jpeg;base64 | H5页面用的较多 [转换地址](http://tool.css-js.com/base64.html) |

#### 使用 CSS3 和 IE 滤镜、空标签代替图片
在 CSS3 和 IE 滤镜都能达到设计效果时，使用它们来代替图片。这些方式能减少网络载入时间，并易于修改。可斟酌不同的项目适当采用。

#### Sprites
CSS Sprites 是在当前宽带互联网条件下，为了减少 HTTP 请求数量，降低对服务器压力，提高页面加载速度而使用的一项技术。
> CSS Sprites 核心是将多个装饰背景图片组合到一张图片上，然后使用 CSS 的 background-position 来控制需要显示的部分。

CSS Sprites 在使用不当时可能造成维护麻烦、占有太多的客户端内存、颜色失真、显示临近图片内容等问题。
> 图片在客户端通常会先初始化为 Bitmap 对象，然后进行渲染、显示，所以其占用内存计算方式为图片的 高*宽*4，而一张 4000*3000 的图片将占用客户端 45M 的内存——这在开发移动终端网页时尤为需要注意。

基于以上特点，使用 CSS Sprites 应遵循以下规范：
* 图标：将实际位于左侧的图标放在右侧，而实际位于右侧的图标放在左侧，而多个图标尽量错位排列；但是对于不定宽度的容器内的右侧图标除外。
* 为图标留出适量的空白，除非确定图标只在尺寸和该图标完全一致的固定容器中显示。
* 尽量不使用 background-position 的 right 或 bottom 来定位，因为当拼图需要修改尺寸时它们将失效；但是对于不定宽度的容器内的右侧图标除外。
* 当网页中的各种背景和装饰性图标颜色较为丰富，超过 256 色所能表现而需要将图片进行拆分。拆分时将颜色相近或相同的元素拼接在一张图片内，这将减少颜色索引数，从而减少文件大小；也能在 256 色的范围内提供更为丰富的颜色表现。 
* 避免拼图尺寸过大。
* 避免单张拼图文件过大，单张图片大小应不大于 20KB。当需要拆分时，按照颜色相近、元素类型相近和网页屏幕占用的规则来进行。

#### 优化
所有的图片结果在文件较大时应进行优化（小于 1.5KB 时不需要），在保证达到设计效果的情况下达到最小的文件大小。
> 在使用 Photoshop CS 存储为 WEB 使用格式时，默认保存了大量的元数据。这会是输出的图片文件增加 1-2KB。 在输出无法利用优化的图片时， 请保证下图所示的选项选择为“无”：


** 如下图：**
![](https://bradenhan.gitbooks.io/front-end/content/img/PS-pic.png)

 
 