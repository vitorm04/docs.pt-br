---
title: Como acessar elementos descendentes XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: cc045114c67ee2917ef672e734bc852c40d408ac
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347166"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="aa1c8-102">Como acessar elementos descendentes XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa1c8-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="aa1c8-103">Este exemplo mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidos em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="aa1c8-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="aa1c8-104">Em particular, ele usa a propriedade `Value` para obter o valor do primeiro elemento na coleção que a propriedade do eixo descendente `name` retorna.</span><span class="sxs-lookup"><span data-stu-id="aa1c8-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="aa1c8-105">A propriedade `name` eixo descendente Obtém todos os elementos chamados `name` contidos no objeto `contacts`.</span><span class="sxs-lookup"><span data-stu-id="aa1c8-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="aa1c8-106">Este exemplo também usa a propriedade `phone` eixo descendente para acessar todos os descendentes nomeados `phone` contidos no objeto `contacts`.</span><span class="sxs-lookup"><span data-stu-id="aa1c8-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa1c8-107">{1&gt;Exemplo&lt;1}</span><span class="sxs-lookup"><span data-stu-id="aa1c8-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="aa1c8-108">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="aa1c8-108">Compile the code</span></span>  
 <span data-ttu-id="aa1c8-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="aa1c8-109">This example requires:</span></span>  
  
- <span data-ttu-id="aa1c8-110">Uma referência ao namespace <xref:System.Xml.Linq>.</span><span class="sxs-lookup"><span data-stu-id="aa1c8-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa1c8-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa1c8-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="aa1c8-112">Propriedade de Eixo Descendente XML</span><span class="sxs-lookup"><span data-stu-id="aa1c8-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="aa1c8-113">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="aa1c8-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="aa1c8-114">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa1c8-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="aa1c8-115">XML</span><span class="sxs-lookup"><span data-stu-id="aa1c8-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
