---
title: Operador ^= (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: d6546f23ffb6dee792339a7e3863bf58ae668d58
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43857226"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="b9702-102">Operador ^= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b9702-102">^= Operator (C# Reference)</span></span>
<span data-ttu-id="b9702-103">O operador de atribuição OR exclusivo.</span><span class="sxs-lookup"><span data-stu-id="b9702-103">The exclusive-OR assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b9702-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9702-104">Remarks</span></span>  
 <span data-ttu-id="b9702-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="b9702-105">An expression of the form</span></span>  
  
```csharp  
x ^= y  
```  
  
 <span data-ttu-id="b9702-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="b9702-106">is evaluated as</span></span>  
  
```csharp  
x = x ^ y  
```  
  
 <span data-ttu-id="b9702-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="b9702-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="b9702-108">O [operador ^](../../../csharp/language-reference/operators/xor-operator.md) realiza uma operação OR exclusiva bit a bit em operandos integrais e OR exclusiva lógica em operandos [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="b9702-108">The [^ operator](../../../csharp/language-reference/operators/xor-operator.md) performs a bitwise exclusive-OR operation on integral operands and logical exclusive-OR on [bool](../../../csharp/language-reference/keywords/bool.md) operands.</span></span>  
  
 <span data-ttu-id="b9702-109">O operador ^= não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador ^](../../../csharp/language-reference/operators/xor-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="b9702-109">The ^= operator cannot be overloaded directly, but user-defined types can overload the [^ operator](../../../csharp/language-reference/operators/xor-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9702-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9702-110">Example</span></span>  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="b9702-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9702-111">See Also</span></span>

- [<span data-ttu-id="b9702-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b9702-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b9702-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b9702-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b9702-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="b9702-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
