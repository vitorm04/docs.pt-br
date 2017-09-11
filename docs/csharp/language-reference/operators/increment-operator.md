---
title: "Operador ++ (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ++_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 9f481dbe2437495b109d6d41cd24c8b4bb5b6a5b
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="-operator-c-reference"></a><span data-ttu-id="372e5-102">Operador ++ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="372e5-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="372e5-103">O operador de incremento (`++`) incrementa seu operando em 1.</span><span class="sxs-lookup"><span data-stu-id="372e5-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="372e5-104">O operador de incremento pode ser exibido antes ou depois de seu operando: `++variable` e `variable++`.</span><span class="sxs-lookup"><span data-stu-id="372e5-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="372e5-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="372e5-105">Remarks</span></span>  
 <span data-ttu-id="372e5-106">A primeira forma é uma operação de incremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="372e5-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="372e5-107">O resultado da operação será o valor do operando "depois" que ele for incrementado.</span><span class="sxs-lookup"><span data-stu-id="372e5-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="372e5-108">A segunda forma é uma operação de incremento pós-fixada.</span><span class="sxs-lookup"><span data-stu-id="372e5-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="372e5-109">O resultado da operação será o valor do operando antes de ser incrementado.</span><span class="sxs-lookup"><span data-stu-id="372e5-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="372e5-110">Tipos numéricos e de enumeração têm operadores de incremento predefinidos.</span><span class="sxs-lookup"><span data-stu-id="372e5-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="372e5-111">Os tipos definidos pelo usuário podem sobrecarregar o operador `++`.</span><span class="sxs-lookup"><span data-stu-id="372e5-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="372e5-112">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="372e5-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="372e5-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="372e5-113">Example</span></span>  
 <span data-ttu-id="372e5-114">[!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="372e5-114">[!code-cs[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="372e5-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="372e5-115">See Also</span></span>  
 <span data-ttu-id="372e5-116">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="372e5-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="372e5-117">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="372e5-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="372e5-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="372e5-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

