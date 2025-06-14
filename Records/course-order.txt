标题：[Godot 2D游戏开发 - Godot 2D Academy: Master 2D Games with Godot 4 and GDScript](https://www.bilibili.com/video/BV1RaQcYhE2n)

以下是本人的梳理和对自己不熟悉的内容的记录

一，什么是Godot？Godot的编辑器如何调整和如何使用？
（课时：1~7）
  略
二，GDScript的语法是什么？
（课时：1~8；1~12；1~7）
  1~8：
    4：STRING.find(a) 返回a在字符串的位置
      STRING.contains(a) 返回a是否存在于字符串的布朗值
      (注：Godot中，in操作符在这种情况下和contains是等价的，详见官方文档）
    5：拥有阅读官方内置文档并理解它的能力非常重要！
      按下F1能够查阅文档
    6：and == &&; or == ||; not == !（意思是它们的使用是等价的）
    7：重点，Godot的变量和函数等是能够指定静态类型的，我强烈推荐使用它以防止某些有关数据类型的错误发生
      静态类型有：int, float, String, bool, void...
      使用：:= 赋值会让Godot自行根据初始值的类型给予静态类型
    8：重点，export关键字
      @export var variable 这个变量就会显示在Godot脚本编辑器的栏中，支持暂时修改并重置
      @export_category("NAME") NAME就会作为分割线的文字，用以使导出的变量在编辑器中更加的可读
