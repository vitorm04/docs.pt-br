---
title: "'Is' requer operandos que tenham tipos de referência, mas este operando tem o tipo de valor '<typename>'"
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 5c9f156272cd0c3cbaeadbc0e162129f41619cc6
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92163344"
---
# <a name="bc30020-is-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-typename"></a><span data-ttu-id="8b1ee-102">BC30020: ' is ' requer operandos que têm tipos de referência, mas esse operando tem o tipo de valor ' \<typename> '</span><span class="sxs-lookup"><span data-stu-id="8b1ee-102">BC30020: 'Is' requires operands that have reference types, but this operand has the value type '\<typename>'</span></span>

<span data-ttu-id="8b1ee-103">O `Is` operador de comparação determina se duas variáveis de objeto se referem à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="8b1ee-104">Essa comparação não é definida para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-104">This comparison is not defined for value types.</span></span>

 <span data-ttu-id="8b1ee-105">**ID do erro:** BC30020</span><span class="sxs-lookup"><span data-stu-id="8b1ee-105">**Error ID:** BC30020</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="8b1ee-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="8b1ee-106">To correct this error</span></span>

- <span data-ttu-id="8b1ee-107">Use o operador de comparação aritmético apropriado ou o `Like` operador para comparar dois tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="8b1ee-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>

## <a name="see-also"></a><span data-ttu-id="8b1ee-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="8b1ee-108">See also</span></span>

- [<span data-ttu-id="8b1ee-109">Operador Is</span><span class="sxs-lookup"><span data-stu-id="8b1ee-109">Is Operator</span></span>](../operators/is-operator.md)
- [<span data-ttu-id="8b1ee-110">Operador Like</span><span class="sxs-lookup"><span data-stu-id="8b1ee-110">Like Operator</span></span>](../operators/like-operator.md)
- [<span data-ttu-id="8b1ee-111">Operadores de comparação</span><span class="sxs-lookup"><span data-stu-id="8b1ee-111">Comparison Operators</span></span>](../operators/comparison-operators.md)
