---
title: Operador ^= (Referência de C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8d4de06dbfd269dc5e0f2cc5003e8981068220a1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="06100-102">Operador ^= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="06100-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="06100-103">O operador de atribuição OR exclusivo.</span><span class="sxs-lookup"><span data-stu-id="06100-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="06100-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="06100-104">Remarks</span></span>  
 <span data-ttu-id="06100-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="06100-105">An expression of the form</span></span>  
  
```  
x ^= y  
```  
  
 <span data-ttu-id="06100-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="06100-106">is evaluated as</span></span>  
  
```  
x = x ^ y  
```  
  
 <span data-ttu-id="06100-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="06100-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="06100-108">O [operador ^](../../../csharp/language-reference/operators/xor-operator.md) realiza uma operação OR exclusiva bit a bit em operandos integrais e OR exclusiva lógica em operandos [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="06100-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="06100-109">O operador ^= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador ^](../../../csharp/language-reference/operators/xor-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="06100-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="06100-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="06100-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="06100-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="06100-111">See Also</span></span>  
 [<span data-ttu-id="06100-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="06100-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="06100-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="06100-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="06100-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="06100-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
