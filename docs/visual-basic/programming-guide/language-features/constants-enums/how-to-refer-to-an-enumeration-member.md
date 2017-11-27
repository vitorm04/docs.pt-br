---
title: "Como fazer referência a um membro de enumeração (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ae4e6eb9c011095c6cf0abe1ee3ac7a68f156f01
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="e5204-102">Como fazer referência a um membro de enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5204-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="e5204-103">Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante com nomes.</span><span class="sxs-lookup"><span data-stu-id="e5204-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="e5204-104">Por exemplo, é possível declarar uma enumeração de um conjunto de constantes de inteiros associados aos dias da semana e, em seguida, usar os nomes de dias em vez de seus valores de inteiros em seu código.</span><span class="sxs-lookup"><span data-stu-id="e5204-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="e5204-105">Você pode evitar o uso de nomes totalmente qualificados com o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="e5204-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="e5204-106">Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="e5204-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="e5204-107">Para se referir a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="e5204-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="e5204-108">Qualifica o nome do membro com a enumeração.</span><span class="sxs-lookup"><span data-stu-id="e5204-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="e5204-109">Por exemplo, o exemplo a seguir atribui o `Saturday` membro o `FirstDayOfWeek` enumeração à variável `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="e5204-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="e5204-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e5204-110">See Also</span></span>  
 [<span data-ttu-id="e5204-111">Como: declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="e5204-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="e5204-112">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="e5204-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="e5204-113">Como: iterar por meio de uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="e5204-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="e5204-114">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="e5204-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="e5204-115">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="e5204-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
