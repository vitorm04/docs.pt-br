---
title: 'Como: Agrupar valores constantes relacionados juntos (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 04697092534daa6f83a29e69dcdc509644fa6147
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54558677"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="0769a-102">Como: Agrupar valores constantes relacionados juntos (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0769a-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="0769a-103">Uma enumeração é a melhor maneira de agrupar constantes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="0769a-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="0769a-104">Você cria uma enumeração com o `Enum` instrução na seção de declarações de uma classe ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="0769a-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="0769a-105">Para obter mais informações, confira [Como: Declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="0769a-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="0769a-106">Para o grupo de valores constantes relacionados</span><span class="sxs-lookup"><span data-stu-id="0769a-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="0769a-107">Escrever uma declaração que inclui um nível de acesso do código, o `Enum` palavra-chave e um nome válido.</span><span class="sxs-lookup"><span data-stu-id="0769a-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="0769a-108">Este exemplo cria o `Private` enumeração, `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="0769a-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="0769a-109">Defina as constantes na enumeração.</span><span class="sxs-lookup"><span data-stu-id="0769a-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="0769a-110">Este exemplo cria o `Public` enumeração `temperatureValues` e atribui seus valores.</span><span class="sxs-lookup"><span data-stu-id="0769a-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="0769a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0769a-111">See also</span></span>
- [<span data-ttu-id="0769a-112">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="0769a-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)
- [<span data-ttu-id="0769a-113">Como: Fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="0769a-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="0769a-114">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="0769a-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)
- [<span data-ttu-id="0769a-115">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="0769a-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)
- [<span data-ttu-id="0769a-116">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="0769a-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)
- [<span data-ttu-id="0769a-117">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="0769a-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
