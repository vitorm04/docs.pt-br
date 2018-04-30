---
title: Operador % (Referência de C#)
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '%_CSharpKeyword'
helpviewer_keywords:
- remainder operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 796b4a40347fc5881db27a8a8a28404c7c4e8c5b
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="78539-102">Operador % (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="78539-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="78539-103">O operador de resto (`%`) calcula o resto após dividir o primeiro operando pelo segundo.</span><span class="sxs-lookup"><span data-stu-id="78539-103">The remainder operator (`%`) computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="78539-104">Todos os tipos numéricos têm operadores de restante predefinidos.</span><span class="sxs-lookup"><span data-stu-id="78539-104">All numeric types have predefined remainder operators.</span></span> 
  
## <a name="remarks"></a><span data-ttu-id="78539-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="78539-105">Remarks</span></span>  
 <span data-ttu-id="78539-106">A fórmula `a % b` sempre retornará um valor no intervalo `(-b, b)`, exclusivo (nunca pode retornar `b` ou `-b`), mantendo o sinal do dividendo.</span><span class="sxs-lookup"><span data-stu-id="78539-106">The formula `a % b` will always return a value on the range `(-b, b)`, exclusive (it can never return `b` or `-b`), keeping the sign of the dividend.</span></span> <span data-ttu-id="78539-107">Para a divisão de inteiros, o operador de resto satisfaz a regra `a % b = a - (a / b) * b`.</span><span class="sxs-lookup"><span data-stu-id="78539-107">For integer division, the remainder operator satisfies the rule `a % b = a - (a / b) * b`.</span></span>
  
 <span data-ttu-id="78539-108">Não deve ser confundido com o módulo canônico, que satisfaz uma regra semelhante, mas com a divisão de piso, e retorna os valores no intervalo `[0, b)`.</span><span class="sxs-lookup"><span data-stu-id="78539-108">This is not to be confused with canonical modulus, which satisfies a similar rule but with floored division and returns values on the range `[0, b)`.</span></span> <span data-ttu-id="78539-109">O C# não tem um operador para o módulo canônico.</span><span class="sxs-lookup"><span data-stu-id="78539-109">C# does not have an operator for canonical modulus.</span></span> <span data-ttu-id="78539-110">No entanto, o comportamento é o mesmo para dividendos positivos.</span><span class="sxs-lookup"><span data-stu-id="78539-110">However, the behavior is the same for positive dividends.</span></span>
  
 <span data-ttu-id="78539-111">Os tipos definidos pelo usuário podem sobrecarregar o operador `%` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="78539-111">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="78539-112">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="78539-112">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="78539-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="78539-113">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/remainder-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="78539-114">Comentários</span><span class="sxs-lookup"><span data-stu-id="78539-114">Comments</span></span>  
 <span data-ttu-id="78539-115">Observe os erros de arredondamento associados ao tipo double.</span><span class="sxs-lookup"><span data-stu-id="78539-115">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="78539-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="78539-116">See Also</span></span>  
 [<span data-ttu-id="78539-117">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="78539-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="78539-118">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="78539-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="78539-119">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="78539-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
