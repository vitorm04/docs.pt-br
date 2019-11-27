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
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="330c4-102">Como agrupar valores constantes relacionados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="330c4-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="330c4-103">Uma enumeração é a melhor maneira de agrupar constantes relacionadas juntas.</span><span class="sxs-lookup"><span data-stu-id="330c4-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="330c4-104">Você cria uma enumeração com a instrução `Enum` na seção declarações de uma classe ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="330c4-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="330c4-105">Para obter mais informações, consulte [como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="330c4-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="330c4-106">Para agrupar valores constantes relacionados</span><span class="sxs-lookup"><span data-stu-id="330c4-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="330c4-107">Escreva uma declaração que inclua um nível de acesso de código, a palavra-chave `Enum` e um nome válido.</span><span class="sxs-lookup"><span data-stu-id="330c4-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="330c4-108">Este exemplo cria a enumeração de `Private`, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="330c4-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="330c4-109">Defina as constantes na enumeração.</span><span class="sxs-lookup"><span data-stu-id="330c4-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="330c4-110">Este exemplo cria a enumeração de `Public` `temperatureValues` e atribui seus valores.</span><span class="sxs-lookup"><span data-stu-id="330c4-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="330c4-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="330c4-111">See also</span></span>

- [<span data-ttu-id="330c4-112">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="330c4-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="330c4-113">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="330c4-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="330c4-114">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="330c4-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="330c4-115">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="330c4-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="330c4-116">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="330c4-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="330c4-117">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="330c4-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
