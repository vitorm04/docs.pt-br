---
title: Tipo unit (F#)
description: "Saiba como o tipo 'unit' F # é geralmente usado para manter o lugar onde um valor é exigido pela sintaxe de linguagem quando nenhum valor é necessário ou desejado."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: eabbb6d7-80f3-4fa5-80b4-0f48982466a7
ms.openlocfilehash: 60ac08c0e3f8380a8f9dec7a083ede93c68bb0e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="unit-type"></a><span data-ttu-id="4f2b9-104">Tipo unit</span><span class="sxs-lookup"><span data-stu-id="4f2b9-104">Unit Type</span></span>

<span data-ttu-id="4f2b9-105">O `unit` é um tipo que indica a ausência de um valor específico; o `unit` tipo tem apenas um único valor, que atua como um espaço reservado quando nenhum outro valor existe ou é necessário.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-105">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>


## <a name="syntax"></a><span data-ttu-id="4f2b9-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4f2b9-106">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="4f2b9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="4f2b9-107">Remarks</span></span>
<span data-ttu-id="4f2b9-108">Cada expressão F # deve ser avaliada como um valor.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-108">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="4f2b9-109">Para expressões que não geram um valor que é de interesse, o valor do tipo `unit` é usado.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-109">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="4f2b9-110">O `unit` tipo é semelhante a `void` tipo em linguagens como c# e C++.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-110">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="4f2b9-111">O `unit` tipo tem um único valor, e esse valor é indicada pelo token de `()`.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-111">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="4f2b9-112">O valor da `unit` tipo geralmente é usado em F # de programação para manter o lugar onde um valor é exigido pela sintaxe de linguagem, mas quando nenhum valor é necessário ou desejado.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-112">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="4f2b9-113">Um exemplo pode ser o valor de retorno de uma `printf` função.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-113">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="4f2b9-114">Como as ações importantes do `printf` operação ocorrer na função, a função não precisa retornar um valor real.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-114">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="4f2b9-115">Portanto, o valor retornado é do tipo `unit`.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-115">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="4f2b9-116">Algumas construções esperam um `unit` valor.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-116">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="4f2b9-117">Por exemplo, um `do` associação ou qualquer código no nível superior de um módulo deve ser avaliada para um `unit` valor.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-117">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="4f2b9-118">O compilador relata um aviso quando um `do` associação ou código no nível superior de um módulo produz um resultado diferente de `unit` valor não for usado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-118">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="4f2b9-119">Esse aviso é uma característica de programação funcional; ele não aparece em outras linguagens de programação do .NET.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-119">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="4f2b9-120">Em um programa totalmente funcional, nos quais funções não têm efeitos colaterais, o valor de retorno final é o único resultado de uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-120">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="4f2b9-121">Portanto, quando o resultado é ignorado, ele é um possível erro de programação.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-121">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="4f2b9-122">Embora o F # não é uma linguagem de programação totalmente funcional, é uma boa prática segue o estilo de programação funcional sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="4f2b9-122">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="4f2b9-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4f2b9-123">See Also</span></span>
[<span data-ttu-id="4f2b9-124">Primitivos</span><span class="sxs-lookup"><span data-stu-id="4f2b9-124">Primitive</span></span>](primitive-types.md)

[<span data-ttu-id="4f2b9-125">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4f2b9-125">F# Language Reference</span></span>](index.md)
