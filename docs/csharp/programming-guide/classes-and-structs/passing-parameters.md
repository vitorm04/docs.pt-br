---
title: "Passando parâmetros (Guia de Programação em C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
caps.latest.revision: "17"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d9e0e06d67f9da39c6b55f91e35d4a75b43353f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="77b7a-102">Passando parâmetros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="77b7a-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="77b7a-103">No C#, argumentos podem ser passados para parâmetros por valor ou por referência.</span><span class="sxs-lookup"><span data-stu-id="77b7a-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="77b7a-104">A passagem por referência permite que métodos, propriedades, indexadores, operadores, construtores e membros da função alterem o valor dos parâmetros e façam essa alteração persistir no ambiente de chamada.</span><span class="sxs-lookup"><span data-stu-id="77b7a-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="77b7a-105">Para passar um parâmetro por referência, use a palavra-chave `ref` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="77b7a-105">To pass a parameter by reference, use the `ref` or `out` keyword.</span></span> <span data-ttu-id="77b7a-106">Para simplificar, somente a palavra-chave `ref` é usada nos exemplos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="77b7a-106">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="77b7a-107">Para obter mais informações sobre a diferença entre `ref` e `out`, consulte [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md) e [Passando matrizes com o uso de ref e out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span><span class="sxs-lookup"><span data-stu-id="77b7a-107">For more information about the difference between `ref` and `out`, see [ref](../../../csharp/language-reference/keywords/ref.md), [out](../../../csharp/language-reference/keywords/out.md), and [Passing Arrays Using ref and out](../../../csharp/programming-guide/arrays/passing-arrays-using-ref-and-out.md).</span></span>  
  
 <span data-ttu-id="77b7a-108">O exemplo a seguir ilustra a diferença entre parâmetros de valor e referência.</span><span class="sxs-lookup"><span data-stu-id="77b7a-108">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="77b7a-109">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="77b7a-109">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="77b7a-110">Passando parâmetros de tipo de valor</span><span class="sxs-lookup"><span data-stu-id="77b7a-110">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="77b7a-111">Passando parâmetros de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="77b7a-111">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="77b7a-112">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="77b7a-112">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="77b7a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="77b7a-113">See Also</span></span>  
 [<span data-ttu-id="77b7a-114">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="77b7a-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="77b7a-115">Métodos</span><span class="sxs-lookup"><span data-stu-id="77b7a-115">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
