---
title: Operador ++ (Referência de C#)
ms.date: 07/20/2015
f1_keywords:
- ++_CSharpKeyword
helpviewer_keywords:
- increment operator (++) [C#]
- ++ operator [C#]
ms.assetid: e9dec353-070b-44fb-98ed-eb8fdf753feb
ms.openlocfilehash: a52f614ce1bbfb8e9d9be686b277c1e69f6f9d35
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44274590"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="4478e-102">Operador ++ (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="4478e-102">++ Operator (C# Reference)</span></span>
<span data-ttu-id="4478e-103">O operador de incremento (`++`) incrementa seu operando em 1.</span><span class="sxs-lookup"><span data-stu-id="4478e-103">The increment operator (`++`) increments its operand by 1.</span></span> <span data-ttu-id="4478e-104">O operador de incremento pode ser exibido antes ou depois de seu operando: `++variable` e `variable++`.</span><span class="sxs-lookup"><span data-stu-id="4478e-104">The increment operator can appear before or after its operand: `++variable` and `variable++`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4478e-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="4478e-105">Remarks</span></span>  
 <span data-ttu-id="4478e-106">A primeira forma é uma operação de incremento de prefixo.</span><span class="sxs-lookup"><span data-stu-id="4478e-106">The first form is a prefix increment operation.</span></span> <span data-ttu-id="4478e-107">O resultado da operação será o valor do operando "depois" que ele for incrementado.</span><span class="sxs-lookup"><span data-stu-id="4478e-107">The result of the operation is the value of the operand after it has been incremented.</span></span>  
  
 <span data-ttu-id="4478e-108">A segunda forma é uma operação de incremento pós-fixada.</span><span class="sxs-lookup"><span data-stu-id="4478e-108">The second form is a postfix increment operation.</span></span> <span data-ttu-id="4478e-109">O resultado da operação será o valor do operando antes de ser incrementado.</span><span class="sxs-lookup"><span data-stu-id="4478e-109">The result of the operation is the value of the operand before it has been incremented.</span></span>  
  
 <span data-ttu-id="4478e-110">Tipos numéricos e de enumeração têm operadores de incremento predefinidos.</span><span class="sxs-lookup"><span data-stu-id="4478e-110">Numeric and enumeration types have predefined increment operators.</span></span> <span data-ttu-id="4478e-111">Os tipos definidos pelo usuário podem sobrecarregar o operador `++`.</span><span class="sxs-lookup"><span data-stu-id="4478e-111">User-defined types can overload the `++` operator.</span></span> <span data-ttu-id="4478e-112">As operações em tipos integrais geralmente são permitidas na enumeração.</span><span class="sxs-lookup"><span data-stu-id="4478e-112">Operations on integral types are generally allowed on enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4478e-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4478e-113">Example</span></span>  
 [!code-csharp[csRefOperators#3](../../../csharp/language-reference/operators/codesnippet/CSharp/increment-operator_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="4478e-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4478e-114">See Also</span></span>

- [<span data-ttu-id="4478e-115">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="4478e-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="4478e-116">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="4478e-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="4478e-117">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="4478e-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
