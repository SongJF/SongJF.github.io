---
title: MaterialDesign使用心得
date: 2018-08-07 00:28:21
author: SongJF
categories: Windos桌面应用
tags: 
  - WPF
  - 小技巧
---

由于`MaterialDesign`的丰富特性，加之其并没有多少中文说明文档，所以我只好摸着官方Demo一步一步慢慢踩坑了...

<!-- more-->

## 双选的Dialog

- Dialog外套 `<materialDesign:DialogHost HorizontalAlignment="Center" VerticalAlignment="Center" DialogClosing="DialogHost_DialogClosing"/>`

  其中 `DialogClosing` 处理对话框关闭后的事务

- Dialog内容 `<materialDesign:DialogHost.DialogContent>`
  
  在里面赛一个`<StackPanel>`或者其他什么框架然后就可以随便填充内容了

- 消息传递(在`DialogClosing`中获取信息)
  
  - 通过`x:Name`在xaml绑定控件再在逻辑层获取信息

  - 在主窗口引用名称空间`xmlns:system="clr-namespace:System;assembly=mscorlib"`

  ``` xaml
  <Button.CommandParameter>
      <system:Boolean>True</system:Boolean>
  </Button.CommandParameter>
  ```

  然后通过`DialogClosing`对应方法的参数`eventArgs`获取信息 如上例在逻辑层中通过`eventArgs.Parameter`获得按钮点击状态

- 打开Dialog
  
  使用命令`Command="{x:Static materialDesign:DialogHost.OpenDialogCommand}"`

- 关闭Dialog

  通过为控件添加`Command="materialDesign:DialogHost.CloseDialogCommand"`命令关闭对话框 例如
  
  `<Button Style="{StaticResource MaterialDesignFlatButton}" Command="materialDesign:DialogHost.CloseDialogCommand">`