---
title: 命名資源
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- names [.NET Framework], localized resources
- localization, naming guidelines
- resource names
- global applications, naming guidelines
- international applications, naming guidelines
ms.assetid: 8b0e97f3-7877-44fd-bc76-e05d36d5d79c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b7cfda4e6a340d040de02903b9b64f0339751c5c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="naming-resources"></a>命名資源
因為好像屬性，可以透過特定的物件參考可當地語系化的資源，資源命名方針如下屬性指導方針。  
  
 **✓ 不要**PascalCasing 用於資源索引鍵。  
  
 **✓ 不要**提供描述性的而不是簡短的識別項。  
  
 **X 不**使用主要的 CLR 語言的語言特有的關鍵字。  
  
 **✓ 不要**使用只使用英數字元和底線命名資源。  
  
 **✓ 不要**下列命名慣例用於例外狀況訊息的資源。  
  
 例外狀況型別名稱加上例外狀況的簡短的識別項，應該使用的資源識別碼：  
  
 `ArgumentExceptionIllegalCharacters`  
 `ArgumentExceptionInvalidName`  
 `ArgumentExceptionFileNameIsMalformed`  
  
 *部分 © 2005年，2009 Microsoft Corporation。All rights reserved.*  
  
 *皮耳森教育，inc.從權限所印製[Framework 設計方針： 慣例、 慣用語和可重複使用.NET 程式庫，第 2 版的模式](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619)Krzysztof Cwalina 並 Brad Abrams，發行 2008 年 10 月 22 日由Addison Wesley Professional，做為 Microsoft Windows 程式開發系列的一部分。*  
  
## <a name="see-also"></a>另請參閱  
 [Framework 設計方針](../../../docs/standard/design-guidelines/index.md)  
 [命名方針](../../../docs/standard/design-guidelines/naming-guidelines.md)
