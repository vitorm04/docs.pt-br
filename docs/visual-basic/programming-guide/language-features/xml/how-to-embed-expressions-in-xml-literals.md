---
title: 'Como: Inserir expressões em literais XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: fba33bc177641f3fc9f67b1a82919a44d28a11cf
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54681775"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="3a3a4-102">Como: Inserir expressões em literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a3a4-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="3a3a4-103">Você pode combinar literais XML com expressões incorporadas para criar um documento XML, fragmento ou elemento que contém o conteúdo criado no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3a3a4-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="3a3a4-104">Os exemplos a seguir demonstram como usar expressões inseridas para preencher os nomes de elementos, atributos e conteúdo do elemento no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="3a3a4-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="3a3a4-105">É a sintaxe para uma expressão inserida `<%=` `exp` `%>`, que é a mesma sintaxe que [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] usa.</span><span class="sxs-lookup"><span data-stu-id="3a3a4-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that [!INCLUDE[vstecasp](~/includes/vstecasp-md.md)] uses.</span></span> <span data-ttu-id="3a3a4-106">Para obter mais informações, consulte [expressões inseridas no XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="3a3a4-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="3a3a4-107">Você também pode usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs para criar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="3a3a4-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="3a3a4-108">Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="3a3a4-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="3a3a4-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="3a3a4-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="3a3a4-110">Para inserir texto como conteúdo do elemento</span><span class="sxs-lookup"><span data-stu-id="3a3a4-110">To insert text as element content</span></span>  
  
-   <span data-ttu-id="3a3a4-111">O exemplo a seguir mostra como inserir o texto que está contido no `contactName` variável entre os nomes de elementos de abertura e fechamento.</span><span class="sxs-lookup"><span data-stu-id="3a3a4-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_1.vb)]  
  
     <span data-ttu-id="3a3a4-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3a3a4-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="3a3a4-113">Para inserir texto como um valor de atributo</span><span class="sxs-lookup"><span data-stu-id="3a3a4-113">To insert text as an attribute value</span></span>  
  
-   <span data-ttu-id="3a3a4-114">O exemplo a seguir mostra como inserir o texto que está contido na `phoneType` variável como o valor do `type` atributo.</span><span class="sxs-lookup"><span data-stu-id="3a3a4-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_2.vb)]  
  
     <span data-ttu-id="3a3a4-115">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3a3a4-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="3a3a4-116">Para inserir texto para um nome de elemento</span><span class="sxs-lookup"><span data-stu-id="3a3a4-116">To insert text for an element name</span></span>  
  
-   <span data-ttu-id="3a3a4-117">O exemplo a seguir mostra como inserir o texto que está contido no `elementName` variável como o nome de um elemento.</span><span class="sxs-lookup"><span data-stu-id="3a3a4-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="3a3a4-118">Ao criar elementos usando essa técnica, você deve fechá-los com o \</ > marca.</span><span class="sxs-lookup"><span data-stu-id="3a3a4-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-embed-expressions-in-xml-literals_3.vb)]  
  
     <span data-ttu-id="3a3a4-119">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="3a3a4-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="3a3a4-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a3a4-120">See also</span></span>
- [<span data-ttu-id="3a3a4-121">Como: Criar literais XML</span><span class="sxs-lookup"><span data-stu-id="3a3a4-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="3a3a4-122">Expressões Inseridas no XML</span><span class="sxs-lookup"><span data-stu-id="3a3a4-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="3a3a4-123">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3a3a4-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="3a3a4-124">XML</span><span class="sxs-lookup"><span data-stu-id="3a3a4-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
