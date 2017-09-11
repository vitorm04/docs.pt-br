---
title: "Como: iterar por uma enumeração no Visual Basic | Documentos do Microsoft"
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
- arrays [Visual Basic], iterating
- enumerations [Visual Basic], iterating
- ListBox control [Windows Forms], populating from an enumeration
ms.assetid: e5aa10eb-cfcd-4a3b-8e76-f06b8f2002be
caps.latest.revision: 20
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
ms.openlocfilehash: 7ff61416452e64f253f10b5a39ba7f2ea0c53edb
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-iterate-through-an-enumeration-in-visual-basic"></a><span data-ttu-id="46abf-102">Como iterar em uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="46abf-102">How to: Iterate Through An Enumeration in Visual Basic</span></span>
<span data-ttu-id="46abf-103">Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores constantes com nomes.</span><span class="sxs-lookup"><span data-stu-id="46abf-103">Enumerations provide a convenient way to work with sets of related constants, and to associate constant values with names.</span></span> <span data-ttu-id="46abf-104">Para iterar por meio de uma enumeração, você pode movê-la para uma matriz usando o <xref:System.Enum.GetValues%2A>método.</xref:System.Enum.GetValues%2A></span><span class="sxs-lookup"><span data-stu-id="46abf-104">To iterate through an enumeration, you can move it into an array using the <xref:System.Enum.GetValues%2A> method.</span></span> <span data-ttu-id="46abf-105">Você também pode percorrer uma enumeração usando um `For...Each` instrução, usando o <xref:System.Enum.GetNames%2A>ou <xref:System.Enum.GetValues%2A>método para extrair o valor de cadeia de caracteres ou numérica.</xref:System.Enum.GetValues%2A> </xref:System.Enum.GetNames%2A></span><span class="sxs-lookup"><span data-stu-id="46abf-105">You could also iterate through an enumeration using a `For...Each` statement, using the <xref:System.Enum.GetNames%2A> or <xref:System.Enum.GetValues%2A> method to extract the string or numeric value.</span></span>  
  
### <a name="to-iterate-through-an-enumeration"></a><span data-ttu-id="46abf-106">Para iterar em uma enumeração</span><span class="sxs-lookup"><span data-stu-id="46abf-106">To iterate through an enumeration</span></span>  
  
-   <span data-ttu-id="46abf-107">Declarar uma matriz e converter a enumeração com o <xref:System.Enum.GetValues%2A>método antes de passar a matriz como você faria qualquer outra variável.</xref:System.Enum.GetValues%2A></span><span class="sxs-lookup"><span data-stu-id="46abf-107">Declare an array and convert the enumeration to it with the <xref:System.Enum.GetValues%2A> method before passing the array as you would any other variable.</span></span> <span data-ttu-id="46abf-108">O exemplo a seguir exibe cada membro da enumeração <xref:Microsoft.VisualBasic.FirstDayOfWeek>como ele itera por meio da enumeração.</xref:Microsoft.VisualBasic.FirstDayOfWeek></span><span class="sxs-lookup"><span data-stu-id="46abf-108">The following example displays each member of the enumeration <xref:Microsoft.VisualBasic.FirstDayOfWeek> as it iterates through the enumeration.</span></span>  
  
     <span data-ttu-id="46abf-109">[!code-vb[VbEnumsTask&#7;](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="46abf-109">[!code-vb[VbEnumsTask#7](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-iterate-through-an-enumeration_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46abf-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46abf-110">See Also</span></span>  
 <span data-ttu-id="46abf-111">[Visão geral de enumerações](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span><span class="sxs-lookup"><span data-stu-id="46abf-111">[Enumerations Overview](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-overview.md) </span></span>  
<span data-ttu-id="46abf-112"> [Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="46abf-112"> [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="46abf-113"> [Quando usar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="46abf-113"> [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md) </span></span>  
<span data-ttu-id="46abf-114"> [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="46abf-114"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="46abf-115"> [Como: fazer referência a um membro de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span><span class="sxs-lookup"><span data-stu-id="46abf-115"> [How to: Refer to an Enumeration Member](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md) </span></span>  
<span data-ttu-id="46abf-116"> [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="46abf-116"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="46abf-117"> [Matrizes](../../../../visual-basic/programming-guide/language-features/arrays/index.md)</span><span class="sxs-lookup"><span data-stu-id="46abf-117"> [Arrays](../../../../visual-basic/programming-guide/language-features/arrays/index.md)</span></span>
