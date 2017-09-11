---
title: "Operador -- (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- --_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- -- operator [C#]
- decrement operator (--) [C#]
ms.assetid: 6b9cfe86-63c7-421f-9379-c9690fea8720
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
ms.openlocfilehash: 100e68f3b07164b0cfb398a32f47137f2726943f
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="---operator-c-reference"></a><span data-ttu-id="1df67-102">Operador -- (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="1df67-102">-- Operator (C# Reference)</span></span>
<span data-ttu-id="1df67-103">O operador de decremento (`--`) decrementa o operando em 1.</span><span class="sxs-lookup"><span data-stu-id="1df67-103">The decrement operator (`--`) decrements its operand by 1.</span></span> <span data-ttu-id="1df67-104">O operador de decremento pode aparecer antes ou depois de seu operando: `--variable` e `variable--`.</span><span class="sxs-lookup"><span data-stu-id="1df67-104">The decrement operator can appear before or after its operand: `--variable` and `variable--`.</span></span> <span data-ttu-id="1df67-105">A primeira forma é uma operação de decremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="1df67-105">The first form is a prefix decrement operation.</span></span> <span data-ttu-id="1df67-106">O resultado da operação será o valor do operando "depois" que ele for decrementado.</span><span class="sxs-lookup"><span data-stu-id="1df67-106">The result of the operation is the value of the operand "after" it has been decremented.</span></span> <span data-ttu-id="1df67-107">A segunda forma é uma operação de decremento sufixo.</span><span class="sxs-lookup"><span data-stu-id="1df67-107">The second form is a postfix decrement operation.</span></span> <span data-ttu-id="1df67-108">O resultado da operação será o valor do operando "antes" de ser decrementado.</span><span class="sxs-lookup"><span data-stu-id="1df67-108">The result of the operation is the value of the operand "before" it has been decremented.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1df67-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="1df67-109">Remarks</span></span>  
 <span data-ttu-id="1df67-110">Tipos numéricos e de enumeração têm operadores de decremento predefinidos.</span><span class="sxs-lookup"><span data-stu-id="1df67-110">Numeric and enumeration types have predefined decrement operators.</span></span>  
  
 <span data-ttu-id="1df67-111">Os tipos definidos pelo usuário podem sobrecarregar o operador `--` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="1df67-111">User-defined types can overload the `--` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="1df67-112">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="1df67-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1df67-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1df67-113">Example</span></span>  
 <span data-ttu-id="1df67-114">[!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="1df67-114">[!code-cs[csRefOperators#8](../../../csharp/language-reference/operators/codesnippet/CSharp/decrement-operator_1.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1df67-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1df67-115">See Also</span></span>  
 <span data-ttu-id="1df67-116">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="1df67-116">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="1df67-117">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="1df67-117">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="1df67-118">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="1df67-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)

