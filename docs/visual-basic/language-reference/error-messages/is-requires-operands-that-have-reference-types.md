---
title: '&#39;É&#39; requer operandos que tenham tipos de referência, mas este operando tem o tipo de valor &#39; &lt;typename&gt;&#39;'
ms.date: 07/20/2015
f1_keywords:
- bc30020
- vbc30020
helpviewer_keywords:
- BC30020
ms.assetid: 228afebd-1203-4bd3-8d7a-c5c56f3cedc4
ms.openlocfilehash: 0b3f80e98087e455ec730dea8c57478528e9259c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722914"
---
# <a name="39is39-requires-operands-that-have-reference-types-but-this-operand-has-the-value-type-39lttypenamegt39"></a><span data-ttu-id="9fa0e-102">&#39;É&#39; requer operandos que tenham tipos de referência, mas este operando tem o tipo de valor &#39; &lt;typename&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="9fa0e-102">&#39;Is&#39; requires operands that have reference types, but this operand has the value type &#39;&lt;typename&gt;&#39;</span></span>
<span data-ttu-id="9fa0e-103">O `Is` operador de comparação que determina se duas variáveis de objeto se referem à mesma instância.</span><span class="sxs-lookup"><span data-stu-id="9fa0e-103">The `Is` comparison operator determines whether two object variables refer to the same instance.</span></span> <span data-ttu-id="9fa0e-104">Essa comparação não está definida para tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="9fa0e-104">This comparison is not defined for value types.</span></span>  
  
 <span data-ttu-id="9fa0e-105">**ID do erro:** BC30020</span><span class="sxs-lookup"><span data-stu-id="9fa0e-105">**Error ID:** BC30020</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="9fa0e-106">Para corrigir este erro</span><span class="sxs-lookup"><span data-stu-id="9fa0e-106">To correct this error</span></span>  
  
-   <span data-ttu-id="9fa0e-107">Use o operador de comparação aritmética apropriado ou o `Like` operador para comparar dois tipos de valor.</span><span class="sxs-lookup"><span data-stu-id="9fa0e-107">Use the appropriate arithmetic comparison operator or the `Like` operator to compare two value types.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa0e-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9fa0e-108">See also</span></span>
- [<span data-ttu-id="9fa0e-109">Operador Is</span><span class="sxs-lookup"><span data-stu-id="9fa0e-109">Is Operator</span></span>](../../../visual-basic/language-reference/operators/is-operator.md)
- [<span data-ttu-id="9fa0e-110">Operador Like</span><span class="sxs-lookup"><span data-stu-id="9fa0e-110">Like Operator</span></span>](../../../visual-basic/language-reference/operators/like-operator.md)
- [<span data-ttu-id="9fa0e-111">Operadores de Comparação</span><span class="sxs-lookup"><span data-stu-id="9fa0e-111">Comparison Operators</span></span>](../../../visual-basic/language-reference/operators/comparison-operators.md)
