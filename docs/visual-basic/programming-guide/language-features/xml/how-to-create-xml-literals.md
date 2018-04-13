---
title: Como criar literais XML (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ce1bf763529b436158c2d74811c4938182166f92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="edab8-102">Como criar literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="edab8-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="edab8-103">Você pode criar um documento XML, fragmento ou elemento diretamente no código usando um literal XML.</span><span class="sxs-lookup"><span data-stu-id="edab8-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="edab8-104">Os exemplos neste tópico demonstram como criar um elemento XML que tem três elementos filho e como criar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="edab8-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="edab8-105">Você também pode usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs para criar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="edab8-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="edab8-106">Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="edab8-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="edab8-107">Para criar um elemento XML</span><span class="sxs-lookup"><span data-stu-id="edab8-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="edab8-108">Crie o XML embutido usando a sintaxe de literais XML, que é o mesmo que a sintaxe XML real.</span><span class="sxs-lookup"><span data-stu-id="edab8-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]  
  
     <span data-ttu-id="edab8-109">Execute o código.</span><span class="sxs-lookup"><span data-stu-id="edab8-109">Run the code.</span></span> <span data-ttu-id="edab8-110">A saída desse código é:</span><span class="sxs-lookup"><span data-stu-id="edab8-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="edab8-111">Para criar um documento XML</span><span class="sxs-lookup"><span data-stu-id="edab8-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="edab8-112">Crie o documento XML embutido.</span><span class="sxs-lookup"><span data-stu-id="edab8-112">Create the XML document inline.</span></span> <span data-ttu-id="edab8-113">O código a seguir cria um documento XML que tem sintaxe literal, uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.</span><span class="sxs-lookup"><span data-stu-id="edab8-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]  
  
     <span data-ttu-id="edab8-114">Execute o código.</span><span class="sxs-lookup"><span data-stu-id="edab8-114">Run the code.</span></span> <span data-ttu-id="edab8-115">A saída desse código é:</span><span class="sxs-lookup"><span data-stu-id="edab8-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="edab8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="edab8-116">See Also</span></span>  
 [<span data-ttu-id="edab8-117">XML</span><span class="sxs-lookup"><span data-stu-id="edab8-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)  
 [<span data-ttu-id="edab8-118">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="edab8-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [<span data-ttu-id="edab8-119">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="edab8-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [<span data-ttu-id="edab8-120">Literal de Documento XML</span><span class="sxs-lookup"><span data-stu-id="edab8-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
