---
title: 'Como: Criar literais XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
ms.openlocfilehash: c79b607f9ce5c779539b7700feafb7d4e3d67d24
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56974244"
---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="e6e8f-102">Como: Criar literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6e8f-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="e6e8f-103">Você pode criar um documento, fragmento ou elemento XML diretamente no código usando um literal XML.</span><span class="sxs-lookup"><span data-stu-id="e6e8f-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="e6e8f-104">Os exemplos neste tópico demonstram como criar um elemento XML que tem três elementos filho e como criar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="e6e8f-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="e6e8f-105">Você também pode usar o [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs para criar [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="e6e8f-105">You can also use the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] APIs to create [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] objects.</span></span> <span data-ttu-id="e6e8f-106">Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="e6e8f-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="e6e8f-107">Para criar um elemento XML</span><span class="sxs-lookup"><span data-stu-id="e6e8f-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="e6e8f-108">Crie o XML embutido usando a sintaxe de literais XML, que é o mesmo que a sintaxe XML real.</span><span class="sxs-lookup"><span data-stu-id="e6e8f-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     [!code-vb[VbXMLSamples#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples2.vb#5)]  
  
     <span data-ttu-id="e6e8f-109">Execute o código.</span><span class="sxs-lookup"><span data-stu-id="e6e8f-109">Run the code.</span></span> <span data-ttu-id="e6e8f-110">A saída desse código é:</span><span class="sxs-lookup"><span data-stu-id="e6e8f-110">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="e6e8f-111">Para criar um documento XML</span><span class="sxs-lookup"><span data-stu-id="e6e8f-111">To create an XML document</span></span>  
  
-   <span data-ttu-id="e6e8f-112">Crie o documento XML embutido.</span><span class="sxs-lookup"><span data-stu-id="e6e8f-112">Create the XML document inline.</span></span> <span data-ttu-id="e6e8f-113">O código a seguir cria um documento XML que tem sintaxe literal, uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.</span><span class="sxs-lookup"><span data-stu-id="e6e8f-113">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
     <span data-ttu-id="e6e8f-114">Execute o código.</span><span class="sxs-lookup"><span data-stu-id="e6e8f-114">Run the code.</span></span> <span data-ttu-id="e6e8f-115">A saída desse código é:</span><span class="sxs-lookup"><span data-stu-id="e6e8f-115">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="e6e8f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6e8f-116">See also</span></span>
- [<span data-ttu-id="e6e8f-117">XML</span><span class="sxs-lookup"><span data-stu-id="e6e8f-117">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
- [<span data-ttu-id="e6e8f-118">Criando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e6e8f-118">Creating XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [<span data-ttu-id="e6e8f-119">Literal do Elemento XML</span><span class="sxs-lookup"><span data-stu-id="e6e8f-119">XML Element Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [<span data-ttu-id="e6e8f-120">Literal de Documento XML</span><span class="sxs-lookup"><span data-stu-id="e6e8f-120">XML Document Literal</span></span>](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
