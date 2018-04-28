---
title: Tipo unit (F#)
description: "Saiba como o tipo 'unit' F # é geralmente usado para manter o lugar onde um valor é exigido pela sintaxe de linguagem quando nenhum valor é necessário ou desejado."
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 1a8c8f74e31c5426a9fb6a7143e9d2ac9a7104c0
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="unit-type"></a><span data-ttu-id="46879-103">Tipo unit</span><span class="sxs-lookup"><span data-stu-id="46879-103">Unit Type</span></span>

<span data-ttu-id="46879-104">O `unit` é um tipo que indica a ausência de um valor específico; o `unit` tipo tem apenas um único valor, que atua como um espaço reservado quando nenhum outro valor existe ou é necessário.</span><span class="sxs-lookup"><span data-stu-id="46879-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>


## <a name="syntax"></a><span data-ttu-id="46879-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="46879-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="46879-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="46879-106">Remarks</span></span>
<span data-ttu-id="46879-107">Cada expressão F # deve ser avaliada como um valor.</span><span class="sxs-lookup"><span data-stu-id="46879-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="46879-108">Para expressões que não geram um valor que é de interesse, o valor do tipo `unit` é usado.</span><span class="sxs-lookup"><span data-stu-id="46879-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="46879-109">O `unit` tipo é semelhante a `void` tipo em linguagens como c# e C++.</span><span class="sxs-lookup"><span data-stu-id="46879-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="46879-110">O `unit` tipo tem um único valor, e esse valor é indicada pelo token de `()`.</span><span class="sxs-lookup"><span data-stu-id="46879-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="46879-111">O valor da `unit` tipo geralmente é usado em F # de programação para manter o lugar onde um valor é exigido pela sintaxe de linguagem, mas quando nenhum valor é necessário ou desejado.</span><span class="sxs-lookup"><span data-stu-id="46879-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="46879-112">Um exemplo pode ser o valor de retorno de uma `printf` função.</span><span class="sxs-lookup"><span data-stu-id="46879-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="46879-113">Como as ações importantes do `printf` operação ocorrer na função, a função não precisa retornar um valor real.</span><span class="sxs-lookup"><span data-stu-id="46879-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="46879-114">Portanto, o valor retornado é do tipo `unit`.</span><span class="sxs-lookup"><span data-stu-id="46879-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="46879-115">Algumas construções esperam um `unit` valor.</span><span class="sxs-lookup"><span data-stu-id="46879-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="46879-116">Por exemplo, um `do` associação ou qualquer código no nível superior de um módulo deve ser avaliada para um `unit` valor.</span><span class="sxs-lookup"><span data-stu-id="46879-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="46879-117">O compilador relata um aviso quando um `do` associação ou código no nível superior de um módulo produz um resultado diferente de `unit` valor não for usado, conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="46879-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="46879-118">Esse aviso é uma característica de programação funcional; ele não aparece em outras linguagens de programação do .NET.</span><span class="sxs-lookup"><span data-stu-id="46879-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="46879-119">Em um programa totalmente funcional, nos quais funções não têm efeitos colaterais, o valor de retorno final é o único resultado de uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="46879-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="46879-120">Portanto, quando o resultado é ignorado, ele é um possível erro de programação.</span><span class="sxs-lookup"><span data-stu-id="46879-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="46879-121">Embora o F # não é uma linguagem de programação totalmente funcional, é uma boa prática segue o estilo de programação funcional sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="46879-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="46879-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46879-122">See Also</span></span>
[<span data-ttu-id="46879-123">Primitivos</span><span class="sxs-lookup"><span data-stu-id="46879-123">Primitive</span></span>](primitive-types.md)

[<span data-ttu-id="46879-124">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="46879-124">F# Language Reference</span></span>](index.md)
