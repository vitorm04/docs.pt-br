---
title: 'Como: acessar elementos descendentes XML (Visual Basic) | Documentos do Microsoft'
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
- XML descendent axis property [Visual Basic]
- XML axis [Visual Basic], descendent
- descendent axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: aabfa258-4112-4e7e-bab9-403f96072ef7
caps.latest.revision: 19
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
ms.openlocfilehash: c6b665676ad66e92c644d0a28ebe51b43fa34f3d
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-access-xml-descendant-elements-visual-basic"></a><span data-ttu-id="d4574-102">Como acessar elementos descendentes XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d4574-102">How to: Access XML Descendant Elements (Visual Basic)</span></span>
<span data-ttu-id="d4574-103">Este exemplo mostra como usar uma propriedade de eixo descendente para acessar todos os elementos XML que têm um nome especificado e que estão contidas em um elemento XML.</span><span class="sxs-lookup"><span data-stu-id="d4574-103">This example shows how to use a descendant axis property to access all XML elements that have a specified name and that are contained under an XML element.</span></span> <span data-ttu-id="d4574-104">Em particular, ele usa o `Value` propriedade para obter o valor do primeiro elemento na coleção de `name` retorna de propriedade de eixo descendente.</span><span class="sxs-lookup"><span data-stu-id="d4574-104">In particular, it uses the `Value` property to get the value of the first element in the collection that the `name` descendant axis property returns.</span></span> <span data-ttu-id="d4574-105">O `name` propriedade de eixo descendente obtém todos os elementos chamados `name` que estão contidos no `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="d4574-105">The `name` descendant axis property gets all elements named `name` that are contained in the `contacts` object.</span></span> <span data-ttu-id="d4574-106">Este exemplo também usa o `phone` propriedade de eixo descendente para acessar todos os descendentes nomeados `phone` que estão contidos no `contacts` objeto.</span><span class="sxs-lookup"><span data-stu-id="d4574-106">This example also uses the `phone` descendant axis property to access all descendants named `phone` that are contained in the `contacts` object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d4574-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d4574-107">Example</span></span>  
 <span data-ttu-id="d4574-108">[!code-vb[VbXMLSamples&#31;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="d4574-108">[!code-vb[VbXMLSamples#31](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/how-to-access-xml-descendant-elements_1.vb)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d4574-109">Compilando o código</span><span class="sxs-lookup"><span data-stu-id="d4574-109">Compiling the Code</span></span>  
 <span data-ttu-id="d4574-110">Este exemplo requer:</span><span class="sxs-lookup"><span data-stu-id="d4574-110">This example requires:</span></span>  
  
-   <span data-ttu-id="d4574-111">Uma referência para o <xref:System.Xml.Linq>namespace.</xref:System.Xml.Linq></span><span class="sxs-lookup"><span data-stu-id="d4574-111">A reference to the <xref:System.Xml.Linq> namespace.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d4574-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d4574-112">See Also</span></span>  
 <span data-ttu-id="d4574-113"><xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="d4574-113"><xref:System.Xml.Linq.XContainer.Descendants%2A?displayProperty=fullName></span></span>   
<span data-ttu-id="d4574-114"> [Propriedade de eixo descendente XML](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span><span class="sxs-lookup"><span data-stu-id="d4574-114"> [XML Descendant Axis Property](../../../../visual-basic/language-reference/xml-axis/xml-descendant-axis-property.md) </span></span>  
<span data-ttu-id="d4574-115"> [Propriedade de valor XML](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span><span class="sxs-lookup"><span data-stu-id="d4574-115"> [XML Value Property](../../../../visual-basic/language-reference/xml-axis/xml-value-property.md) </span></span>  
<span data-ttu-id="d4574-116"> [Acessando XML no Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md) </span><span class="sxs-lookup"><span data-stu-id="d4574-116"> [Accessing XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/accessing-xml.md) </span></span>  
<span data-ttu-id="d4574-117"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span><span class="sxs-lookup"><span data-stu-id="d4574-117"> [XML](../../../../visual-basic/programming-guide/language-features/xml/index.md)</span></span>
