---
title: Como agrupar valores constantes relacionados
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: d2393af8b0c2b0c2e528f9908a78fbc7f182c8cf
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414434"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="589e1-102">Como agrupar valores constantes relacionados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="589e1-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="589e1-103">Uma enumeração é a melhor maneira de agrupar constantes relacionadas juntas.</span><span class="sxs-lookup"><span data-stu-id="589e1-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="589e1-104">Você cria uma enumeração com a `Enum` instrução na seção declarações de uma classe ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="589e1-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="589e1-105">Para obter mais informações, consulte [como: declarar uma enumeração](how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="589e1-105">For more information, see [How to: Declare an Enumeration](how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="589e1-106">Para agrupar valores constantes relacionados</span><span class="sxs-lookup"><span data-stu-id="589e1-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="589e1-107">Escreva uma declaração que inclua um nível de acesso de código, a `Enum` palavra-chave e um nome válido.</span><span class="sxs-lookup"><span data-stu-id="589e1-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="589e1-108">Este exemplo cria a `Private` enumeração, `temperatureValues` .</span><span class="sxs-lookup"><span data-stu-id="589e1-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="589e1-109">Defina as constantes na enumeração.</span><span class="sxs-lookup"><span data-stu-id="589e1-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="589e1-110">Este exemplo cria a `Public` enumeração `temperatureValues` e atribui seus valores.</span><span class="sxs-lookup"><span data-stu-id="589e1-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="589e1-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="589e1-111">See also</span></span>

- [<span data-ttu-id="589e1-112">Enumerações e qualificação de nome</span><span class="sxs-lookup"><span data-stu-id="589e1-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="589e1-113">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="589e1-113">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="589e1-114">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="589e1-114">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="589e1-115">Visão geral de constantes</span><span class="sxs-lookup"><span data-stu-id="589e1-115">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="589e1-116">Tipos de dados constante e literal</span><span class="sxs-lookup"><span data-stu-id="589e1-116">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="589e1-117">Constantes e enumerações</span><span class="sxs-lookup"><span data-stu-id="589e1-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
