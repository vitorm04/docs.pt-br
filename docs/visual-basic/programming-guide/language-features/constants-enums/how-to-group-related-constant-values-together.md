---
title: Como agrupar valores constantes relacionados
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 151eefee4f69e1db8ba40f91334da8a051b95732
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74354039"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="0e4d1-102">Como agrupar valores constantes relacionados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0e4d1-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="0e4d1-103">An enumeration is the best way to group related constants together.</span><span class="sxs-lookup"><span data-stu-id="0e4d1-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="0e4d1-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span><span class="sxs-lookup"><span data-stu-id="0e4d1-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="0e4d1-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="0e4d1-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="0e4d1-106">To group related constant values</span><span class="sxs-lookup"><span data-stu-id="0e4d1-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="0e4d1-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span><span class="sxs-lookup"><span data-stu-id="0e4d1-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="0e4d1-108">This example creates the `Private` enumeration, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="0e4d1-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="0e4d1-109">Define the constants in the enumeration.</span><span class="sxs-lookup"><span data-stu-id="0e4d1-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="0e4d1-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span><span class="sxs-lookup"><span data-stu-id="0e4d1-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0e4d1-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0e4d1-111">See also</span></span>

- [<span data-ttu-id="0e4d1-112">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="0e4d1-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="0e4d1-113">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="0e4d1-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="0e4d1-114">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="0e4d1-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="0e4d1-115">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="0e4d1-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="0e4d1-116">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="0e4d1-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="0e4d1-117">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="0e4d1-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
