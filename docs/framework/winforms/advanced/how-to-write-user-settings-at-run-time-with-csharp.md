---
title: 如何：在執行階段使用 C# 撰寫使用者設定
ms.date: 03/30/2017
helpviewer_keywords:
- application settings [Windows Forms], run time
- application settings [Windows Forms], writing user settings
- application settings [Windows Forms], C#
ms.assetid: 9d061c7d-b33b-470f-a36d-edccb1d6f9a3
ms.openlocfilehash: f289b6a6a4a726ffa6bb2c9df99c665e2872e8d5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-write-user-settings-at-run-time-with-c"></a>如何：在執行階段使用 C# 撰寫使用者設定 #
應用程式範圍的設定是唯讀的，並只能在設計階段變更，或藉由更改應用程式工作階段之間的 .config 檔案變更。 不過，使用者範圍的設定可以在執行階段撰寫，就如同您變更任何屬性值一樣。 新的值在應用程式工作階段期間保存。 您可以藉由呼叫 Save 方法在應用程式工作階段之間保存設定的變更。  
  
### <a name="how-to-write-and-persist-user-settings-at-run-time-with-c"></a>如何：在執行階段使用 C# 撰寫和保存使用者設定  
  
1.  存取設定，並指派新值，如本範例所示：  
  
    ```  
    // C#  
    Properties.Settings.Default.myColor = Color.AliceBlue;  
    ```  
  
2.  如果您想要在應用程式工作階段之間保存變更的設定，請呼叫 Save 方法，如本範例所示：  
  
    ```  
    // C#  
    Properties.Settings.Default.Save();  
    ```  
  
     使用者設定會儲存在使用者的本機隱藏應用程式儲存資料夾的子資料夾內。  
  
## <a name="see-also"></a>另請參閱  
 [使用應用程式設定和使用者設定](../../../../docs/framework/winforms/advanced/using-application-settings-and-user-settings.md)  
 [操作說明：在執行階段使用 C# 讀取設定](../../../../docs/framework/winforms/advanced/how-to-read-settings-at-run-time-with-csharp.md)  
 [應用程式設定概觀](../../../../docs/framework/winforms/advanced/application-settings-overview.md)
