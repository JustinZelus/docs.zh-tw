---
title: 如何：將 ToolStrip 移出 ToolStripContainer 並移至表單上
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], parenting to forms
- Windows Forms, parenting ToolStrip controls
ms.assetid: a1c94a7f-6fc5-4e4c-84cf-ff11dc573d33
ms.openlocfilehash: 6cc54264033eca541ce845b75d608087fee8a542
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>如何：將 ToolStrip 移出 ToolStripContainer 並移至表單上
使用下列程序移動<xref:System.Windows.Forms.ToolStrip>超出<xref:System.Windows.Forms.ToolStripContainer>拖曳至表單。  
  
> [!NOTE]
>  根據您目前使用的設定或版本，您所看到的對話方塊與功能表命令可能會與 [說明] 中描述的不同。 若要變更設定，請從 [ **工具** ] 功能表中選取 [ **匯入和匯出設定** ]。 如需詳細資訊，請參閱 [在 Visual Studio 中自訂開發設定](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3)  
  
### <a name="to-move-a-toolstrip-out-of-a-toolstripcontainer-onto-a-form"></a>若要移動 ToolStrip 從 toolstripcontainer 並移至表單  
  
1.  選取 <xref:System.Windows.Forms.ToolStrip>。  
  
2.  剪下<xref:System.Windows.Forms.ToolStrip>藉由按下 CTRL + X，或以滑鼠右鍵按一下<xref:System.Windows.Forms.ToolStrip>選擇**剪下**從內容功能表。  
  
3.  選取的表單。  
  
4.  貼上<xref:System.Windows.Forms.ToolStrip>藉由按下 CTRL + V，或選擇**貼上**從**編輯**功能表。  
  
5.  設定<xref:System.Windows.Forms.ToolStrip.Dock%2A>屬性<xref:System.Windows.Forms.ToolStrip>至**頂端**。  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.ToolStripContainer>  
 [ToolStrip 控制項概觀](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)
