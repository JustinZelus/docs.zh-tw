---
title: 如何：將 Stretch 屬性套用至 Viewbox 的內容
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- StretchDirection properties [WPF]
- Stretch properties [WPF]
- controls [WPF], Viewbox
- Viewbox control [WPF]
ms.assetid: b9c22ef4-bce4-4300-9e0c-8260b7db83cc
ms.openlocfilehash: 3e81ec9fd045bb3fcf359943e455d2cce94aec55
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-apply-stretch-properties-to-the-contents-of-a-viewbox"></a>如何：將 Stretch 屬性套用至 Viewbox 的內容
## <a name="example"></a>範例  
 這個範例示範如何變更的值<xref:System.Windows.Controls.Viewbox.StretchDirection%2A>和<xref:System.Windows.Controls.Viewbox.Stretch%2A>屬性<xref:System.Windows.Controls.Viewbox>。  
  
 第一個範例會使用[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]定義<xref:System.Windows.Controls.Viewbox>項目。 它會將指派<xref:System.Windows.FrameworkElement.MaxWidth%2A>和<xref:System.Windows.FrameworkElement.MaxHeight%2A>為 400。 範例巢狀放置於<xref:System.Windows.Controls.Image>內的項目<xref:System.Windows.Controls.Viewbox>。 <xref:System.Windows.Controls.Button> 所對應的屬性值的項目<xref:System.Windows.Controls.Viewbox.Stretch%2A>和<xref:System.Windows.Controls.StretchDirection>列舉型別操作巢狀的自動縮放行為<xref:System.Windows.Controls.Image>。  
  
 [!code-xaml[viewboxStretchLayoutSamp#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml#1)]  
  
 下列程式碼後置檔案控制代碼<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.Primitives.ButtonBase.Click>事件，先前[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]範例會定義。  
  
 [!code-csharp[viewboxStretchLayoutSamp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/viewboxStretchLayoutSamp/CSharp/Window1.xaml.cs#2)]
 [!code-vb[viewboxStretchLayoutSamp#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/viewboxStretchLayoutSamp/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Controls.Viewbox>  
 <xref:System.Windows.Media.Stretch>  
 <xref:System.Windows.Controls.StretchDirection>
