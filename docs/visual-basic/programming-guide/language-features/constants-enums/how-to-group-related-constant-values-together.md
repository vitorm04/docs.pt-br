---
title: Como agrupar valores constantes relacionados
ms.date: 07/20/2015
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
ms.openlocfilehash: 0f694aee722e8ce31f663ec9fe52a09a2eb2a958
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058723"
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="bafbc-102">Como agrupar valores constantes relacionados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bafbc-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>

<span data-ttu-id="bafbc-103">Uma enumeração é a melhor maneira de agrupar constantes relacionadas juntas.</span><span class="sxs-lookup"><span data-stu-id="bafbc-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="bafbc-104">Você cria uma enumeração com a `Enum` instrução na seção declarações de uma classe ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="bafbc-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="bafbc-105">Para obter mais informações, consulte [como: declarar uma enumeração](how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="bafbc-105">For more information, see [How to: Declare an Enumeration](how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="bafbc-106">Para agrupar valores constantes relacionados</span><span class="sxs-lookup"><span data-stu-id="bafbc-106">To group related constant values</span></span>  
  
1. <span data-ttu-id="bafbc-107">Escreva uma declaração que inclua um nível de acesso de código, a `Enum` palavra-chave e um nome válido.</span><span class="sxs-lookup"><span data-stu-id="bafbc-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="bafbc-108">Este exemplo cria a `Private` enumeração, `temperatureValues` .</span><span class="sxs-lookup"><span data-stu-id="bafbc-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#21)]  
  
2. <span data-ttu-id="bafbc-109">Defina as constantes na enumeração.</span><span class="sxs-lookup"><span data-stu-id="bafbc-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="bafbc-110">Este exemplo cria a `Public` enumeração `temperatureValues` e atribui seus valores.</span><span class="sxs-lookup"><span data-stu-id="bafbc-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbEnumsTask/VB/Class2.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bafbc-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="bafbc-111">See also</span></span>

- [<span data-ttu-id="bafbc-112">Enumerações e qualificação de nome</span><span class="sxs-lookup"><span data-stu-id="bafbc-112">Enumerations and Name Qualification</span></span>](enumerations-and-name-qualification.md)
- [<span data-ttu-id="bafbc-113">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="bafbc-113">How to: Refer to an Enumeration Member</span></span>](how-to-refer-to-an-enumeration-member.md)
- [<span data-ttu-id="bafbc-114">Quando usar uma enumeração</span><span class="sxs-lookup"><span data-stu-id="bafbc-114">When to Use an Enumeration</span></span>](when-to-use-an-enumeration.md)
- [<span data-ttu-id="bafbc-115">Visão geral de constantes</span><span class="sxs-lookup"><span data-stu-id="bafbc-115">Constants Overview</span></span>](constants-overview.md)
- [<span data-ttu-id="bafbc-116">Tipos de dados constante e literal</span><span class="sxs-lookup"><span data-stu-id="bafbc-116">Constant and Literal Data Types</span></span>](constant-and-literal-data-types.md)
- [<span data-ttu-id="bafbc-117">Constantes e enumerações</span><span class="sxs-lookup"><span data-stu-id="bafbc-117">Constants and Enumerations</span></span>](../../../language-reference/constants-and-enumerations.md)
