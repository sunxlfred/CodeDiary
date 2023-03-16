### from  老郭

#### 等值线绘制逻辑
1. 先读入格点数据（绿圈圈），再找等值线点（红十字），连接等值点（红线），平滑等值线绘图（兰线）。具体怎么做呢?看书去吧…
2. 等值线标注转转，与纬圈平行，跟填图规范一致了
3. 气象站点数据，经Micaps数据处理程序处理后，会将各种要素插值（关于插值，以后有时间再讲讲）到规则网格点上，生成格点数据，即Micaps第4类格式数据。利用格点数据，参考大师的算法，http://local.wasp.uwa.edu.au/~pbourke/papers/conrec/，生成等值线，老外的文章写的很详细，并附有各种语言的代码，1987年的文章，真是让人感动加佩服。
4. 可惜此等值线分析仅完成等值线插值及查找过程，并未对等值线进行追踪，无法对等值线进行平滑操作。
等值线平滑一般采用样条平滑。抹角平滑，把小于45度的角都削掉
5. 等值线追踪，过程还是挺复杂的，目前FreeMicaps的等值线追踪效率还不是太高，
6. 扩展了leaflet的GeoJson类，实现等值线填色及高低中心标注

#### gis发展
1. 在.NET里，就是用Graphics类的方法，在窗口中绘制点、线、面、标准、栅格等，组合起来，就是一张地图（瓦片图方式除外）。
2. 早些年Flash流行的时候用Flex实现过一部分功能，后来借助html5的canvas，还有wpf（.net的绘制框架），实现了基本的webgis（中间还用opengl实现过）。但技术更新很快，基于瓦片图的webgis大为流行，速度、效果堪称完美。不再重新发明轮子了，直接用成熟的开源webgis框架，气象数据使用canvas绘制叠加，开发容易了不少。
#### 项目曾用到的框架/插件
   1. leaflet,
   2. protobuf, 数据传输框架
   3. axios,
   4. moment,类似dayjs，时间格式工具类
   5. layui,后端快速开发前端的ui库
   6. html2canvas 前端生成分享图
   7.  使用webpack打包，使用babel进行es6转换，部分使用了typescript

