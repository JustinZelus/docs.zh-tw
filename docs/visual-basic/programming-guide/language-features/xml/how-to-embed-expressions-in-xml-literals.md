---
title: 如何：將運算式內嵌在 XML 常值中 (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 41dc6ef8d2ec2ffd6cd1cf793911f2e09f1a1e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a>如何：將運算式內嵌在 XML 常值中 (Visual Basic)
您可以使用內嵌的運算式，來建立 XML 文件、 片段或包含在執行階段建立的內容項目結合 XML 常值。 下列範例會示範如何使用內嵌的運算式來填入項目內容、 屬性和項目名稱，在執行階段。  
  
 內嵌運算式的語法是`<%=` `exp` `%>`，這是相同的語法，[!INCLUDE[vstecasp](~/includes/vstecasp-md.md)]使用。 如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。  
  
 您也可以使用[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]Api 來建立[!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]物件。 如需詳細資訊，請參閱<xref:System.Xml.Linq.XElement>。  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-insert-text-as-element-content"></a>若要為項目內容中插入文字  
  
-   下列範例示範如何插入文字中包含`contactName`變數之間的開頭和結尾名稱項目。  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     這個範例會產生下列輸出：  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a>將文字插入做為屬性值  
  
-   下列範例示範如何插入文字中包含`phoneType`變數的值作為`type`屬性。  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     這個範例會產生下列輸出：  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a>若要插入項目名稱的文字  
  
-   下列範例示範如何插入文字中包含`elementName`變數做為項目的名稱。  
  
     當使用這項技術建立的項目，您必須關閉它們與\</ > 標記。  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     這個範例會產生下列輸出：  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a>另請參閱  
 [如何：建立 XML 常值](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [XML 中內嵌的運算式](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)
