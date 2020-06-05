---
title: Como acessar elementos filho XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
ms.openlocfilehash: 994249801eecc2984947efac9712df0047f076a4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392812"
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="c6bb5-102">Como acessar elementos filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c6bb5-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="c6bb5-103">Este exemplo mostra como usar uma propriedade de eixo filho para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="c6bb5-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="c6bb5-104">Em particular, ele usa a <xref:System.Xml.Linq.XElement.Value%2A> propriedade para obter o valor do primeiro elemento na coleção que a propriedade do `name` eixo filho retorna.</span><span class="sxs-lookup"><span data-stu-id="c6bb5-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="c6bb5-105">A `name` Propriedade do eixo filho obtém todos os elementos filho chamados `phone` no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="c6bb5-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="c6bb5-106">Este exemplo também usa a `phone` propriedade de eixo filho para acessar todos os elementos filho chamados `phone` que estão contidos no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="c6bb5-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6bb5-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c6bb5-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#10)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="c6bb5-108">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="c6bb5-108">Compile the code</span></span>  
 <span data-ttu-id="c6bb5-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="c6bb5-109">This example requires:</span></span>  
  
- <span data-ttu-id="c6bb5-110">Uma referência ao <xref:System.Xml.Linq> namespace.</span><span class="sxs-lookup"><span data-stu-id="c6bb5-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6bb5-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="c6bb5-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>
- [<span data-ttu-id="c6bb5-112">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="c6bb5-112">XML Child Axis Property</span></span>](../../../language-reference/xml-axis/xml-child-axis-property.md)
- [<span data-ttu-id="c6bb5-113">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="c6bb5-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="c6bb5-114">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c6bb5-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="c6bb5-115">XML</span><span class="sxs-lookup"><span data-stu-id="c6bb5-115">XML</span></span>](index.md)
