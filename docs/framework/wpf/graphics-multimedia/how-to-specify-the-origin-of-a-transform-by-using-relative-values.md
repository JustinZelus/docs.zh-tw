---
title: 操作說明：使用相對值指定轉換的原點
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: ff263af8fbedeec483eee213c07dd4ec169805de
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a>操作說明：使用相對值指定轉換的原點
此範例示範如何使用相對的值來指定來源的<xref:System.Windows.UIElement.RenderTransform%2A>套用至<xref:System.Windows.FrameworkElement>。  
  
 當旋轉、 縮放或扭曲<xref:System.Windows.FrameworkElement>使用<xref:System.Windows.UIElement.RenderTransform%2A>屬性，預設值的轉換套用至項目的左上角。 如果您想要從元素的中心進行旋轉、縮放或扭曲，您可以將轉換的中心設為元素的中心。 不過，使用此解決方案需要先知道元素的大小。 將轉換套用至的元素中心的更簡單的方法是設定它<xref:System.Windows.UIElement.RenderTransformOrigin%2A>屬性 （0.5，0.5），而不是在本身的轉換上設定之中間值。  
  
## <a name="example"></a>範例  
 下列範例會使用<xref:System.Windows.Media.RotateTransform>旋轉<xref:System.Windows.Controls.Button>順時針旋轉 45 度。 由於範例沒有指定中心，因此按鈕會以點 (0, 0)，也就是左上角為中心旋轉。 <xref:System.Windows.Media.RotateTransform>套用至<xref:System.Windows.UIElement.RenderTransform%2A>屬性。  
  
 下圖顯示後續範例的轉換結果。  
  
 ![使用 rendertransform 經過轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")  
使用 RenderTransform 屬性順時針旋轉 45 度  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 下列範例也會使用<xref:System.Windows.Media.RotateTransform>旋轉<xref:System.Windows.Controls.Button>45 度順時針旋轉; 不過，此範例會設定<xref:System.Windows.UIElement.RenderTransformOrigin%2A>按鈕的 （0.5，0.5）。 因此，旋轉會套用到按鈕的中心，而非左上角。  
  
 下圖顯示後續範例的轉換結果。  
  
 ![對其中心轉換的按鈕](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")  
使用 RenderTransform 屬性搭配 (0.5, 0.5) 的 RenderTransformOrigin 旋轉 45 度  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 如需有關轉換<xref:System.Windows.FrameworkElement>物件，請參閱[轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Media.Transform>  
 [轉換概觀](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [HOW-TO 主題](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
