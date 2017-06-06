### 性能优化的方法

1. 减少http请求次数：CSS Sprites, JS、CSS源码压缩、图片大小控制合适；网页Gzip，CDN托管，data缓存 ，图片服务器。
2. 前端模板 JS+数据，减少由于HTML标签导致的带宽浪费，前端用变量保存AJAX请求结果，每次操作本地变量，不用请求，减少请求次数
3. 用innerHTML代替DOM操作，减少DOM操作次数，优化javascript性能。
4. 当需要设置的样式很多时设置className而不是直接操作style。
5. 少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。
6. 避免使用CSS Expression（css表达式)又称Dynamic properties(动态属性)。
7. 图片预加载，将样式表放在顶部，将脚本放在底部  加上时间戳。