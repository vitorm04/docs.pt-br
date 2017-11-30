---
title: Como acessar elementos filho XML (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d3a708b787ad38f08d4673d4003db839f6cf6a9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="23e52-102">Como acessar elementos filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="23e52-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="23e52-103">Este exemplo mostra como usar um filho de propriedade de eixo para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="23e52-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="23e52-104">Em particular, ele usa o <xref:System.Xml.Linq.XElement.Value%2A> propriedade para obter o valor do primeiro elemento na coleção de `name` retorna de propriedade de eixo filho.</span><span class="sxs-lookup"><span data-stu-id="23e52-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="23e52-105">O `name` propriedade de eixo filho obtém todos os elementos filho denominados `phone` no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="23e52-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="23e52-106">Este exemplo também usa o `phone` propriedade de eixo filho para acessar todos os elementos filho denominados `phone` que estão contidos no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="23e52-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23e52-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="23e52-107">Example</span></span>  
 [!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="23e52-108">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="23e52-108">Compiling the Code</span></span>  
 <span data-ttu-id="23e52-109">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="23e52-109">This example requires:</span></span>  
  
-   <span data-ttu-id="23e52-110">Uma referência para o <xref:System.Xml.Linq> namespace.</span><span class="sxs-lookup"><span data-stu-id="23e52-110">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23e52-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="23e52-111">See Also</span></span>  
 <xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="23e52-112">Propriedade do Eixo Filho XML</span><span class="sxs-lookup"><span data-stu-id="23e52-112">XML Child Axis Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)  
 [<span data-ttu-id="23e52-113">Propriedade do Valor XML</span><span class="sxs-lookup"><span data-stu-id="23e52-113">XML Value Property</span></span>](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md)  
 [<span data-ttu-id="23e52-114">Acessando XML no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="23e52-114">Accessing XML in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md)  
 [<span data-ttu-id="23e52-115">XML</span><span class="sxs-lookup"><span data-stu-id="23e52-115">XML</span></span>](../../../../visual-basic/programming-guide/language-features/xml/index.md)
