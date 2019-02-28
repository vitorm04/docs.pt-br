---
title: 'Como: Acessar elementos de filho XML (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 874c7490e451d64bf50e25934ea43a9b928ddab9
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56980549"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="1feb6-102">Como: Acessar elementos de filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1feb6-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="1feb6-103">Este exemplo mostra como usar um filho de propriedade de eixo para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="1feb6-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="1feb6-104">Em particular, ele usa o <xref:System.Xml.Linq.XElement.Value%2A> propriedade para obter o valor do primeiro elemento na coleção que o `name` retorna de propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="1feb6-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="1feb6-105">O `name` propriedade de eixo filho obtém todos os elementos filho chamados `phone` no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="1feb6-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="1feb6-106">Este exemplo também usa o `phone` propriedade de eixo filho para acessar todos os elementos filho chamados `phone` que estão contidos no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="1feb6-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1feb6-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1feb6-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1feb6-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="1feb6-108">Compiling the Code</span></span>  
 <span data-ttu-id="1feb6-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="1feb6-109">This example requires:</span></span>  
  
-   <span data-ttu-id="1feb6-110">Uma referência para o <xref:System.Xml.Linq> namespace.</span><span class="sxs-lookup"><span data-stu-id="1feb6-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1feb6-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1feb6-111">See also</span></span>
- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="1feb6-112">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="1feb6-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="1feb6-113">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="1feb6-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="1feb6-114">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1feb6-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="1feb6-115">XML</span><span class="sxs-lookup"><span data-stu-id="1feb6-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
