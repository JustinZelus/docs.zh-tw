---
title: 如何：顯示命令列引數 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- command-line arguments [C#], displaying
ms.assetid: b8479f2d-9e05-4d38-82da-2e61246e5437
ms.openlocfilehash: 7b9e488e84c78c8fdbf64431f42ea5797fdca916
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-command-line-arguments-c-programming-guide"></a>如何：顯示命令列引數 (C# 程式設計手冊)
提供給命令列上可執行檔的引數，可以透過 `Main` 的選擇性參數來存取。 引數是以字串陣列的形式提供。 陣列的每個項目都包含一個引數。 引數之間的空白字元會被移除。 例如，請考慮這些虛擬可執行檔的命令列引動過程：  
  
|命令列上的輸入|傳遞至 Main 的字串陣列|  
|----------------------------|-------------------------------------|  
|**executable.exe a b c**|"a"<br /><br /> "b"<br /><br /> "c"|  
|**executable.exe one two**|"one"<br /><br /> "two"|  
|**executable.exe "one two" three**|"one two"<br /><br /> "three"|  
  
> [!NOTE]
>  在 Visual Studio 中執行應用程式時，您可以在[專案設計工具、偵錯頁](/visualstudio/ide/reference/debug-page-project-designer)中指定命令列引數。  
  
## <a name="example"></a>範例  
 此範例顯示傳遞至命令列應用程式的命令列引數。 所顯示的輸出是上表中的第一個項目。  
  
 [!code-csharp[csProgGuideMain#9](../../../csharp/programming-guide/inside-a-program/codesnippet/CSharp/how-to-display-command-line-arguments_1.cs)]  
  
## <a name="see-also"></a>請參閱  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [使用 csc.exe 建置命令列](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)  
 [Main() 和命令列引數](../../../csharp/programming-guide/main-and-command-args/index.md)  
 [如何：使用 foreach 存取命令列引數](../../../csharp/programming-guide/main-and-command-args/how-to-access-command-line-arguments-using-foreach.md)  
 [Main() 傳回值](../../../csharp/programming-guide/main-and-command-args/main-return-values.md)
