---
title: 'Como: criar literais XML (Visual Basic) | Documentos do Microsoft'
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
- XML literals [Visual Basic], creating
ms.assetid: 573a6db5-b14d-4e42-b356-8cc7e2d77745
caps.latest.revision: 17
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
ms.openlocfilehash: 3a7b5dc692317067290b48222ba056d765a449f3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-create-xml-literals-visual-basic"></a><span data-ttu-id="fb3ec-102">Como criar literais XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fb3ec-102">How to: Create XML Literals (Visual Basic)</span></span>
<span data-ttu-id="fb3ec-103">Você pode criar um documento XML, fragmento ou elemento diretamente no código usando um literal XML.</span><span class="sxs-lookup"><span data-stu-id="fb3ec-103">You can create an XML document, fragment, or element directly in code by using an XML literal.</span></span> <span data-ttu-id="fb3ec-104">Os exemplos neste tópico demonstram como criar um elemento XML que tem três elementos filho e como criar um documento XML.</span><span class="sxs-lookup"><span data-stu-id="fb3ec-104">The examples in this topic demonstrate how to create an XML element that has three child elements, and how to create an XML document.</span></span>  
  
 <span data-ttu-id="fb3ec-105">Você também pode usar o [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs para criar [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objetos.</span><span class="sxs-lookup"><span data-stu-id="fb3ec-105">You can also use the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] APIs to create [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] objects.</span></span> <span data-ttu-id="fb3ec-106">Para obter mais informações, consulte <xref:System.Xml.Linq.XElement>.</xref:System.Xml.Linq.XElement></span><span class="sxs-lookup"><span data-stu-id="fb3ec-106">For more information, see <xref:System.Xml.Linq.XElement>.</span></span>  
  
### <a name="to-create-an-xml-element"></a><span data-ttu-id="fb3ec-107">Para criar um elemento XML</span><span class="sxs-lookup"><span data-stu-id="fb3ec-107">To create an XML element</span></span>  
  
-   <span data-ttu-id="fb3ec-108">Crie o XML embutido usando a sintaxe literal XML, que é o mesmo que a sintaxe XML real.</span><span class="sxs-lookup"><span data-stu-id="fb3ec-108">Create the XML inline by using the XML literal syntax, which is the same as the actual XML syntax.</span></span>  
  
     <span data-ttu-id="fb3ec-109">[!code-vb[VbXMLSamples n º&5;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="fb3ec-109">[!code-vb[VbXMLSamples#5](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_1.vb)]</span></span>  
  
     <span data-ttu-id="fb3ec-110">Execute o código.</span><span class="sxs-lookup"><span data-stu-id="fb3ec-110">Run the code.</span></span> <span data-ttu-id="fb3ec-111">A saída desse código é:</span><span class="sxs-lookup"><span data-stu-id="fb3ec-111">The output of this code is:</span></span>  
  
     `<contact>`  
  
     `<name>Patrick Hines</name>`  
  
     `<phone type="home">206-555-0144</phone>`  
  
     `<phone type="work">425-555-0145</phone>`  
  
     `</contact>`  
  
### <a name="to-create-an-xml-document"></a><span data-ttu-id="fb3ec-112">Para criar um documento XML</span><span class="sxs-lookup"><span data-stu-id="fb3ec-112">To create an XML document</span></span>  
  
-   <span data-ttu-id="fb3ec-113">Crie o documento XML embutido.</span><span class="sxs-lookup"><span data-stu-id="fb3ec-113">Create the XML document inline.</span></span> <span data-ttu-id="fb3ec-114">O código a seguir cria um documento XML que tem sintaxe literal, uma declaração XML, uma instrução de processamento, um comentário e um elemento que contém outro elemento.</span><span class="sxs-lookup"><span data-stu-id="fb3ec-114">The following code creates an XML document that has literal syntax, an XML declaration, a processing instruction, a comment, and an element that contains another element.</span></span>  
  
     <span data-ttu-id="fb3ec-115">[!code-vb[30 VbXMLSamples](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]</span><span class="sxs-lookup"><span data-stu-id="fb3ec-115">[!code-vb[VbXMLSamples#30](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-create-xml-literals_2.vb)]</span></span>  
  
     <span data-ttu-id="fb3ec-116">Execute o código.</span><span class="sxs-lookup"><span data-stu-id="fb3ec-116">Run the code.</span></span> <span data-ttu-id="fb3ec-117">A saída desse código é:</span><span class="sxs-lookup"><span data-stu-id="fb3ec-117">The output of this code is:</span></span>  
  
     `<?xml-stylesheet type="text/xsl" href="show_book.xsl"?>`  
  
     `<!-- Tests that the application works. -->`  
  
     `<books>`  
  
     `<book/>`  
  
     `</books>`  
  
## <a name="see-also"></a><span data-ttu-id="fb3ec-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fb3ec-118">See Also</span></span>  
 <span data-ttu-id="fb3ec-119">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span><span class="sxs-lookup"><span data-stu-id="fb3ec-119">[XML](../../../../visual-basic/programming-guide/language-features/xml/index.md) </span></span>  
<span data-ttu-id="fb3ec-120"> [Criando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span><span class="sxs-lookup"><span data-stu-id="fb3ec-120"> [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md) </span></span>  
<span data-ttu-id="fb3ec-121"> [Literal do elemento XML](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span><span class="sxs-lookup"><span data-stu-id="fb3ec-121"> [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md) </span></span>  
<span data-ttu-id="fb3ec-122"> [Literal de Documento XML](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)</span><span class="sxs-lookup"><span data-stu-id="fb3ec-122"> [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)</span></span>
