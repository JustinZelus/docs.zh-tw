---
title: 如何：指定腳本動畫之間的傳遞行為
ms.date: 03/30/2017
helpviewer_keywords:
- Storyboards [WPF], handoff behavior between animations
- animation [WPF], handoff behavior between
ms.assetid: 97bd6842-929b-49d9-813e-46553ae46472
ms.openlocfilehash: c4728dc1cb4eeeff55e533b8d91e4512d9cc1d94
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-handoffbehavior-between-storyboard-animations"></a>如何：指定腳本動畫之間的傳遞行為
這個範例示範如何指定分鏡腳本動畫之間的遞移式行為。 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>屬性<xref:System.Windows.Media.Animation.BeginStoryboard>指定新動畫已套用至屬性的現有與互動。  
  
## <a name="example"></a>範例  
 下列範例會建立兩個按鈕放大滑鼠游標移到上面時，會變小，當資料指標移開。 如果您將滑鼠移 按鈕，然後快速移除資料指標，第一個完成之前，將會套用第二個動畫。 您可以看到之間的差異如下重疊的兩個動畫時<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>值<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>和<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>。 值為<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>結合造成平穩動畫時的值之間的重疊動畫<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>使新的動畫，若要立即取代先前重疊的動畫。  
  
 [!code-xaml[timingbehaviors_snip#HandoffBehaviorWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_snip/CSharp/HandoffBehaviorExample.xaml#handoffbehaviorwholepage)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
 <xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>  
 [動畫概觀](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [動畫和計時](http://msdn.microsoft.com/library/7d83765b-d5ae-41b1-b423-80206e1124aa)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)
