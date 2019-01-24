---
title: 'Como: Elementos descendentes de XML de acesso (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
ms.openlocfilehash: f1248109dfcc853f701ea2ab61edc67d768e9663
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54666170"
---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="fd9a9-102">Como: Elementos descendentes de XML de acesso (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fd9a9-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="fd9a9-103">Este exemplo mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidas em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="fd9a9-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="fd9a9-104">Em particular, ele usa o `Value` propriedade para obter o valor do primeiro elemento na coleção que o `name` retorna da propriedade de eixo descendente.</span><span class="sxs-lookup"><span data-stu-id="fd9a9-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="fd9a9-105">O `name` propriedade de eixo descendente obtém todos os elementos chamados `name` que estão contidos no `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="fd9a9-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="fd9a9-106">Este exemplo também usa o `phone` propriedade de eixo descendente para acessar todos os descendentes nomeados `phone` que estão contidos no `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="fd9a9-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fd9a9-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fd9a9-107">Example</span></span>  
 [!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fd9a9-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="fd9a9-108">Compiling the Code</span></span>  
 <span data-ttu-id="fd9a9-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="fd9a9-109">This example requires:</span></span>  
  
-   <span data-ttu-id="fd9a9-110">Uma referência para o <xref:System.Xml.Linq> namespace.</span><span class="sxs-lookup"><span data-stu-id="fd9a9-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd9a9-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fd9a9-111">See also</span></span>
- <xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fd9a9-112">Propriedade de Eixo Descendente XML</span><span class="sxs-lookup"><span data-stu-id="fd9a9-112">XML Descendant Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md)
- [<span data-ttu-id="fd9a9-113">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="fd9a9-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)
- [<span data-ttu-id="fd9a9-114">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="fd9a9-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)
- [<span data-ttu-id="fd9a9-115">XML</span><span class="sxs-lookup"><span data-stu-id="fd9a9-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
