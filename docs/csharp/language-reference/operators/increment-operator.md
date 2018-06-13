---
title: Operador ++ (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: 0fe1150ca7267d02feeab33168eab7f79734c2a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33275058"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="6e182-102">Operador ++ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6e182-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="6e182-103">O operador de incremento (`++`) incrementa seu operando em 1.</span><span class="sxs-lookup"><span data-stu-id="6e182-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="6e182-104">O operador de incremento pode ser exibido antes ou depois de seu operando: `++variable` e `variable++`.</span><span class="sxs-lookup"><span data-stu-id="6e182-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6e182-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="6e182-105">Remarks</span></span>  
 <span data-ttu-id="6e182-106">A primeira forma é uma operação de incremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="6e182-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="6e182-107">O resultado da operação será o valor do operando "depois" que ele for incrementado.</span><span class="sxs-lookup"><span data-stu-id="6e182-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="6e182-108">A segunda forma é uma operação de incremento pós-fixada.</span><span class="sxs-lookup"><span data-stu-id="6e182-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="6e182-109">O resultado da operação será o valor do operando antes de ser incrementado.</span><span class="sxs-lookup"><span data-stu-id="6e182-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="6e182-110">Tipos numéricos e de enumeração têm operadores de incremento predefinidos.</span><span class="sxs-lookup"><span data-stu-id="6e182-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="6e182-111">Os tipos definidos pelo usuário podem sobrecarregar o operador `++`.</span><span class="sxs-lookup"><span data-stu-id="6e182-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="6e182-112">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="6e182-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6e182-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6e182-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="6e182-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6e182-114">See Also</span></span>  
 [<span data-ttu-id="6e182-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="6e182-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6e182-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6e182-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6e182-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="6e182-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
