---
title: "Operador /= (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
caps.latest.revision: 17
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
ms.openlocfilehash: 5e105bf11f5413d77d62be4177ed22ba420312c3
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="d0679-102">Operador /= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d0679-102">/= Operator (C# Reference)</span></span>
<span data-ttu-id="d0679-103">O operador de atribuição de divisão.</span><span class="sxs-lookup"><span data-stu-id="d0679-103">The division assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0679-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0679-104">Remarks</span></span>  
 <span data-ttu-id="d0679-105">Uma expressão que usa o operador de atribuição `/=`, como</span><span class="sxs-lookup"><span data-stu-id="d0679-105">An expression using the `/=` assignment operator, such as</span></span>  
  
```  
x /= y  
```  
  
 <span data-ttu-id="d0679-106">equivale a</span><span class="sxs-lookup"><span data-stu-id="d0679-106">is equivalent to</span></span>  
  
```  
x = x / y  
```  
  
 <span data-ttu-id="d0679-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="d0679-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="d0679-108">O [operador /](../../../csharp/language-reference/operators/division-operator.md) é predefinido para que os tipos numéricos executem divisão.</span><span class="sxs-lookup"><span data-stu-id="d0679-108">The [/ operator](../../../csharp/language-reference/operators/division-operator.md) is predefined for numeric types to perform division.</span></span>  
  
 <span data-ttu-id="d0679-109">O operador `/=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador /](../../../csharp/language-reference/operators/division-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d0679-109">The `/=` operator cannot be overloaded directly, but user-defined types can overload the [/ operator](../../../csharp/language-reference/operators/division-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="d0679-110">Em todos os operadores de atribuição composta, sobrecarregar o operador binário implicitamente sobrecarrega a atribuição composta equivalente.</span><span class="sxs-lookup"><span data-stu-id="d0679-110">On all compound assignment operators, overloading the binary operator implicitly overloads the equivalent compound assignment.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d0679-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0679-111">Example</span></span>  
 <span data-ttu-id="d0679-112">[!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="d0679-112">[!code-cs[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0679-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d0679-113">See Also</span></span>  
 <span data-ttu-id="d0679-114">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="d0679-114">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="d0679-115">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="d0679-115">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="d0679-116">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="d0679-116">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

