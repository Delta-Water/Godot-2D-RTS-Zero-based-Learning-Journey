# Godot学习之旅

###### 按时间线排序

## 1.27

### 游戏构成

1. 场景 - 节点树
2. 节点 - Object

Gogot认为，游戏是由一个个场景组成的，而一个个场景中的背景、地形、角色，声音，计时器等等都属于节点这一概念

每一个节点都能够拥有自己的脚本，即在节点被创建、添加时会执行的代码，但最多只能绑定一个

这并不意味着其不能编写复杂的代码逻辑，相反，这是一种面向对象编程的体现，通过重写和拓展相关函数的内容，可以很方便的实现复杂的业务需要

### Object中的从属关系

1. Node节点
   1. Node3D - 3D
      - ...
   2. CanvasItem
      1. Node2D - 2D
         - ...
      2. Control - UI
         - ...
2. RefCounted功能类节点
   1. 寻路
   2. 资源加载
   3. ...

我会优先了解`CanvasItem`（其实就是2D）和`RefCounted功能类节点`中的有关知识

### 脚本基础

1. 脚本的几个重要的生命周期方法：
   1. _enter_tree() - 进入树
      - 系统正序调用
   2. _ready() - 所有子节点进入树
      - 系统倒序调用
   3. _process() - 帧
   4. _physics_process() - 物理计算
   5. _exit_tree() - 离开树

请不要在`enter_tree()`中放置涉及和子节点有关的初始化代码，因为此时子节点可能还没有被创建

## 1.31

修订

## 2.1

修订

### 按键输入

###### Input类

1. 鼠标设置 - MouseMode
###### 枚举变量 - MouseModeEnum
   - Visible - 显示（默认）
   - Hidden - 隐藏
   - Captured - 锁定在窗口中心并隐藏
   - Confined - 限制
   - ConfinedHidden - 限制并隐藏

2. 按键输入
###### 放在_process中判断（逐帧判断按键的按下情况）

   - 是否按下某键 is_key_pressed( keycode || Key.KEY_ANY)
   - 按下按键触发 _input(event: InputEvent)
     应当先判断事件类型是否为键盘类型 - InputEventKey
     - 优点：能够判断状态
        - 持续按压 - echo
        - 按下瞬间 - pressed
        - 抬起瞬间 - released
     ```
     # 这是一个可能的示例，但建议使用输入动作来代替
     func _input(event):
	    if event is InputEventKey and event.pressed:
         if event.keycode == KEY_T:
			  print("T was pressed")
     ```
