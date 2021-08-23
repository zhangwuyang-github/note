# 重排重绘

重排由CPU控制，重绘由GPU控制。CPU的处理速度远不如GPU。

# 优化

- 可以将容易发生重排重绘的元素单独触发渲染层，与其他静态元素隔离，也就是GPU(硬件)加速。

  ```css
  transform: translateZ(0);
  backface-visibility: hidden;
  ```

- CSS属性读写分离；避免读写两者交叉使用，尽量不使用js操作样式，通过切换class来改变样式。

- 图片渲染前就指定大小。