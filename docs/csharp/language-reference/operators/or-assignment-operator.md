---
title: Operador |= – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: ad8d5c8e65c2768d1dfc4644323e801189a4399c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53245331"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="566c2-102">Operador |= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="566c2-102">|= Operator (C# Reference)</span></span>
<span data-ttu-id="566c2-103">O operador de atribuição OR.</span><span class="sxs-lookup"><span data-stu-id="566c2-103">The OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="566c2-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="566c2-104">Remarks</span></span>  
 <span data-ttu-id="566c2-105">Uma expressão que usa o operador de atribuição `|=`, como</span><span class="sxs-lookup"><span data-stu-id="566c2-105">An expression using the `|=` assignment operator, such as</span></span>  
  
```csharp  
x |= y  
```  
  
 <span data-ttu-id="566c2-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="566c2-106">is equivalent to</span></span>  
  
```csharp  
x = x | y  
```  
  
 <span data-ttu-id="566c2-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="566c2-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="566c2-108">O [operador &#124;](../../../csharp/language-reference/operators/or-operator.md) executa uma operação OR lógica bit a bit em operandos integrais e OR lógica em operandos bool.</span><span class="sxs-lookup"><span data-stu-id="566c2-108">The [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) performs a bitwise logical OR operation on integral operands and logical OR on bool operands.</span></span>  
  
 <span data-ttu-id="566c2-109">O operador `|=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador &#124;](../../../csharp/language-reference/operators/or-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="566c2-109">The `|=` operator cannot be overloaded directly, but user-defined types can overload the [&#124; operator](../../../csharp/language-reference/operators/or-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="566c2-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="566c2-110">Example</span></span>  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="566c2-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="566c2-111">See Also</span></span>

- [<span data-ttu-id="566c2-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="566c2-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="566c2-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="566c2-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="566c2-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="566c2-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
