---
title: 如何：使用 FontSizeConverter 類別
ms.date: 03/30/2017
helpviewer_keywords:
- FontSizeConverter objects [WPF]
- typography [WPF], FontSizeConverter objects
ms.assetid: 3b0592bd-7223-4860-a108-a5d72f3a9178
ms.openlocfilehash: 625beb06b526e2753abc6f982cf5834bfae1f202
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-the-fontsizeconverter-class"></a>如何：使用 FontSizeConverter 類別
## <a name="example"></a>範例  
 這個範例示範如何建立的執行個體<xref:System.Windows.FontSizeConverter>並用它來變更字型的大小。  
  
 此範例會定義自訂的方法呼叫`changeSize`將轉換的內容<xref:System.Windows.Controls.ListBoxItem>定義在個別[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]檔案，以執行個體<xref:System.Double>，及更新版本為<xref:System.String>。 這個方法會傳遞<xref:System.Windows.Controls.ListBoxItem>至<xref:System.Windows.FontSizeConverter>物件，然後將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>的執行個體<xref:System.Double>。 此值接著會傳遞做為值回<xref:System.Windows.Controls.TextBlock.FontSize%2A>屬性<xref:System.Windows.Controls.TextBlock>項目。  
  
 這個範例也會定義呼叫的第二個自訂方法`changeFamily`。 這個方法會將轉換<xref:System.Windows.Controls.ContentControl.Content%2A>的<xref:System.Windows.Controls.ListBoxItem>至<xref:System.String>，然後將傳送至該值<xref:System.Windows.Controls.TextBlock.FontFamily%2A>屬性<xref:System.Windows.Controls.TextBlock>項目。  
  
 此範例不會執行。  
  
 [!code-csharp[FontSizeConverter#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FontSizeConverter/CSharp/Window1.xaml.cs#1)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.FontSizeConverter>
