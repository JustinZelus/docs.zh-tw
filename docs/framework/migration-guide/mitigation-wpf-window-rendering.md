---
title: "風險降低：WPF 視窗呈現 | Microsoft Docs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 28ed6bf8-141b-4b73-a4e3-44a99fae5084
caps.latest.revision: 3
author: rpetrusha
ms.author: ronpet
manager: wpickett
translationtype: Human Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: c911513551e9629a4a6975762c1952c73c50f733
ms.lasthandoff: 04/18/2017

---
# <a name="mitigation-wpf-window-rendering"></a>風險降低：WPF 視窗呈現
在 Windows 8 與更新版本中執行的 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] 多重監視器案例中，如果視窗擴充到單一顯示畫面以外，可呈現完整視窗而不會將其裁剪。  
  
## <a name="impact"></a>影響  
 一般而言，當跨多個監視器時，不裁剪而呈現整個視窗是預期的行為。 不過，在 Windows 7 和舊版中，如果 WPF 視窗超過單一顯示畫面，會將其裁剪，主要是因為要在第二個監視器呈現部分視窗時，會造成顯著的效能影響。  
  
 在 Windows 8 和更新版本中，跨監視器呈現 WPF 視窗的影響涉及太多因素，因此無法精確量化。 在某些情況下，它仍可能會產生不良的效能影響，特別是針對執行使用大量圖形的應用程式並有跨監視器顯示視窗的使用者來說，更是明顯。 在其他情況下，您可能只需要 .NET Framework 版本之間保持一致的行為。  
  
## <a name="mitigation"></a>緩和  
 您可以停用這項變更並還原為先前的行為，即可在超出單一顯示畫面時裁剪 WPF 視窗。 執行這項作業的方法有兩種：  
  
-   您可將 `<EnableMultiMonitorDisplayClipping>` 項目加入應用程式組態檔的 `<appSettings>` 區段，以針對在 Windows 8 或更新版本中執行的應用程式停用或啟用此行為。 例如，下列組態區段會停用呈現時不裁剪的行為：  
  
    ```  
  
    <appSettings>  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
      </appSettings>  
  
    ```  
  
     `<EnableMultiMonitorDisplayClipping>` 組態設定可以為下列兩個值之一：  
  
    -   若要在呈現期間，啟用將視窗裁剪至監視器界限的行為，即為 `true`。  
  
    -   若要在呈現期間，停用將視窗裁剪至監視器界限的行為，即為 `false`。  
  
-   將應用程式啟動時的 <xref:System.Windows.CoreCompatibilityPreferences.EnableMultiMonitorDisplayClipping%2A> 屬性設為 `true`。  
  
## <a name="see-also"></a>另請參閱  
 [執行階段變更](../../../docs/framework/migration-guide/runtime-changes-in-the-net-framework-4-6.md)