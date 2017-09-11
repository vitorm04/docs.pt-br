---
title: "Operador &lt;&lt;= (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <<=_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- <<= operator (left-shift assignment) [C#]
- left shift assignment operator (<<=) [C#]
ms.assetid: 3bc99c78-1edb-4827-86fc-bce6c3048871
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
ms.openlocfilehash: fd562a538891a5592cc724e74cffb3d086248898
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="ltlt-operator-c-reference"></a><span data-ttu-id="fe1f0-102">Operador &lt;&lt;= (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="fe1f0-102">&lt;&lt;= Operator (C# Reference)</span></span>
<span data-ttu-id="fe1f0-103">O operador de atribuição de deslocamento para a esquerda.</span><span class="sxs-lookup"><span data-stu-id="fe1f0-103">The left-shift assignment operator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="fe1f0-104">Comentários</span><span class="sxs-lookup"><span data-stu-id="fe1f0-104">Remarks</span></span>  
 <span data-ttu-id="fe1f0-105">Uma expressão da forma</span><span class="sxs-lookup"><span data-stu-id="fe1f0-105">An expression of the form</span></span>  
  
```  
x <<= y  
```  
  
 <span data-ttu-id="fe1f0-106">é avaliada como</span><span class="sxs-lookup"><span data-stu-id="fe1f0-106">is evaluated as</span></span>  
  
```  
x = x << y  
```  
  
 <span data-ttu-id="fe1f0-107">exceto que `x` é avaliado apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="fe1f0-107">except that `x` is only evaluated once.</span></span> <span data-ttu-id="fe1f0-108">O [operador <<](../../../csharp/language-reference/operators/left-shift-operator.md) desloca `x` para a esquerda pelo número de bits especificado pelo `y`.</span><span class="sxs-lookup"><span data-stu-id="fe1f0-108">The [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) shifts `x` left by the number of bits specified by `y`.</span></span>  
  
 <span data-ttu-id="fe1f0-109">O operador `<<=` não pode ser sobrecarregado diretamente, mas tipos definidos pelo usuário podem sobrecarregar o [operador <<](../../../csharp/language-reference/operators/left-shift-operator.md) (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="fe1f0-109">The `<<=` operator cannot be overloaded directly, but user-defined types can overload the [<< operator](../../../csharp/language-reference/operators/left-shift-operator.md) (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe1f0-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fe1f0-110">Example</span></span>  
 <span data-ttu-id="fe1f0-111">[!code-cs[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="fe1f0-111">[!code-cs[csRefOperators#12](../../../csharp/language-reference/operators/codesnippet/CSharp/left-shift-assignment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe1f0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fe1f0-112">See Also</span></span>  
 <span data-ttu-id="fe1f0-113">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="fe1f0-113">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="fe1f0-114">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="fe1f0-114">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="fe1f0-115">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="fe1f0-115">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

