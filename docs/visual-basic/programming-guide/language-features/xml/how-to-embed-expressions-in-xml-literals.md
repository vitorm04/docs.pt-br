---
title: Como inserir expressões em literais XML (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 41dc6ef8d2ec2ffd6cd1cf793911f2e09f1a1e77
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33652263"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="dfced-102">Como inserir expressões em literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dfced-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="dfced-103">Você pode combinar literais XML com expressões incorporadas para criar um documento XML, fragmento ou elemento que contém o conteúdo criado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dfced-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="dfced-104">Os exemplos a seguir demonstram como usar expressões inseridas para preencher os nomes de elementos, atributos e conteúdo de elemento em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="dfced-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="dfced-105">A sintaxe para uma expressão inserida é `<%=` `exp` `%>`, que é a mesma sintaxe que [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] usa.</span><span class="sxs-lookup"><span data-stu-id="dfced-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="dfced-106">Para obter mais informações, consulte [expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="dfced-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="dfced-107">Você também pode usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs para criar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="dfced-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="dfced-108">Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="dfced-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="dfced-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="dfced-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="dfced-110">Para inserir texto como conteúdo de elemento</span><span class="sxs-lookup"><span data-stu-id="dfced-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="dfced-111">O exemplo a seguir mostra como inserir o texto que está contido no `contactName` variável entre os nomes de elementos de abertura e fechamento.</span><span class="sxs-lookup"><span data-stu-id="dfced-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     <span data-ttu-id="dfced-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="dfced-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="dfced-113">Para inserir texto como um valor de atributo</span><span class="sxs-lookup"><span data-stu-id="dfced-113">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="dfced-114">O exemplo a seguir mostra como inserir o texto que está contido no `phoneType` variável como o valor da `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="dfced-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     <span data-ttu-id="dfced-115">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="dfced-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="dfced-116">Para inserir texto para um nome de elemento</span><span class="sxs-lookup"><span data-stu-id="dfced-116">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="dfced-117">O exemplo a seguir mostra como inserir o texto que está contido no `elementName` variável como o nome de um elemento.</span><span class="sxs-lookup"><span data-stu-id="dfced-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="dfced-118">Ao criar elementos usando essa técnica, você deve fechá-los com o \</ > marca.</span><span class="sxs-lookup"><span data-stu-id="dfced-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     <span data-ttu-id="dfced-119">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="dfced-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="dfced-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dfced-120">See Also</span></span>  
 [<span data-ttu-id="dfced-121">Como criar literais XML</span><span class="sxs-lookup"><span data-stu-id="dfced-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)  
 [<span data-ttu-id="dfced-122">Expressões Inseridas no XML</span><span class="sxs-lookup"><span data-stu-id="dfced-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [<span data-ttu-id="dfced-123">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="dfced-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="dfced-124">XML</span><span class="sxs-lookup"><span data-stu-id="dfced-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
