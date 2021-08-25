# React与Vue的不同

- 监听数据变化不同

  Vue使用数据劫持配合发布订阅者模式实现监听数据变化；React通过diff算法来监听数据。原因是设计理念不同，Vue更加简单，React更适合大型应用。

- 数据流不同

  Vue支持双向数据绑定；React单向数据流，提倡数据不可变。

- 组合功能方式不同

  Vue使用mixin，在创建组件实例时隐式封装了；React通过高阶函数实现。

- 模版渲染方式不同

- 框架本质不同

  Vue是MVVM框架；React是前端组件化框架。

# 虚拟Dom

真实dom很庞大，操作频繁会导致性能问题，于是使用Object模拟了真实Dom，再将虚拟Dom通过特定的render方法渲染成真实Dom

# WebPack

## 打包过程

1. 初始化参数：启动构建程序，从配置文件和shell中读取合并配置参数
2. 开始编译：使用参数初始化compile对象，加载所有插件，然后执行run方法进行编译
3. 确定接口：根据entry找出所有的入口文件
4. 编译模块：从入口文件出发，调用对应的loader对每个module进行编译，再找出module依赖的module，递归进行编译
5. 编译完成：编译完所有module后，得到每个模块的内容和其依赖关系
6. 输出资源：根据入口文件和模块之间的依赖关系，组合成一个个chunk，再将每一个chunk转换成一个单独的文件加入到输出列表
7. 完成：根据配置中的output确定输出文件及目录，将文件内容写入到文件系统

# 生命周期

getDefaultProps => getInitialState => componentWillMount => render => componentMount => componentWillReceiveProps => shouldComponentUpdate => componentWillUpdate => render => componentDidUpdate => componentWillOnMount