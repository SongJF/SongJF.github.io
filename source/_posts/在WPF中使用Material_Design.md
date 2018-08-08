---
title: 在WPF中使用Material Design
date: 2018-08-03 16:13:11
author: SongJF
tags: WPF
categories: Windos桌面应用
---

由于WPF自带样式太过233了，我们希望有更好看的UI框架，所以我们这里采用Material Design这个框架

<!--more-->

## 引入包

 在包管理工具中引入`MaterialDesignColors`和`MaterialDesignThemes`


## 引用主题颜色

- 在`App.xaml`中添加引用

   在`<Application.Resources>`中添加

  ``` xaml
    <ResourceDictionary>
      <ResourceDictionary.MergedDictionaries>

        <!--设定主題背景色-->
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Dark.xaml" />
        <!--套用基本控制样式-->
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" />
        <!--设定主色-->
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Primary/MaterialDesignColor.Red.xaml" />
        <!--设定辅色-->
        <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Accent/MaterialDesignColor.Red.xaml" />

      </ResourceDictionary.MergedDictionaries>
    </ResourceDictionary>
  ```

  另一种配色方案

    ``` xaml
    <!-- Material Design -->
    <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Dark.xaml" />
    <ResourceDictionary Source="pack://application:,,,/MaterialDesignThemes.Wpf;component/Themes/MaterialDesignTheme.Defaults.xaml" />
    <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Primary/MaterialDesignColor.bluegrey.xaml" />
    <ResourceDictionary Source="pack://application:,,,/MaterialDesignColors;component/Themes/Recommended/Accent/MaterialDesignColor.DeepPurPle.xaml" />
    ```

- 在`MainPage.xaml`中应用如下更改

  添加 `TextElement.Foreground` 和 `Background` 属性的具体内容

  修改后代码如下

  ``` xaml
  <Window x:Class="ENBpresetAssistant.MainWindow"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        xmlns:local="clr-namespace:ENBpresetAssistant"
        TextElement.Foreground="{DynamicResource MaterialDesignBody}"
        Background="{DynamicResource MaterialDesignPaper}"
        mc:Ignorable="d"
        Title="MainWindow" Height="450" Width="800">
    <Grid>
    </Grid>
  </Window>
  ```

## 更改窗体外观

- 修改`APP.xaml`中的对应内容

  - 在`<ResourceDictionary>`添加笔刷资源

    ``` xaml
    <!-- 加入筆刷資源 -->
    <SolidColorBrush x:Key="HighlightBrush" Color="{DynamicResource Primary700}" />
    <SolidColorBrush x:Key="AccentColorBrush" Color="{DynamicResource Primary500}" />
    <SolidColorBrush x:Key="AccentColorBrush2" Color="{DynamicResource Primary400}" />
    <SolidColorBrush x:Key="AccentColorBrush3" Color="{DynamicResource Primary300}" />
    <SolidColorBrush x:Key="AccentColorBrush4" Color="{DynamicResource Primary200}" />
    <SolidColorBrush x:Key="WindowTitleColorBrush" Color="{DynamicResource Primary700}" />
    <SolidColorBrush x:Key="AccentSelectedColorBrush" Color="{DynamicResource Primary500Foreground}" />
    <LinearGradientBrush x:Key="ProgressBrush" EndPoint="0.001,0.5" StartPoint="1.002,0.5">
        <GradientStop Color="{DynamicResource Primary700}" Offset="0" />
        <GradientStop Color="{DynamicResource Primary300}" Offset="1" />
    </LinearGradientBrush>
    <SolidColorBrush x:Key="CheckmarkFill" Color="{DynamicResource Primary500}" />
    <SolidColorBrush x:Key="RightArrowFill" Color="{DynamicResource Primary500}" />
    <SolidColorBrush x:Key="IdealForegroundColorBrush" Color="{DynamicResource Primary500Foreground}" />
    <SolidColorBrush x:Key="IdealForegroundDisabledBrush" Color="{DynamicResource Primary500}" Opacity="0.4" />
    ```

  - 设置 `Windos` 属性 `WindowStyle` 为 `None`



参考资料:[透過 MATERIAL DESIGN XAML TOOLKIT 讓你的 WPF 應用程式潮又有料]("http://ouch1978.github.io/2017/03/25/material-design-xaml-toolkit/")