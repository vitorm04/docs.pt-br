---
title: Inferência de tipos
description: Saiba como o F# compilador infere os tipos de valores, variáveis, parâmetros e valores de retorno.
ms.date: 05/16/2016
ms.openlocfilehash: ab1a4aa8df4312287df749d5d6d0ea2858091152
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65641674"
---
# <a name="type-inference"></a><span data-ttu-id="72ab0-103">Inferência de tipos</span><span class="sxs-lookup"><span data-stu-id="72ab0-103">Type Inference</span></span>

<span data-ttu-id="72ab0-104">Este tópico descreve como o F# compilador infere os tipos de valores, variáveis, parâmetros e valores de retorno.</span><span class="sxs-lookup"><span data-stu-id="72ab0-104">This topic describes how the F# compiler infers the types of values, variables, parameters and return values.</span></span>

## <a name="type-inference-in-general"></a><span data-ttu-id="72ab0-105">Inferência de tipo em geral</span><span class="sxs-lookup"><span data-stu-id="72ab0-105">Type Inference in General</span></span>

<span data-ttu-id="72ab0-106">A ideia de inferência de tipo é que você não precisa especificar os tipos de F# construções, exceto quando o compilador conclusivamente não é possível deduzir o tipo.</span><span class="sxs-lookup"><span data-stu-id="72ab0-106">The idea of type inference is that you do not have to specify the types of F# constructs except when the compiler cannot conclusively deduce the type.</span></span> <span data-ttu-id="72ab0-107">Omitir informações de tipo explícito não significa que F# é uma linguagem dinamicamente tipada ou que os valores no F# são fracamente tipado.</span><span class="sxs-lookup"><span data-stu-id="72ab0-107">Omitting explicit type information does not mean that F# is a dynamically typed language or that values in F# are weakly typed.</span></span> <span data-ttu-id="72ab0-108">F#é uma linguagem estaticamente digitada, o que significa que o compilador deduz um tipo exato para cada constructo durante a compilação.</span><span class="sxs-lookup"><span data-stu-id="72ab0-108">F# is a statically typed language, which means that the compiler deduces an exact type for each construct during compilation.</span></span> <span data-ttu-id="72ab0-109">Se não houver informações suficientes para que o compilador Deduza os tipos de cada construção, você deve fornecer informações de tipo adicionais, normalmente com a adição de anotações de tipo explícito em algum lugar no código.</span><span class="sxs-lookup"><span data-stu-id="72ab0-109">If there is not enough information for the compiler to deduce the types of each construct, you must supply additional type information, typically by adding explicit type annotations somewhere in the code.</span></span>

## <a name="inference-of-parameter-and-return-types"></a><span data-ttu-id="72ab0-110">Inferência de tipos de parâmetro e tipos de retorno</span><span class="sxs-lookup"><span data-stu-id="72ab0-110">Inference of Parameter and Return Types</span></span>

<span data-ttu-id="72ab0-111">Em uma lista de parâmetros, você precisa especificar o tipo de cada parâmetro.</span><span class="sxs-lookup"><span data-stu-id="72ab0-111">In a parameter list, you do not have to specify the type of each parameter.</span></span> <span data-ttu-id="72ab0-112">E ainda, F# é uma linguagem estaticamente digitada e, portanto, cada valor e a expressão tem um tipo definido em tempo de compilação.</span><span class="sxs-lookup"><span data-stu-id="72ab0-112">And yet, F# is a statically typed language, and therefore every value and expression has a definite type at compile time.</span></span> <span data-ttu-id="72ab0-113">Para os tipos que você não especificar explicitamente, o compilador infere o tipo com base no contexto.</span><span class="sxs-lookup"><span data-stu-id="72ab0-113">For those types that you do not specify explicitly, the compiler infers the type based on the context.</span></span> <span data-ttu-id="72ab0-114">Se o tipo não é especificado, ele é inferido para ser genérico.</span><span class="sxs-lookup"><span data-stu-id="72ab0-114">If the type is not otherwise specified, it is inferred to be generic.</span></span> <span data-ttu-id="72ab0-115">Se o código usa um valor de forma inconsistente, de forma que haja não único tipo inferido que atende a todos os usos de um valor, que o compilador relatará um erro.</span><span class="sxs-lookup"><span data-stu-id="72ab0-115">If the code uses a value inconsistently, in such a way that there is no single inferred type that satisfies all the uses of a value, the compiler reports an error.</span></span>

<span data-ttu-id="72ab0-116">O tipo de retorno de uma função é determinado pelo tipo da última expressão na função.</span><span class="sxs-lookup"><span data-stu-id="72ab0-116">The return type of a function is determined by the type of the last expression in the function.</span></span>

<span data-ttu-id="72ab0-117">Por exemplo, no código a seguir, os tipos de parâmetro `a` e `b` e o tipo de retorno são inferidos seja `int` porque o literal `100` é do tipo `int`.</span><span class="sxs-lookup"><span data-stu-id="72ab0-117">For example, in the following code, the parameter types `a` and `b` and the return type are all inferred to be `int` because the literal `100` is of type `int`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet301.fs)]

<span data-ttu-id="72ab0-118">Você pode influenciar a inferência de tipo, alterando os literais.</span><span class="sxs-lookup"><span data-stu-id="72ab0-118">You can influence type inference by changing the literals.</span></span> <span data-ttu-id="72ab0-119">Se você fizer a `100` uma `uint32` acrescentando o sufixo `u`, os tipos de `a`, `b`, e o valor de retorno são inferidos ser `uint32`.</span><span class="sxs-lookup"><span data-stu-id="72ab0-119">If you make the `100` a `uint32` by appending the suffix `u`, the types of `a`, `b`, and the return value are inferred to be `uint32`.</span></span>

<span data-ttu-id="72ab0-120">Você também pode influenciar inferência de tipos usando outras construções que implicam restrições no tipo, como funções e métodos que funcionam com apenas um tipo específico.</span><span class="sxs-lookup"><span data-stu-id="72ab0-120">You can also influence type inference by using other constructs that imply restrictions on the type, such as functions and methods that work with only a particular type.</span></span>

<span data-ttu-id="72ab0-121">Além disso, você pode aplicar as anotações de tipo explícito para parâmetros de método ou função ou variáveis em expressões, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="72ab0-121">Also, you can apply explicit type annotations to function or method parameters or to variables in expressions, as shown in the following examples.</span></span> <span data-ttu-id="72ab0-122">Erros resultam se ocorrerem conflitos entre diferentes restrições.</span><span class="sxs-lookup"><span data-stu-id="72ab0-122">Errors result if conflicts occur between different constraints.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet302.fs)]

<span data-ttu-id="72ab0-123">Você também pode especificar explicitamente o valor de retorno de uma função, fornecendo uma anotação de tipo depois que todos os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="72ab0-123">You can also explicitly specify the return value of a function by providing a type annotation after all the parameters.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet303.fs)]

<span data-ttu-id="72ab0-124">Um caso comum em que uma anotação de tipo é útil em um parâmetro é quando o parâmetro é um tipo de objeto e você deseja usar um membro.</span><span class="sxs-lookup"><span data-stu-id="72ab0-124">A common case where a type annotation is useful on a parameter is when the parameter is an object type and you want to use a member.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet304.fs)]

## <a name="automatic-generalization"></a><span data-ttu-id="72ab0-125">Generalização automática</span><span class="sxs-lookup"><span data-stu-id="72ab0-125">Automatic Generalization</span></span>

<span data-ttu-id="72ab0-126">Se o código de função não é dependente do tipo de um parâmetro, o compilador considera o parâmetro para ser genérico.</span><span class="sxs-lookup"><span data-stu-id="72ab0-126">If the function code is not dependent on the type of a parameter, the compiler considers the parameter to be generic.</span></span> <span data-ttu-id="72ab0-127">Isso é chamado *generalização automática*, e pode ser uma poderosa ajuda para escrever código genérico sem aumentar a complexidade.</span><span class="sxs-lookup"><span data-stu-id="72ab0-127">This is called *automatic generalization*, and it can be a powerful aid to writing generic code without increasing complexity.</span></span>

<span data-ttu-id="72ab0-128">Por exemplo, a função a seguir combina dois parâmetros de qualquer tipo em uma tupla.</span><span class="sxs-lookup"><span data-stu-id="72ab0-128">For example, the following function combines two parameters of any type into a tuple.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-3/snippet305.fs)]

<span data-ttu-id="72ab0-129">O tipo é inferido para ser</span><span class="sxs-lookup"><span data-stu-id="72ab0-129">The type is inferred to be</span></span>

```fsharp
'a -> 'b -> 'a * 'b
```

## <a name="additional-information"></a><span data-ttu-id="72ab0-130">Informações adicionais</span><span class="sxs-lookup"><span data-stu-id="72ab0-130">Additional Information</span></span>

<span data-ttu-id="72ab0-131">Inferência de tipo é descrita mais detalhadamente o F# especificação da linguagem.</span><span class="sxs-lookup"><span data-stu-id="72ab0-131">Type inference is described in more detail in the F# Language Specification.</span></span>

## <a name="see-also"></a><span data-ttu-id="72ab0-132">Consulte também</span><span class="sxs-lookup"><span data-stu-id="72ab0-132">See also</span></span>

- [<span data-ttu-id="72ab0-133">Generalização Automática</span><span class="sxs-lookup"><span data-stu-id="72ab0-133">Automatic Generalization</span></span>](generics/automatic-generalization.md)
