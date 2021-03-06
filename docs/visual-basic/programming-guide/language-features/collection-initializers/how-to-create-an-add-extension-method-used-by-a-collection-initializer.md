---
title: 如何：建立集合初始設定式所使用的 Add 擴充方法 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 5e35ad80037e843fd3cbd9caa68dcb2a09d707e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>如何：建立集合初始設定式所使用的 Add 擴充方法 (Visual Basic)
當您使用集合初始設定式來建立集合時，Visual Basic 編譯器會搜尋`Add`的集合型別的方法的參數`Add`方法符合型別集合初始設定式中的值。 這`Add`方法用來填入集合初始設定式中的值集合。  
  
 如果沒有相符的`Add`方法的存在，您無法修改集合的程式碼，您可以加入擴充方法呼叫`Add`採用所需的集合初始設定式的參數。 這通常是您需要時，您可以使用集合初始設定式的泛型集合。  
  
## <a name="example"></a>範例  
 下列範例示範如何將擴充方法新增至泛型<xref:System.Collections.Generic.List%601>型別，如此集合初始設定式可以用來加入類型的物件`Employee`。 擴充方法可讓您使用簡短的集合初始設定式語法。  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a>另請參閱  
 [集合初始設定式](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [如何：建立集合初始設定式所使用的集合](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
