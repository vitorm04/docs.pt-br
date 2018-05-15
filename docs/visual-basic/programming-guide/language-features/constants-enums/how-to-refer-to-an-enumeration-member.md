---
title: Como fazer referência a um membro de enumeração (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], referring to
- values [Visual Basic], associating constant values with names
- enumeration members
- constants [Visual Basic], enumerated
ms.assetid: bbb5c3cc-7cdb-4814-8d6a-a6d91546ed1e
ms.openlocfilehash: f995a0ef69c503360a5d709551a7f0ccfd67ce40
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-refer-to-an-enumeration-member-visual-basic"></a><span data-ttu-id="0d80f-102">Como fazer referência a um membro de enumeração (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0d80f-102">How to: Refer to an Enumeration Member (Visual Basic)</span></span>
<span data-ttu-id="0d80f-103">Enumerações fornecem uma maneira conveniente para trabalhar com conjuntos de constantes relacionadas e para associar valores de constante com nomes.</span><span class="sxs-lookup"><span data-stu-id="0d80f-103">Enumerations provide a convenient way to work with sets of related constants and to associate constant values with names.</span></span> <span data-ttu-id="0d80f-104">Por exemplo, é possível declarar uma enumeração de um conjunto de constantes de inteiros associados aos dias da semana e, em seguida, usar os nomes de dias em vez de seus valores de inteiros em seu código.</span><span class="sxs-lookup"><span data-stu-id="0d80f-104">For example, you can declare an enumeration for a set of integer constants associated with the days of the week, and then use the names of the days rather than their integer values in your code.</span></span>  
  
 <span data-ttu-id="0d80f-105">Você pode evitar o uso de nomes totalmente qualificados com o `Imports` instrução.</span><span class="sxs-lookup"><span data-stu-id="0d80f-105">You can avoid using fully qualified names with the `Imports` statement.</span></span> <span data-ttu-id="0d80f-106">Para obter mais informações, consulte [enumerações e qualificação de nome](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span><span class="sxs-lookup"><span data-stu-id="0d80f-106">For more information, see [Enumerations and Name Qualification](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md).</span></span>  
  
### <a name="to-refer-to-an-enumeration-member"></a><span data-ttu-id="0d80f-107">Para se referir a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="0d80f-107">To refer to an enumeration member</span></span>  
  
-   <span data-ttu-id="0d80f-108">Qualifica o nome do membro com a enumeração.</span><span class="sxs-lookup"><span data-stu-id="0d80f-108">Qualify the member name with the enumeration.</span></span> <span data-ttu-id="0d80f-109">Por exemplo, o exemplo a seguir atribui o `Saturday` membro o `FirstDayOfWeek` enumeração à variável `DayValue`.</span><span class="sxs-lookup"><span data-stu-id="0d80f-109">For example, the following example assigns the `Saturday` member of the `FirstDayOfWeek` enumeration to the variable `DayValue`.</span></span>  
  
     [!code-vb[VbEnumsTask#19](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-refer-to-an-enumeration-member_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0d80f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0d80f-110">See Also</span></span>  
 [<span data-ttu-id="0d80f-111">Como: declarar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="0d80f-111">How to: Declare an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md)  
 [<span data-ttu-id="0d80f-112">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="0d80f-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="0d80f-113">Como: iterar por meio de uma enumeração no Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0d80f-113">How to: Iterate Through An Enumeration in Visual Basic</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-iterate-through-an-enumeration.md)  
 [<span data-ttu-id="0d80f-114">Como determinar a cadeia de caracteres associada a um valor de enumeração</span><span class="sxs-lookup"><span data-stu-id="0d80f-114">How to: Determine the String Associated with an Enumeration Value</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-determine-the-string-associated-with-an-enumeration-value.md)  
 [<span data-ttu-id="0d80f-115">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="0d80f-115">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
