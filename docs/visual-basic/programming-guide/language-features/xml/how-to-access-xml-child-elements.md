---
title: 'Como: acessar elementos filho XML (Visual Basic) | Documentos do Microsoft'
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
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 6689eb36-c471-469f-a82d-099ab8197b25
caps.latest.revision: 18
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
ms.openlocfilehash: 2cbd42a8d603264ff53117b34d54a438ce4f797b
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-access-xml-child-elements-visual-basic"></a><span data-ttu-id="55443-102">Como acessar elementos filho XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55443-102">How to: Access XML Child Elements (Visual Basic)</span></span>
<span data-ttu-id="55443-103">Este exemplo mostra como usar um filho de propriedade de eixo para acessar todos os elementos filho XML que têm um nome especificado em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="55443-103">This example shows how to use a child axis property to access all XML child elements that have a specified name in an XML element.</span></span> <span data-ttu-id="55443-104">Em particular, ele usa o <xref:System.Xml.Linq.XElement.Value%2A>propriedade para obter o valor do primeiro elemento na coleção de `name` retorna de propriedade de eixo filho.</xref:System.Xml.Linq.XElement.Value%2A></span><span class="sxs-lookup"><span data-stu-id="55443-104">In particular, it uses the <xref:System.Xml.Linq.XElement.Value%2A> property to get the value of the first element in the collection that the `name` child axis property returns.</span></span> <span data-ttu-id="55443-105">O `name` propriedade de eixo filho obtém todos os elementos filho chamados `phone` no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="55443-105">The `name` child axis property gets all child elements named `phone` in the `contact` object.</span></span> <span data-ttu-id="55443-106">Este exemplo também usa o `phone` propriedade do eixo filho para acessar todos os elementos filho chamados `phone` que estão contidos no `contact` objeto.</span><span class="sxs-lookup"><span data-stu-id="55443-106">This example also uses the `phone` child axis property to access all child elements named `phone` that are contained in the `contact` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55443-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55443-107">Example</span></span>  
 <span data-ttu-id="55443-108">[!code-vb[VbXMLSamples n º&10;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="55443-108">[!code-vb[VbXMLSamples#10](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-child-elements_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="55443-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="55443-109">Compiling the Code</span></span>  
 <span data-ttu-id="55443-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="55443-110">This example requires:</span></span>  
  
-   <span data-ttu-id="55443-111">Uma referência para o <xref:System.Xml.Linq>namespace.</xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="55443-111">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55443-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55443-112">See Also</span></span>  
 <span data-ttu-id="55443-113"><xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="55443-113"><xref:System.Xml.Linq.XContainer.Elements%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="55443-114"> [Propriedade de eixo filho XML](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="55443-114"> [XML Child Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md) </span></span>  
<span data-ttu-id="55443-115"> [Propriedade de valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span><span class="sxs-lookup"><span data-stu-id="55443-115"> [XML Value Property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span></span>  
<span data-ttu-id="55443-116"> [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md) </span><span class="sxs-lookup"><span data-stu-id="55443-116"> [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md) </span></span>  
<span data-ttu-id="55443-117"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="55443-117"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
