---
title: 使用&#39;FileGetObject&#39;而不是&#39;FileGet&#39;的型別引數時&#39;物件&#39;
ms.date: 07/20/2015
ms.assetid: 090b8088-895a-482a-9362-606596bac304
ms.openlocfilehash: 2edb80f6df95774e0ea5a7b51e57925845d7ba75
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="use-39filegetobject39-instead-of-39fileget39-when-using-argument-of-type-39object39"></a>使用&#39;FileGetObject&#39;而不是&#39;FileGet&#39;的型別引數時&#39;物件&#39;
`FileGet` 方法包含類型 `Object`的引數。 `FileGetObject` 應該用於取代 `FileGet` ，以避免模稜兩可。  
  
 請注意， `My.Computer.Filesystem` 所提供的功能比 `FileGet` 或 `FileGetObject`更容易使用和執行。  
  
## <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  將 `FileGet` 取代為 `FileGetObject`。  
  
2.  請將 `Object` 引數轉換為更特定的類型。  
  
## <a name="see-also"></a>另請參閱  
   
 [My.Computer.FileSystem](xref:Microsoft.VisualBasic.FileIO.FileSystem)
