---
title: "'Is' requer operandos que tenham tipos de referência, mas este operando tem o tipo de valor '<typename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: daf9724fef81b4d7adb4f571ee950723aec09d8d
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90873911"
---
# <a name="is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="8f498-102">'Is' requer operandos que tenham tipos de referência, mas este operando tem o tipo de valor '\<typename>'</span><span class="sxs-lookup"><span data-stu-id="8f498-102">'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="8f498-103">O `Is` operador de comparação determina se duas variáveis de objeto se referem à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="8f498-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="8f498-104">Essa comparação não é definida para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="8f498-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="8f498-105">**ID do erro:** BC30020</span><span class="sxs-lookup"><span data-stu-id="8f498-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="8f498-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8f498-106">To correct this error</span></span>  
  
- <span data-ttu-id="8f498-107">Use o operador de comparação aritmético apropriado ou o `Like` operador para comparar dois tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="8f498-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8f498-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="8f498-108">See also</span></span>

- [<span data-ttu-id="8f498-109">Operador Is</span><span class="sxs-lookup"><span data-stu-id="8f498-109">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="8f498-110">Operador Like</span><span class="sxs-lookup"><span data-stu-id="8f498-110">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="8f498-111">Operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="8f498-111">Comparison Operators</span></span>](../operators/comparison-operators.md)
