---
title: "Operador % (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '%_CSharpKeyword'
helpviewer_keywords:
- modulus operator [C#]
- '% operator [C#]'
ms.assetid: 3b74f4f9-fd9c-45e7-84fa-c8d71a0dfad7
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cea4aa03424e93f3ec144126d73c63931a737b54
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3863a-102">Operador % (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3863a-102">% Operator (C# Reference)</span></span>
<span data-ttu-id="3863a-103">O operador `%` calcula o restante após dividir o primeiro operando pelo segundo.</span><span class="sxs-lookup"><span data-stu-id="3863a-103">The `%` operator computes the remainder after dividing its first operand by its second.</span></span> <span data-ttu-id="3863a-104">Todos os tipos numéricos têm operadores de restante predefinidos.</span><span class="sxs-lookup"><span data-stu-id="3863a-104">All numeric types have predefined remainder operators.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3863a-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3863a-105">Remarks</span></span>  
 <span data-ttu-id="3863a-106">Os tipos definidos pelo usuário podem sobrecarregar o operador `%` (consulte [operador](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="3863a-106">User-defined types can overload the `%` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="3863a-107">Quando um operador binário está sobrecarregado, o operador de atribuição correspondente, se houver, também estará implicitamente sobrecarregado.</span><span class="sxs-lookup"><span data-stu-id="3863a-107">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3863a-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3863a-108">Example</span></span>  
 [!code-csharp[csRefOperators#9](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-operator_1.cs)]  
  
## <a name="comments"></a><span data-ttu-id="3863a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="3863a-109">Comments</span></span>  
 <span data-ttu-id="3863a-110">Observe os erros de arredondamento associados ao tipo double.</span><span class="sxs-lookup"><span data-stu-id="3863a-110">Note the round-off errors associated with the double type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3863a-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3863a-111">See Also</span></span>  
 [<span data-ttu-id="3863a-112">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3863a-112">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="3863a-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3863a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="3863a-114">Operadores do C#</span><span class="sxs-lookup"><span data-stu-id="3863a-114">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
