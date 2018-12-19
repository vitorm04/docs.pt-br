---
title: Passando parâmetros – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 3e205ecba48df69c0e7f289ad8201765b35d5767
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238137"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="d34de-102">Passando parâmetros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d34de-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="d34de-103">No C#, argumentos podem ser passados para parâmetros por valor ou por referência.</span><span class="sxs-lookup"><span data-stu-id="d34de-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="d34de-104">A passagem por referência permite que métodos, propriedades, indexadores, operadores, construtores e membros da função alterem o valor dos parâmetros e façam essa alteração persistir no ambiente de chamada.</span><span class="sxs-lookup"><span data-stu-id="d34de-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="d34de-105">Para passar um parâmetro por referência com a intenção de alterar o valor, use a palavra-chave `ref` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="d34de-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="d34de-106">Para passar por referência com a intenção de evitar a cópia, mas não alterar o valor, use o modificador `in`.</span><span class="sxs-lookup"><span data-stu-id="d34de-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="d34de-107">Para simplificar, somente a palavra-chave `ref` é usada nos exemplos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="d34de-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="d34de-108">Para obter mais informações sobre a diferença entre `in`, `ref` e `out`, consulte [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) e [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="d34de-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="d34de-109">O exemplo a seguir ilustra a diferença entre parâmetros de valor e referência.</span><span class="sxs-lookup"><span data-stu-id="d34de-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/passing-parameters_1.cs)]  
  
 <span data-ttu-id="d34de-110">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="d34de-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d34de-111">Passando parâmetros de tipo de valor</span><span class="sxs-lookup"><span data-stu-id="d34de-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="d34de-112">Passando parâmetros de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="d34de-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="d34de-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d34de-113">C# Language Specification</span></span>  

<span data-ttu-id="d34de-114">Para obter mais informações, veja as [listas de argumentos](~/_csharplang/spec/expressions.md#argument-lists) na [Especificação da linguagem C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d34de-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="d34de-115">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="d34de-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d34de-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d34de-116">See Also</span></span>

- [<span data-ttu-id="d34de-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d34de-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="d34de-118">Métodos</span><span class="sxs-lookup"><span data-stu-id="d34de-118">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
