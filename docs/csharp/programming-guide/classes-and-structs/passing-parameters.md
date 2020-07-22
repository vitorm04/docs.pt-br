---
title: Passando parâmetros – Guia de Programação em C#
description: Você pode passar um argumento para um parâmetro em C# por valor ou referência. As alterações em um argumento passado por referência são mantidas. Use ref ou out para passar por referência.
ms.date: 07/20/2015
helpviewer_keywords:
- parameters [C#], passing
- passing parameters [C#]
- arguments [C#]
- methods [C#], passing parameters
- C# language, method parameters
ms.assetid: a5c3003f-7441-4710-b8b1-c79de77e0b77
ms.openlocfilehash: 875a42aacf3d7aa4124684aefafdcb07ff4c87d6
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864729"
---
# <a name="passing-parameters-c-programming-guide"></a><span data-ttu-id="69ef5-105">Passando parâmetros (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="69ef5-105">Passing Parameters (C# Programming Guide)</span></span>
<span data-ttu-id="69ef5-106">No C#, argumentos podem ser passados para parâmetros por valor ou por referência.</span><span class="sxs-lookup"><span data-stu-id="69ef5-106">In C#, arguments can be passed to parameters either by value or by reference.</span></span> <span data-ttu-id="69ef5-107">A passagem por referência permite que métodos, propriedades, indexadores, operadores, construtores e membros da função alterem o valor dos parâmetros e façam essa alteração persistir no ambiente de chamada.</span><span class="sxs-lookup"><span data-stu-id="69ef5-107">Passing by reference enables function members, methods, properties, indexers, operators, and constructors to change the value of the parameters and have that change persist in the calling environment.</span></span> <span data-ttu-id="69ef5-108">Para passar um parâmetro por referência com a intenção de alterar o valor, use a palavra-chave `ref` ou `out`.</span><span class="sxs-lookup"><span data-stu-id="69ef5-108">To pass a parameter by reference with the intent of changing the value, use the `ref`, or `out` keyword.</span></span> <span data-ttu-id="69ef5-109">Para passar por referência com a intenção de evitar a cópia, mas não alterar o valor, use o modificador `in`.</span><span class="sxs-lookup"><span data-stu-id="69ef5-109">To pass by reference with the intent of avoiding copying but not changing the value, use the `in` modifier.</span></span> <span data-ttu-id="69ef5-110">Para simplificar, somente a palavra-chave `ref` é usada nos exemplos neste tópico.</span><span class="sxs-lookup"><span data-stu-id="69ef5-110">For simplicity, only the `ref` keyword is used in the examples in this topic.</span></span> <span data-ttu-id="69ef5-111">Para obter mais informações sobre a diferença entre `in`, `ref` e `out`, consulte [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md) e [out](../../language-reference/keywords/out-parameter-modifier.md).</span><span class="sxs-lookup"><span data-stu-id="69ef5-111">For more information about the difference between `in`, `ref`, and `out`, see [in](../../language-reference/keywords/in-parameter-modifier.md), [ref](../../language-reference/keywords/ref.md), and [out](../../language-reference/keywords/out-parameter-modifier.md).</span></span>  
  
 <span data-ttu-id="69ef5-112">O exemplo a seguir ilustra a diferença entre parâmetros de valor e referência.</span><span class="sxs-lookup"><span data-stu-id="69ef5-112">The following example illustrates the difference between value and reference parameters.</span></span>  
  
 [!code-csharp[csProgGuideParameters#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideParameters/CS/Parameters.cs#10)]  
  
 <span data-ttu-id="69ef5-113">Para obter mais informações, consulte estes tópicos:</span><span class="sxs-lookup"><span data-stu-id="69ef5-113">For more information, see the following topics:</span></span>  
  
- [<span data-ttu-id="69ef5-114">Passando parâmetros de tipo de valor</span><span class="sxs-lookup"><span data-stu-id="69ef5-114">Passing Value-Type Parameters</span></span>](./passing-value-type-parameters.md)  
  
- [<span data-ttu-id="69ef5-115">Passando parâmetros de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="69ef5-115">Passing Reference-Type Parameters</span></span>](./passing-reference-type-parameters.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="69ef5-116">Especificação da Linguagem C#</span><span class="sxs-lookup"><span data-stu-id="69ef5-116">C# Language Specification</span></span>  

<span data-ttu-id="69ef5-117">Para obter mais informações, veja as [listas de argumentos](~/_csharplang/spec/expressions.md#argument-lists) na [Especificação da linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="69ef5-117">For more information, see [Argument lists](~/_csharplang/spec/expressions.md#argument-lists) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="69ef5-118">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="69ef5-118">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="69ef5-119">Veja também</span><span class="sxs-lookup"><span data-stu-id="69ef5-119">See also</span></span>

- [<span data-ttu-id="69ef5-120">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="69ef5-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="69ef5-121">Métodos</span><span class="sxs-lookup"><span data-stu-id="69ef5-121">Methods</span></span>](./methods.md)
