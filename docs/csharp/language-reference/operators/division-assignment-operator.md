---
title: Operador /= (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 8fff048cc441181aa3f0e3c0c638d501aaf9de3f
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/03/2018
ms.locfileid: "43477939"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6d4c0-102">Operador /= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6d4c0-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="6d4c0-103">O operador de atribuição de divisão.</span><span class="sxs-lookup"><span data-stu-id="6d4c0-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d4c0-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="6d4c0-104">Remarks</span></span>  
 <span data-ttu-id="6d4c0-105">Uma expressão que usa o operador de atribuição `/=`, como</span><span class="sxs-lookup"><span data-stu-id="6d4c0-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```csharp  
x /= y  
```  
  
 <span data-ttu-id="6d4c0-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="6d4c0-106">is equivalent to</span></span>  
  
```csharp  
x = x / y  
```  
  
 <span data-ttu-id="6d4c0-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="6d4c0-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="6d4c0-108">O [operador /](../../../csharp/language-reference/operators/division-operator.md) é predefinido para que os tipos numéricos executem divisão.</span><span class="sxs-lookup"><span data-stu-id="6d4c0-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="6d4c0-109">O operador `/=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador /](../../../csharp/language-reference/operators/division-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="6d4c0-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="6d4c0-110">Em todos os operadores de atribuição composta, sobrecarregar o operador binário implicitamente sobrecarrega a atribuição composta equivalente.</span><span class="sxs-lookup"><span data-stu-id="6d4c0-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6d4c0-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6d4c0-111">Example</span></span>  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6d4c0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d4c0-112">See Also</span></span>

- [<span data-ttu-id="6d4c0-113">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="6d4c0-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="6d4c0-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6d4c0-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="6d4c0-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="6d4c0-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
