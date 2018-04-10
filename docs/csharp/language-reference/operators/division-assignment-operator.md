---
title: Operador /= (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 26096d9b5dfc565c9933f1ed8ffb241dc900d9ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="72d24-102">Operador /= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="72d24-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="72d24-103">O operador de atribuição de divisão.</span><span class="sxs-lookup"><span data-stu-id="72d24-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="72d24-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="72d24-104">Remarks</span></span>  
 <span data-ttu-id="72d24-105">Uma expressão que usa o operador de atribuição `/=`, como</span><span class="sxs-lookup"><span data-stu-id="72d24-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```  
x /= y  
```  
  
 <span data-ttu-id="72d24-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="72d24-106">is equivalent to</span></span>  
  
```  
x = x / y  
```  
  
 <span data-ttu-id="72d24-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="72d24-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="72d24-108">O [operador /](../../../csharp/language-reference/operators/division-operator.md) é predefinido para que os tipos numéricos executem divisão.</span><span class="sxs-lookup"><span data-stu-id="72d24-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="72d24-109">O operador `/=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador /](../../../csharp/language-reference/operators/division-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="72d24-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="72d24-110">Em todos os operadores de atribuição composta, sobrecarregar o operador binário implicitamente sobrecarrega a atribuição composta equivalente.</span><span class="sxs-lookup"><span data-stu-id="72d24-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="72d24-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="72d24-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="72d24-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72d24-112">See Also</span></span>  
 [<span data-ttu-id="72d24-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="72d24-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="72d24-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="72d24-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="72d24-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="72d24-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
