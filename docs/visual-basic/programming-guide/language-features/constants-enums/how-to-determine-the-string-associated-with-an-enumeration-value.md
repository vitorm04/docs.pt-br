---
title: "Como: determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic) | Documentos do Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- enumerations [Visual Basic]
- strings [Visual Basic], enumeration values
- values, enumeration members
ms.assetid: 9253e7c8-579c-49a2-8f26-392b20ea99eb
caps.latest.revision: 12
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
ms.openlocfilehash: 9612ee72961235cae5feecbfdd19af0477e3fa4a
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-determine-the-string-associated-with-an-enumeration-value-visual-basic"></a><span data-ttu-id="c0ee2-102">Como determinar a cadeia de caracteres associada a um valor de enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c0ee2-102">How to: Determine the String Associated with an Enumeration Value (Visual Basic)</span></span>
<span data-ttu-id="c0ee2-103">O <xref:System.Enum.GetValues%2A>e <xref:System.Enum.GetNames%2A>métodos permitem que você determine as cadeias de caracteres e valores associados a membros de enumeração.</xref:System.Enum.GetNames%2A> </xref:System.Enum.GetValues%2A></span><span class="sxs-lookup"><span data-stu-id="c0ee2-103">The <xref:System.Enum.GetValues%2A> and <xref:System.Enum.GetNames%2A> methods allow you to determine the strings and values associated with enumeration members.</span></span>  
  
### <a name="to-determine-the-string-associated-with-an-enumeration"></a><span data-ttu-id="c0ee2-104">Para determinar a cadeia de caracteres associada a uma enumeração</span><span class="sxs-lookup"><span data-stu-id="c0ee2-104">To determine the string associated with an enumeration</span></span>  
  
-   <span data-ttu-id="c0ee2-105">Use o <xref:System.Enum.GetNames%2A>método para recuperar as cadeias de caracteres associadas com os membros de enumeração.</xref:System.Enum.GetNames%2A></span><span class="sxs-lookup"><span data-stu-id="c0ee2-105">Use the <xref:System.Enum.GetNames%2A> method to retrieve the strings associated with the enumeration members.</span></span> <span data-ttu-id="c0ee2-106">Este exemplo declara uma enumeração, `flavorEnum`, em seguida, usa o <xref:System.Enum.GetNames%2A>método para exibir as cadeias de caracteres associadas a cada membro.</xref:System.Enum.GetNames%2A></span><span class="sxs-lookup"><span data-stu-id="c0ee2-106">This example declares an enumeration, `flavorEnum`, then uses the <xref:System.Enum.GetNames%2A> method to display the strings associated with each member.</span></span>  
  
     <span data-ttu-id="c0ee2-107">[!code-vb[VbEnumsTask n º&2;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="c0ee2-107">[!code-vb[VbEnumsTask#2](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-determine-the-string-associated-with-an-enumeration-value_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0ee2-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c0ee2-108">See Also</span></span>  
 <span data-ttu-id="c0ee2-109"><xref:System.Enum.GetValues%2A></xref:System.Enum.GetValues%2A></span><span class="sxs-lookup"><span data-stu-id="c0ee2-109"><xref:System.Enum.GetValues%2A></span></span>   
 <span data-ttu-id="c0ee2-110"><xref:System.Enum.GetNames%2A></xref:System.Enum.GetNames%2A></span><span class="sxs-lookup"><span data-stu-id="c0ee2-110"><xref:System.Enum.GetNames%2A></span></span>   
 <span data-ttu-id="c0ee2-111"><xref:System.Enum></xref:System.Enum></span><span class="sxs-lookup"><span data-stu-id="c0ee2-111"><xref:System.Enum></span></span>   
<span data-ttu-id="c0ee2-112"> [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="c0ee2-112"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="c0ee2-113"> [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="c0ee2-113"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="c0ee2-114"> [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="c0ee2-114"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="c0ee2-115"> [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="c0ee2-115"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="c0ee2-116"> [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="c0ee2-116"> [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span></span>  
<span data-ttu-id="c0ee2-117"> [Instrução Enum](../../../../visual-basic/language-reference/statements/enum-statement.md)</span><span class="sxs-lookup"><span data-stu-id="c0ee2-117"> [Enum Statement](../../../../visual-basic/language-reference/statements/enum-statement.md)</span></span>
