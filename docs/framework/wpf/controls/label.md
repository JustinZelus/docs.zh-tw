---
title: "標籤 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "AutoGeneratedOrientationPage"
helpviewer_keywords: 
  - "控制項 [WPF], 標籤"
  - "Label 控制項 [WPF]"
ms.assetid: 241c1ce2-60f8-4613-a0ec-9b9bb25fb6af
caps.latest.revision: 66
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 66
---
# 標籤
<xref:System.Windows.Controls.Label> 控制項通常會在[!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] 中提供資訊。  在過去，<xref:System.Windows.Controls.Label> 只能包含文字，但由於 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 隨附的 <xref:System.Windows.Controls.Label> 是 <xref:System.Windows.Controls.ContentControl>，因此可以包含文字或 <xref:System.Windows.UIElement>。  
  
 <xref:System.Windows.Controls.Label> 可為便捷鍵提供功能和視覺支援。  它常用來啟用快速鍵盤存取像是 <xref:System.Windows.Controls.TextBox> 之類的控制項。  若要將 <xref:System.Windows.Controls.Label> 指派給 <xref:System.Windows.Controls.Control>，請將 <xref:System.Windows.Controls.Label.Target%2A?displayProperty=fullName> 屬性設為使用者按下便捷鍵時應取得焦點的控制項。  
  
 下圖顯示 <xref:System.Windows.Controls.Label> "Themes"，其以 <xref:System.Windows.Controls.ComboBox> 為目標。  當使用者按下時，<xref:System.Windows.Controls.ComboBox> 就會接收焦點。  如需詳細資訊，請參閱 [How to: Set the Target Property of a Label](http://msdn.microsoft.com/zh-tw/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)。  
  
 ![顯示用法所標記的屬性顯示](../../../../docs/framework/wpf/controls/media/labeledby.JPG "LabeledBy")  
  
## 在本節中  
 [How to: Set the Target Property of a Label](http://msdn.microsoft.com/zh-tw/b24c6977-ebcb-4855-a9bb-3fd4435af8f8)  
  
## 參考  
 <xref:System.Windows.Controls.Label>