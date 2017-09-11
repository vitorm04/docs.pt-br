---
title: "Como: inserir expressões em literais XML (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: e4f086b06575cb8300bd65d450cda6b9893bb692
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="ffc84-102">Como inserir expressões em literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffc84-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="ffc84-103">Você pode combinar literais XML com expressões inseridas para criar um documento XML, fragmento ou elemento que contém o conteúdo criado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ffc84-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="ffc84-104">Os exemplos a seguir demonstram como usar expressões inseridas para preencher o conteúdo de elemento, atributos e nomes de elementos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ffc84-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="ffc84-105">A sintaxe para uma expressão inserida é `<%=` `exp` `%>`, que é a mesma sintaxe que [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] usa.</span><span class="sxs-lookup"><span data-stu-id="ffc84-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)] uses.</span></span> <span data-ttu-id="ffc84-106">Para obter mais informações, consulte [expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="ffc84-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="ffc84-107">Você também pode usar o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs para criar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="ffc84-107">You can also use the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs to create [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects.</span></span> <span data-ttu-id="ffc84-108">Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="ffc84-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="ffc84-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="ffc84-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="ffc84-110">Para inserir texto como conteúdo de elemento</span><span class="sxs-lookup"><span data-stu-id="ffc84-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="ffc84-111">O exemplo a seguir mostra como inserir o texto que está contido no `contactName` variável entre os nomes de elementos de abertura e fechamento.</span><span class="sxs-lookup"><span data-stu-id="ffc84-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     <span data-ttu-id="ffc84-112">[!code-vb[VbXMLSamples&#39;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="ffc84-112">[!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="ffc84-113">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="ffc84-113">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="ffc84-114">Para inserir texto como um valor de atributo</span><span class="sxs-lookup"><span data-stu-id="ffc84-114">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="ffc84-115">O exemplo a seguir mostra como inserir o texto que está contido no `phoneType` variável como o valor da `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="ffc84-115">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     <span data-ttu-id="ffc84-116">[!code-vb[40 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="ffc84-116">[!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="ffc84-117">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="ffc84-117">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="ffc84-118">Para inserir texto para um nome de elemento</span><span class="sxs-lookup"><span data-stu-id="ffc84-118">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="ffc84-119">O exemplo a seguir mostra como inserir o texto que está contido no `elementName` variável como o nome de um elemento.</span><span class="sxs-lookup"><span data-stu-id="ffc84-119">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="ffc84-120">Ao criar elementos usando esta técnica, você deve fechá-los com o \</ > marca.</span><span class="sxs-lookup"><span data-stu-id="ffc84-120">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     <span data-ttu-id="ffc84-121">[!code-vb[41 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]</span><span class="sxs-lookup"><span data-stu-id="ffc84-121">[!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]</span></span>  
  
     <span data-ttu-id="ffc84-122">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="ffc84-122">This example produces the following output:</span></span>  
  
    ```  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ffc84-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffc84-123">See Also</span></span>  
 <span data-ttu-id="ffc84-124">[Como: criar literais XML](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md) </span><span class="sxs-lookup"><span data-stu-id="ffc84-124">[How to: Create XML Literals](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md) </span></span>  
<span data-ttu-id="ffc84-125"> [Expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span><span class="sxs-lookup"><span data-stu-id="ffc84-125"> [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md) </span></span>  
<span data-ttu-id="ffc84-126"> [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="ffc84-126"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="ffc84-127"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="ffc84-127"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
