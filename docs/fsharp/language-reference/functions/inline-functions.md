---
title: "Funções embutidas (F#)"
description: "Saiba como usar o F # embutido funções que são integradas diretamente no código de chamada."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 3fa31178-08f8-463d-9d41-d29220a90027
ms.openlocfilehash: 0489d411e2754eaab6a10ff0feb4405491b3b511
ms.sourcegitcommit: 425524461530f020f9747492b42f8cd72b011ae7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2017
---
# <a name="inline-functions"></a><span data-ttu-id="7d4bb-104">Funções embutidas</span><span class="sxs-lookup"><span data-stu-id="7d4bb-104">Inline Functions</span></span>

<span data-ttu-id="7d4bb-105">*Funções embutidas* são funções que são integradas diretamente no código de chamada.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-105">*Inline functions* are functions that are integrated directly into the calling code.</span></span>


## <a name="using-inline-functions"></a><span data-ttu-id="7d4bb-106">Usando funções embutidas</span><span class="sxs-lookup"><span data-stu-id="7d4bb-106">Using Inline Functions</span></span>
<span data-ttu-id="7d4bb-107">Quando você usar parâmetros de tipo estático, todas as funções que são parametrizadas por parâmetros de tipo devem ser embutida.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-107">When you use static type parameters, any functions that are parameterized by type parameters must be inline.</span></span> <span data-ttu-id="7d4bb-108">Isso garante que o compilador pode resolver esses parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-108">This guarantees that the compiler can resolve these type parameters.</span></span> <span data-ttu-id="7d4bb-109">Quando você usar parâmetros de tipo genérico comum, não há nenhuma restrição.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-109">When you use ordinary generic type parameters, there is no such restriction.</span></span>

<span data-ttu-id="7d4bb-110">Além de habilitar o uso de restrições de membro, funções embutidas podem ser úteis na otimização de código.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-110">Other than enabling the use of member constraints, inline functions can be helpful in optimizing code.</span></span> <span data-ttu-id="7d4bb-111">No entanto, o uso excessivo de funções embutidas pode causar seu código seja menos resistentes a mudanças em otimizações do compilador e a implementação de funções de biblioteca.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-111">However, overuse of inline functions can cause your code to be less resistant to changes in compiler optimizations and the implementation of library functions.</span></span> <span data-ttu-id="7d4bb-112">Por esse motivo, você deve evitar usar funções embutidas para otimização, a menos que você tentou todas as outras técnicas de otimização.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-112">For this reason, you should avoid using inline functions for optimization unless you have tried all other optimization techniques.</span></span> <span data-ttu-id="7d4bb-113">Fazer um método ou função em linha pode muitas vezes melhorar desempenho, mas que não é sempre o caso.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-113">Making a function or method inline can sometimes improve performance, but that is not always the case.</span></span> <span data-ttu-id="7d4bb-114">Portanto, você também deve usar medidas de desempenho para verificar o que fazer qualquer determinada função embutida na verdade tem um efeito positivo.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-114">Therefore, you should also use performance measurements to verify that making any given function inline does in fact have a positive effect.</span></span>

<span data-ttu-id="7d4bb-115">O `inline` modificador pode ser aplicado às funções de nível superior, no nível de módulo ou no nível de método em uma classe.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-115">The `inline` modifier can be applied to functions at the top level, at the module level, or at the method level in a class.</span></span>

<span data-ttu-id="7d4bb-116">O exemplo de código a seguir ilustra uma função embutida no nível superior, um método de instância embutido e um método estático em linha.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-116">The following code example illustrates an inline function at the top level, an inline instance method, and an inline static method.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet201.fs)]
    
## <a name="inline-functions-and-type-inference"></a><span data-ttu-id="7d4bb-117">Funções embutidas e Inferência de tipo</span><span class="sxs-lookup"><span data-stu-id="7d4bb-117">Inline Functions and Type Inference</span></span>
<span data-ttu-id="7d4bb-118">A presença de `inline` afeta a inferência de tipos.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-118">The presence of `inline` affects type inference.</span></span> <span data-ttu-id="7d4bb-119">Isso ocorre porque funções embutidas podem ter resolvidos estaticamente parâmetros de tipo, enquanto as funções embutidas não não é possível.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-119">This is because inline functions can have statically resolved type parameters, whereas non-inline functions cannot.</span></span> <span data-ttu-id="7d4bb-120">O exemplo de código a seguir mostra um caso onde `inline` é útil porque você está usando uma função que tem um parâmetro de tipo resolvidos estaticamente, o `float` operador de conversão.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-120">The following code example shows a case where `inline` is helpful because you are using a function that has a statically resolved type parameter, the `float` conversion operator.</span></span>

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-3/snippet202.fs)]

<span data-ttu-id="7d4bb-121">Sem o `inline` força de inferência de tipo de modificador, a função para usar um tipo específico, nesse caso `int`.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-121">Without the `inline` modifier, type inference forces the function to take a specific type, in this case `int`.</span></span> <span data-ttu-id="7d4bb-122">Mas com o `inline` modificador, a função também é inferido para ter um parâmetro de tipo resolvidos estaticamente.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-122">But with the `inline` modifier, the function is also inferred to have a statically resolved type parameter.</span></span> <span data-ttu-id="7d4bb-123">Com o `inline` modificador, o tipo é inferido para ser o seguinte:</span><span class="sxs-lookup"><span data-stu-id="7d4bb-123">With the `inline` modifier, the type is inferred to be the following:</span></span>

```fsharp
^a -> unit when ^a : (static member op_Explicit : ^a -> float)
```

<span data-ttu-id="7d4bb-124">Isso significa que a função aceita qualquer tipo que oferece suporte a uma conversão **float**.</span><span class="sxs-lookup"><span data-stu-id="7d4bb-124">This means that the function accepts any type that supports a conversion to **float**.</span></span>


## <a name="see-also"></a><span data-ttu-id="7d4bb-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d4bb-125">See Also</span></span>
[<span data-ttu-id="7d4bb-126">Funções</span><span class="sxs-lookup"><span data-stu-id="7d4bb-126">Functions</span></span>](index.md)

[<span data-ttu-id="7d4bb-127">Restrições</span><span class="sxs-lookup"><span data-stu-id="7d4bb-127">Constraints</span></span>](../generics/constraints.md)

[<span data-ttu-id="7d4bb-128">Parâmetros de Tipo Resolvidos Estaticamente</span><span class="sxs-lookup"><span data-stu-id="7d4bb-128">Statically Resolved Type Parameters</span></span>](../generics/statically-resolved-type-parameters.md)
