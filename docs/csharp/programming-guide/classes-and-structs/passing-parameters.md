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
ms.openlocfilehash: c8da86d2a8f5101acf5b9cc1bcc2f9ad50378fa4
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969538"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="d9f0f-102">Passando parâmetros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="d9f0f-102">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="d9f0f-103">No C#, argumentos podem ser passados para parâmetros por valor ou por referência.</span><span class="sxs-lookup"><span data-stu-id="d9f0f-103">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="d9f0f-104">A passagem por referência permite que métodos, propriedades, indexadores, operadores, construtores e membros da função alterem o valor dos parâmetros e façam essa alteração persistir no ambiente de chamada.</span><span class="sxs-lookup"><span data-stu-id="d9f0f-104">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="d9f0f-105">Para passar um parâmetro por referência com a intenção de alterar o valor, use a palavra-chave `ref` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="d9f0f-105">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="d9f0f-106">Para passar por referência com a intenção de evitar a cópia, mas não alterar o valor, use o modificador `in`.</span><span class="sxs-lookup"><span data-stu-id="d9f0f-106">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="d9f0f-107">Para simplificar, somente a palavra-chave `ref` é usada nos exemplos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="d9f0f-107">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="d9f0f-108">Para obter mais informações sobre a diferença entre `in`, `ref` e `out`, consulte [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md) e [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="d9f0f-108">For more information about the difference between `in`, `ref`, and `out`, see [in](../../../csharp/language-reference/keywords/in-parameter-modifier.md), [ref](../../../csharp/language-reference/keywords/ref.md), and [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="d9f0f-109">O exemplo a seguir ilustra a diferença entre parâmetros de valor e referência.</span><span class="sxs-lookup"><span data-stu-id="d9f0f-109">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="d9f0f-110">Para mais informações, consulte os seguintes tópicos:</span><span class="sxs-lookup"><span data-stu-id="d9f0f-110">For more information, see the following topics:</span></span>  
  
-   [<span data-ttu-id="d9f0f-111">Passando parâmetros de tipo de valor</span><span class="sxs-lookup"><span data-stu-id="d9f0f-111">Passing Value-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-value-type-parameters.md)  
  
-   [<span data-ttu-id="d9f0f-112">Passando parâmetros de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="d9f0f-112">Passing Reference-Type Parameters</span></span>](../../../csharp/programming-guide/classes-and-structs/passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="d9f0f-113">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="d9f0f-113">C# Language Specification</span></span>  

<span data-ttu-id="d9f0f-114">Para obter mais informações, veja as [listas de argumentos](~/_csharplang/spec/expressions.md#argument-lists) na [Especificação da linguagem C#](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="d9f0f-114">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="d9f0f-115">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="d9f0f-115">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="d9f0f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d9f0f-116">See also</span></span>

- [<span data-ttu-id="d9f0f-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d9f0f-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="d9f0f-118">Métodos</span><span class="sxs-lookup"><span data-stu-id="d9f0f-118">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
