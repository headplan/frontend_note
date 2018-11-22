# Navbar

响应式水平导航 , 可以支持图像、链接、按钮和下拉菜单 .

**组件结构**

* `navbar` - 主容器
  * `navbar-brand` - 居左侧 , 始终可见 , 其中通常包含徽标和可选的一些链接或图标 . 
    * `navbar-burger` - 汉堡包图标 , 主要用于切换触摸设备上的导航栏菜单 . 
  * `navbar-menu` - 居右侧 , 隐藏在触摸设备上 , 桌面上可见 . 
    * `navbar-start` - 菜单的左侧部分 , 显示在桌面上的navbar-brand旁边 . 
    * `navbar-end` - 菜单的右侧部分 , 它出现在导航栏的末尾 . 
      * `navbar-item` - 导航栏中的每个项目 , 可以是`a`或`div`标签
        * `navbar-link` - 带有箭头的下拉菜单的同级链接 . 
        * `navbar-dropdown` - 下拉菜单 , 其中可以包括导航的项目和分隔线 . 
          * `navbar-divider` - 用于分隔导航项的水平线 . 



