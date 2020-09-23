---
title: Como acessar elementos descendentes XML
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: dcbaf1f9022d86f40a90ef6a1e0033f627caeef2
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058203"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="184c7-102">Como acessar elementos descendentes XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="184c7-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>

<span data-ttu-id="184c7-103">Este exemplo mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidos em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="184c7-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="184c7-104">Em particular, ele usa a `Value` propriedade para obter o valor do primeiro elemento na coleção que a propriedade do `name` eixo descendente retorna.</span><span class="sxs-lookup"><span data-stu-id="184c7-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="184c7-105">A `name` Propriedade do eixo descendente Obtém todos os elementos chamados `name` que estão contidos no `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="184c7-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="184c7-106">Este exemplo também usa a `phone` Propriedade Axis descendente para acessar todos os descendentes nomeados `phone` contidos no `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="184c7-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="184c7-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="184c7-107">Example</span></span>  

 [!code-vb[VbXMLSamples#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#31)]  
  
## <a name="compile-the-code"></a><span data-ttu-id="184c7-108">Compilar o código</span><span class="sxs-lookup"><span data-stu-id="184c7-108">Compile the code</span></span>  

 <span data-ttu-id="184c7-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="184c7-109">This example requires:</span></span>  
  
- <span data-ttu-id="184c7-110">Uma referência ao <xref:System.Xml.Linq> namespace.</span><span class="sxs-lookup"><span data-stu-id="184c7-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="184c7-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="184c7-111">See also</span></span>

- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="184c7-112">Propriedade de Eixo Descendente XML</span><span class="sxs-lookup"><span data-stu-id="184c7-112">XML Descendant Axis Property</span></span>](../../../language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="184c7-113">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="184c7-113">XML Value Property</span></span>](../../../language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="184c7-114">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="184c7-114">Accessing XML in Visual Basic</span></span>](accessing-xml.md)
- [<span data-ttu-id="184c7-115">XML</span><span class="sxs-lookup"><span data-stu-id="184c7-115">XML</span></span>](index.md)
