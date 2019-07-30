---
title: Tipo unit
description: Saiba como o F# tipo de "unidade" geralmente é usado para manter o local em que um valor é exigido pela sintaxe de idioma quando nenhum valor é necessário ou desejado.
ms.date: 05/16/2016
ms.openlocfilehash: 4e586702324565b8dcd4f6c7e11a0e1754f89c58
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630167"
---
# <a name="unit-type"></a><span data-ttu-id="cf804-103">Tipo unit</span><span class="sxs-lookup"><span data-stu-id="cf804-103">Unit Type</span></span>

<span data-ttu-id="cf804-104">O `unit` tipo é um tipo que indica a ausência de um valor específico; o `unit` tipo tem apenas um único valor, que atua como um espaço reservado quando nenhum outro valor existe ou é necessário.</span><span class="sxs-lookup"><span data-stu-id="cf804-104">The `unit` type is a type that indicates the absence of a specific value; the `unit` type has only a single value, which acts as a placeholder when no other value exists or is needed.</span></span>

## <a name="syntax"></a><span data-ttu-id="cf804-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf804-105">Syntax</span></span>

```fsharp
// The value of the unit type.
()
```

## <a name="remarks"></a><span data-ttu-id="cf804-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf804-106">Remarks</span></span>

<span data-ttu-id="cf804-107">Cada F# expressão deve ser avaliada como um valor.</span><span class="sxs-lookup"><span data-stu-id="cf804-107">Every F# expression must evaluate to a value.</span></span> <span data-ttu-id="cf804-108">Para expressões que não geram um valor de interesse, o valor do tipo `unit` é usado.</span><span class="sxs-lookup"><span data-stu-id="cf804-108">For expressions that do not generate a value that is of interest, the value of type `unit` is used.</span></span> <span data-ttu-id="cf804-109">O `unit` tipo é semelhante ao `void` tipo em idiomas como C# e C++.</span><span class="sxs-lookup"><span data-stu-id="cf804-109">The `unit` type resembles the `void` type in languages such as C# and C++.</span></span>

<span data-ttu-id="cf804-110">O `unit` tipo tem um único valor e esse valor é indicado pelo token `()`.</span><span class="sxs-lookup"><span data-stu-id="cf804-110">The `unit` type has a single value, and that value is indicated by the token `()`.</span></span>

<span data-ttu-id="cf804-111">O valor do `unit` tipo é geralmente usado na F# programação para manter o local em que um valor é exigido pela sintaxe da linguagem, mas quando nenhum valor é necessário ou desejado.</span><span class="sxs-lookup"><span data-stu-id="cf804-111">The value of the `unit` type is often used in F# programming to hold the place where a value is required by the language syntax, but when no value is needed or desired.</span></span> <span data-ttu-id="cf804-112">Um exemplo pode ser o valor de retorno de `printf` uma função.</span><span class="sxs-lookup"><span data-stu-id="cf804-112">An example might be the return value of a `printf` function.</span></span> <span data-ttu-id="cf804-113">Como as ações importantes da `printf` operação ocorrem na função, a função não precisa retornar um valor real.</span><span class="sxs-lookup"><span data-stu-id="cf804-113">Because the important actions of the `printf` operation occur in the function, the function does not have to return an actual value.</span></span> <span data-ttu-id="cf804-114">Portanto, o valor de retorno é do `unit`tipo.</span><span class="sxs-lookup"><span data-stu-id="cf804-114">Therefore, the return value is of type `unit`.</span></span>

<span data-ttu-id="cf804-115">Algumas construções esperam um `unit` valor.</span><span class="sxs-lookup"><span data-stu-id="cf804-115">Some constructs expect a `unit` value.</span></span> <span data-ttu-id="cf804-116">Por exemplo, uma `do` associação ou qualquer código no nível superior de um módulo deve ser avaliado como um `unit` valor.</span><span class="sxs-lookup"><span data-stu-id="cf804-116">For example, a `do` binding or any code at the top level of a module is expected to evaluate to a `unit` value.</span></span> <span data-ttu-id="cf804-117">O compilador relata um aviso quando uma `do` associação ou código no nível superior de um módulo produz um resultado diferente do `unit` valor que não é usado, como mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="cf804-117">The compiler reports a warning when a `do` binding or code at the top level of a module produces a result other than the `unit` value that is not used, as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet901.fs)]

<span data-ttu-id="cf804-118">Esse aviso é uma característica da programação funcional; Ele não aparece em outras linguagens de programação do .NET.</span><span class="sxs-lookup"><span data-stu-id="cf804-118">This warning is a characteristic of functional programming; it does not appear in other .NET programming languages.</span></span> <span data-ttu-id="cf804-119">Em um programa puramente funcional, no qual as funções não têm nenhum efeito colateral, o valor final de retorno é o único resultado de uma chamada de função.</span><span class="sxs-lookup"><span data-stu-id="cf804-119">In a purely functional program, in which functions do not have any side effects, the final return value is the only result of a function call.</span></span> <span data-ttu-id="cf804-120">Portanto, quando o resultado é ignorado, é um possível erro de programação.</span><span class="sxs-lookup"><span data-stu-id="cf804-120">Therefore, when the result is ignored, it is a possible programming error.</span></span> <span data-ttu-id="cf804-121">Embora F# o não seja uma linguagem de programação puramente funcional, é uma boa prática seguir o estilo de programação funcional sempre que possível.</span><span class="sxs-lookup"><span data-stu-id="cf804-121">Although F# is not a purely functional programming language, it is a good practice to follow functional programming style whenever possible.</span></span>

## <a name="see-also"></a><span data-ttu-id="cf804-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf804-122">See also</span></span>

- [<span data-ttu-id="cf804-123">Primitiva</span><span class="sxs-lookup"><span data-stu-id="cf804-123">Primitive</span></span>](primitive-types.md)
- [<span data-ttu-id="cf804-124">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="cf804-124">F# Language Reference</span></span>](index.md)
