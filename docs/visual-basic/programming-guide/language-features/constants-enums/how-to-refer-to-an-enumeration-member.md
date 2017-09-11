---
title: "Como: fazer referência a um membro de enumeração (Visual Basic) | Documentos do Microsoft"
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
- enumerations [Visual Basic], referring to
- values, associating constant values with names
- enumeration members
- constants, enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
caps.latest.revision: 13
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
ms.openlocfilehash: 95877cac2b825f86449668c0a8db7e44dd508ce3
ms.contentlocale: pt-br
ms.lasthandoff: 04/12/2017

---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="b7f1f-102">Como fazer referência a um membro de enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b7f1f-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="b7f1f-103">Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e associar valores constantes com nomes.</span><span class="sxs-lookup"><span data-stu-id="b7f1f-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="b7f1f-104">Por exemplo, você pode declarar uma enumeração de um conjunto de constantes de inteiro associados com os dias da semana e, em seguida, usar os nomes de dias em vez de seus valores inteiros em seu código.</span><span class="sxs-lookup"><span data-stu-id="b7f1f-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="b7f1f-105">Você pode evitar o uso de nomes totalmente qualificados com o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="b7f1f-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="b7f1f-106">Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="b7f1f-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="b7f1f-107">Para fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="b7f1f-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="b7f1f-108">Qualifica o nome do membro com a enumeração.</span><span class="sxs-lookup"><span data-stu-id="b7f1f-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="b7f1f-109">Por exemplo, o exemplo a seguir atribui o `Saturday` membro o `FirstDayOfWeek` enumeração à variável `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="b7f1f-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     <span data-ttu-id="b7f1f-110">[!code-vb[19 VbEnumsTask](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="b7f1f-110">[!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7f1f-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b7f1f-111">See Also</span></span>  
 <span data-ttu-id="b7f1f-112">[Como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span><span class="sxs-lookup"><span data-stu-id="b7f1f-112">[How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md) </span></span>  
<span data-ttu-id="b7f1f-113"> [Enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span><span class="sxs-lookup"><span data-stu-id="b7f1f-113"> [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md) </span></span>  
<span data-ttu-id="b7f1f-114"> [Como: iterar por uma enumeração no Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span><span class="sxs-lookup"><span data-stu-id="b7f1f-114"> [How to: Iterate Through An Enumeration in Visual Basic](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md) </span></span>  
<span data-ttu-id="b7f1f-115"> [Como: determinar a cadeia de caracteres associada a um valor de enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span><span class="sxs-lookup"><span data-stu-id="b7f1f-115"> [How to: Determine the String Associated with an Enumeration Value](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md) </span></span>  
<span data-ttu-id="b7f1f-116"> [Quando Usar uma Enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)</span><span class="sxs-lookup"><span data-stu-id="b7f1f-116"> [When to Use an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)</span></span>
