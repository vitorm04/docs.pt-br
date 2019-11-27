---
title: Como inserir expressões em literais XML
ms.date: 07/20/2015
helpviewer_keywords:
- embedded expressions [Visual Basic]
- XML literals [Visual Basic], embedded expressions
ms.assetid: 75016fad-0141-42de-8564-5051be29487e
ms.openlocfilehash: 2e8dd10b334b0271e3c9de11ed155c9d5d7aae48
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332937"
---
# <a name="how-to-embed-expressions-in-xml-literals-visual-basic"></a><span data-ttu-id="a0b19-102">Como inserir expressões em literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a0b19-102">How to: Embed Expressions in XML Literals (Visual Basic)</span></span>
<span data-ttu-id="a0b19-103">Você pode combinar literais XML com expressões inseridas para criar um documento XML, fragmento ou elemento que contém o conteúdo criado em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a0b19-103">You can combine XML literals with embedded expressions to create an XML document, fragment, or element that contains content created at run time.</span></span> <span data-ttu-id="a0b19-104">Os exemplos a seguir demonstram como usar expressões inseridas para popular o conteúdo do elemento, os atributos e os nomes de elementos em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="a0b19-104">The following examples demonstrate how to use embedded expressions to populate element content, attributes, and element names at run time.</span></span>  
  
 <span data-ttu-id="a0b19-105">A sintaxe de uma expressão inserida é `<%=` `exp` `%>`, que é a mesma sintaxe que o ASP.NET usa.</span><span class="sxs-lookup"><span data-stu-id="a0b19-105">The syntax for an embedded expression is `<%=` `exp` `%>`, which is the same syntax that ASP.NET uses.</span></span> <span data-ttu-id="a0b19-106">Para obter mais informações, consulte [expressões inseridas em XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a0b19-106">For more information, see [Embedded Expressions in XML](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).</span></span>  
  
 <span data-ttu-id="a0b19-107">Você também pode usar as APIs de [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] para criar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="a0b19-107">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="a0b19-108">Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="a0b19-108">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="a0b19-109">Procedimentos</span><span class="sxs-lookup"><span data-stu-id="a0b19-109">Procedures</span></span>  
  
#### <a name="to-insert-text-as-element-content"></a><span data-ttu-id="a0b19-110">Para inserir texto como conteúdo do elemento</span><span class="sxs-lookup"><span data-stu-id="a0b19-110">To insert text as element content</span></span>  
  
- <span data-ttu-id="a0b19-111">O exemplo a seguir mostra como inserir o texto contido na variável `contactName` entre os elementos de nome de abertura e fechamento.</span><span class="sxs-lookup"><span data-stu-id="a0b19-111">The following example shows how to insert the text that is contained in the `contactName` variable between the opening and closing name elements.</span></span>  
  
     [!code-vb[VbXMLSamples#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#39)]  
  
     <span data-ttu-id="a0b19-112">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a0b19-112">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-as-an-attribute-value"></a><span data-ttu-id="a0b19-113">Para inserir texto como um valor de atributo</span><span class="sxs-lookup"><span data-stu-id="a0b19-113">To insert text as an attribute value</span></span>  
  
- <span data-ttu-id="a0b19-114">O exemplo a seguir mostra como inserir o texto contido na variável `phoneType` como o valor do atributo `type`.</span><span class="sxs-lookup"><span data-stu-id="a0b19-114">The following example shows how to insert the text that is contained in the `phoneType` variable as the value of the `type` attribute.</span></span>  
  
     [!code-vb[VbXMLSamples#40](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#40)]  
  
     <span data-ttu-id="a0b19-115">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a0b19-115">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <phone type="home">206-555-0144</phone>  
    </contact>  
    ```  
  
#### <a name="to-insert-text-for-an-element-name"></a><span data-ttu-id="a0b19-116">Para inserir texto para um nome de elemento</span><span class="sxs-lookup"><span data-stu-id="a0b19-116">To insert text for an element name</span></span>  
  
- <span data-ttu-id="a0b19-117">O exemplo a seguir mostra como inserir o texto contido na variável `elementName` como o nome de um elemento.</span><span class="sxs-lookup"><span data-stu-id="a0b19-117">The following example shows how to insert the text that is contained in the `elementName` variable as the name of an element.</span></span>  
  
     <span data-ttu-id="a0b19-118">Ao criar elementos usando essa técnica, você deve fechá-los com a marca \</>.</span><span class="sxs-lookup"><span data-stu-id="a0b19-118">When creating elements by using this technique, you must close them with the \</> tag.</span></span>  
  
     [!code-vb[VbXMLSamples#41](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples14.vb#41)]  
  
     <span data-ttu-id="a0b19-119">Este exemplo gera a seguinte saída:</span><span class="sxs-lookup"><span data-stu-id="a0b19-119">This example produces the following output:</span></span>  
  
    ```xml  
    <contact>  
      <name>Patrick Hines</name>  
    </contact>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="a0b19-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0b19-120">See also</span></span>

- [<span data-ttu-id="a0b19-121">Como criar literais XML</span><span class="sxs-lookup"><span data-stu-id="a0b19-121">How to: Create XML Literals</span></span>](../../../../visual-basic/programming-guide/language-features/xml/how-to-create-xml-literals.md)
- [<span data-ttu-id="a0b19-122">Expressões Inseridas no XML</span><span class="sxs-lookup"><span data-stu-id="a0b19-122">Embedded Expressions in XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [<span data-ttu-id="a0b19-123">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0b19-123">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="a0b19-124">XML</span><span class="sxs-lookup"><span data-stu-id="a0b19-124">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
