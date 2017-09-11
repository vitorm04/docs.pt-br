---
title: "Operador *= (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*=_CSharpKeyword'
dev_langs:
- CSharp
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 2969ba3ce303da591353fd0114dccf752e63f2c3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="8dc5a-102">Operador *= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8dc5a-102">*= Operator (C# Reference)</span></span>
<span data-ttu-id="8dc5a-103">O operador de atribuição de multiplicação binária.</span><span class="sxs-lookup"><span data-stu-id="8dc5a-103">The binary multiplication assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8dc5a-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="8dc5a-104">Remarks</span></span>  
 <span data-ttu-id="8dc5a-105">Uma expressão que usa o operador de atribuição `*=`, como</span><span class="sxs-lookup"><span data-stu-id="8dc5a-105">An expression using the `*=` assignment operator, such as</span></span>  
  
```  
x *= y  
```  
  
 <span data-ttu-id="8dc5a-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="8dc5a-106">is equivalent to</span></span>  
  
```  
x = x * y  
```  
  
 <span data-ttu-id="8dc5a-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="8dc5a-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="8dc5a-108">O [* operador](../../../csharp/language-reference/operators/multiplication-operator.md) é predefinido para que os tipos numéricos executem multiplicação.</span><span class="sxs-lookup"><span data-stu-id="8dc5a-108">The [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) is predefined for numeric types to perform multiplication.</span></span>  
  
 <span data-ttu-id="8dc5a-109">O operador `*=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador *](../../../csharp/language-reference/operators/multiplication-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="8dc5a-109">The `*=` operator cannot be overloaded directly, but user-defined types can overload the [* operator](../../../csharp/language-reference/operators/multiplication-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8dc5a-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8dc5a-110">Example</span></span>  
 <span data-ttu-id="8dc5a-111">[!code-cs[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8dc5a-111">[!code-cs[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8dc5a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8dc5a-112">See Also</span></span>  
 <span data-ttu-id="8dc5a-113">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="8dc5a-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="8dc5a-114">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8dc5a-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="8dc5a-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="8dc5a-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

