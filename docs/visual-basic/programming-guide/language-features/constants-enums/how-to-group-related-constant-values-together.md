---
title: Como agrupar valores constantes relacionados (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- enumerations [Visual Basic], constants
- constants [Visual Basic], grouping together
ms.assetid: 09d61da5-c940-4126-a79f-ba93c36653dc
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: be57b56047654d6eb3536bb0b8f63eca27decdb7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-group-related-constant-values-together-visual-basic"></a><span data-ttu-id="dc68d-102">Como agrupar valores constantes relacionados (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="dc68d-102">How to: Group Related Constant Values Together (Visual Basic)</span></span>
<span data-ttu-id="dc68d-103">Uma enumeração é a melhor maneira de agrupar constantes relacionadas.</span><span class="sxs-lookup"><span data-stu-id="dc68d-103">An enumeration is the best way to group related constants together.</span></span> <span data-ttu-id="dc68d-104">Você cria uma enumeração com o `Enum` instrução na seção de declarações de uma classe ou um módulo.</span><span class="sxs-lookup"><span data-stu-id="dc68d-104">You create an enumeration with the `Enum` statement in the declarations section of a class or a module.</span></span> <span data-ttu-id="dc68d-105">Para obter mais informações, consulte [como: declarar uma enumeração](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span><span class="sxs-lookup"><span data-stu-id="dc68d-105">For more information, see [How to: Declare an Enumeration](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-declare-enumerations.md).</span></span>  
  
### <a name="to-group-related-constant-values"></a><span data-ttu-id="dc68d-106">Para o grupo de valores constantes relacionados</span><span class="sxs-lookup"><span data-stu-id="dc68d-106">To group related constant values</span></span>  
  
1.  <span data-ttu-id="dc68d-107">Escreva uma declaração que inclui um nível de acesso do código, o `Enum` palavra-chave e um nome válido.</span><span class="sxs-lookup"><span data-stu-id="dc68d-107">Write a declaration that includes a code access level, the `Enum` keyword, and a valid name.</span></span> <span data-ttu-id="dc68d-108">Este exemplo cria o `Private` enumeração `temperatureValues`.</span><span class="sxs-lookup"><span data-stu-id="dc68d-108">This example creates the `Private` enumeration, `temperatureValues`.</span></span>  
  
     [!code-vb[VbEnumsTask#21](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_1.vb)]  
  
2.  <span data-ttu-id="dc68d-109">Defina as constantes na enumeração.</span><span class="sxs-lookup"><span data-stu-id="dc68d-109">Define the constants in the enumeration.</span></span> <span data-ttu-id="dc68d-110">Este exemplo cria o `Public` enumeração `temperatureValues` e atribui seus valores.</span><span class="sxs-lookup"><span data-stu-id="dc68d-110">This example creates the `Public` enumeration `temperatureValues` and assigns its values.</span></span>  
  
     [!code-vb[VbEnumsTask#1](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-group-related-constant-values-together_2.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="dc68d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc68d-111">See Also</span></span>  
 [<span data-ttu-id="dc68d-112">Enumerações e Qualificação de Nome</span><span class="sxs-lookup"><span data-stu-id="dc68d-112">Enumerations and Name Qualification</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/enumerations-and-name-qualification.md)  
 [<span data-ttu-id="dc68d-113">Como fazer referência a um membro de enumeração</span><span class="sxs-lookup"><span data-stu-id="dc68d-113">How to: Refer to an Enumeration Member</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/how-to-refer-to-an-enumeration-member.md)  
 [<span data-ttu-id="dc68d-114">Quando Usar uma Enumeração</span><span class="sxs-lookup"><span data-stu-id="dc68d-114">When to Use an Enumeration</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/when-to-use-an-enumeration.md)  
 [<span data-ttu-id="dc68d-115">Visão Geral de Constantes</span><span class="sxs-lookup"><span data-stu-id="dc68d-115">Constants Overview</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constants-overview.md)  
 [<span data-ttu-id="dc68d-116">Tipos de Dados Constante e Literal</span><span class="sxs-lookup"><span data-stu-id="dc68d-116">Constant and Literal Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/constants-enums/constant-and-literal-data-types.md)  
 [<span data-ttu-id="dc68d-117">Constantes e Enumerações</span><span class="sxs-lookup"><span data-stu-id="dc68d-117">Constants and Enumerations</span></span>](../../../../visual-basic/language-reference/constants-and-enumerations.md)
