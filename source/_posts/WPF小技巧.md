---
title: WPF小技巧
date: 2018-08-05 13:24:43
author: SongJF
categories: Windos桌面应用
tags: 
    - WPF
    - 小技巧
---

## 使用数据绑定

- 理解
  
  数据绑定就是把两个元素、对象等的某个属性连接在一起，一变俱变，保持同步

- 使用 将文本框的内容绑定至滑动条上

  - xaml

    ``` xaml
     <TextBox Height="20" Margin="0,0,10,87" Text="{Binding ElementName=slider1,Path=Value}" BorderThickness="1"/>
     <Slider Maximum="100" Margin="0,50,0,35" Name="slider1"/>
    ```

  - cs

    ``` cs
     this.textbox1.SetBinding(TextBox.TextProperty, new Binding("Value") { ElementName = slider1.Name,Mode=BindingMode.TwoWay});
    ```

[参考](https://www.cnblogs.com/lelehellow/p/6215499.html)

## 使用字符串资源

- 在.CS文件中

  - 引用
    `using System.Resources;`
  - 使用
    `Properties.Resources.字符串名`

- 在.xaml文件中

  - 引用

  - 使用

## ContentControl

  `ContentControl`是WPF中的数据模板，利用它可以帮助我们动态的变更控件

- 使用

  - 