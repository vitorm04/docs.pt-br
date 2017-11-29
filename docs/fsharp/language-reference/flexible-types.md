---
title: "Tipos flexíveis (F#)"
description: "Saiba como usar o F # anotação de tipo flexível, que indica que um valor, variável ou parâmetro tem um tipo que é compatível com um tipo especificado."
keywords: "visual f#, f#, programação funcional"
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: c8b510f2-3405-4cc9-b55b-e47b35e2b15b
ms.openlocfilehash: 7c5e4eb97791b9c6c56fe2847755866e8240e038
ms.sourcegitcommit: a19548e5167cbe7e9e58df4ffd8c3b23f17d5c7a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/02/2017
---
# <a name="flexible-types"></a><span data-ttu-id="4d1ee-104">Tipos flexíveis</span><span class="sxs-lookup"><span data-stu-id="4d1ee-104">Flexible Types</span></span>

<span data-ttu-id="4d1ee-105">Um *anotação de tipo flexível* indica que um valor, variável ou parâmetro tem um tipo que é compatível com um tipo especificado, onde a compatibilidade é determinada pela posição em uma hierarquia orientado a objeto de classes ou interfaces.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-105">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="4d1ee-106">Tipos flexíveis são úteis, especialmente quando a conversão automática para tipos superiores na hierarquia de tipo não ocorrer, mas você ainda deseja habilitar a funcionalidade trabalhar com qualquer tipo na hierarquia ou qualquer tipo que implementa uma interface.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-106">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="4d1ee-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4d1ee-107">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="4d1ee-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="4d1ee-108">Remarks</span></span>

<span data-ttu-id="4d1ee-109">Na sintaxe anterior, *tipo* representa um tipo base ou interface.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-109">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="4d1ee-110">Um tipo flexível é equivalente a um tipo genérico que tem uma restrição que limita os tipos permitidos para tipos que são compatíveis com o tipo base ou interface.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-110">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="4d1ee-111">Ou seja, as duas linhas de código a seguir são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-111">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="4d1ee-112">Tipos flexíveis são úteis em vários tipos de situações.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-112">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="4d1ee-113">Por exemplo, quando você tem uma função de ordem superior (uma função que usa uma função como um argumento), geralmente é útil para que a função retornar um tipo flexível.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-113">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="4d1ee-114">No exemplo a seguir, o uso de um tipo flexível com um argumento de sequência em `iterate2` permite que a função de ordem superior trabalhar com funções que geram sequências, matrizes, listas e qualquer outro tipo enumerável.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-114">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="4d1ee-115">Considere duas funções a seguir, um dos quais retorna uma sequência, outro que retorna um tipo de flexível.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-115">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="4d1ee-116">Como outro exemplo, considere o [SEQ](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) função de biblioteca:</span><span class="sxs-lookup"><span data-stu-id="4d1ee-116">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="4d1ee-117">Você pode transmitir qualquer uma das seguintes sequências enumeráveis para esta função:</span><span class="sxs-lookup"><span data-stu-id="4d1ee-117">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="4d1ee-118">Uma lista de listas</span><span class="sxs-lookup"><span data-stu-id="4d1ee-118">A list of lists</span></span>
- <span data-ttu-id="4d1ee-119">Uma lista de matrizes</span><span class="sxs-lookup"><span data-stu-id="4d1ee-119">A list of arrays</span></span>
- <span data-ttu-id="4d1ee-120">Uma matriz das listas</span><span class="sxs-lookup"><span data-stu-id="4d1ee-120">An array of lists</span></span>
- <span data-ttu-id="4d1ee-121">Uma matriz de sequências</span><span class="sxs-lookup"><span data-stu-id="4d1ee-121">An array of sequences</span></span>
- <span data-ttu-id="4d1ee-122">Qualquer outra combinação de sequências enumeráveis</span><span class="sxs-lookup"><span data-stu-id="4d1ee-122">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="4d1ee-123">O código a seguir usa `Seq.concat` para demonstrar os cenários que você pode suportar usando tipos flexíveis.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-123">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="4d1ee-124">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-124">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="4d1ee-125">Em F #, como em outros idiomas e orientada a objeto, há contextos em que tipos derivados ou tipos que implementam as interfaces são automaticamente convertidos em um tipo base ou interface.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-125">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="4d1ee-126">Essas conversões automático ocorrerem nos argumentos diretos, mas não quando o tipo é em uma posição subordinada, como parte de um tipo mais complexo, como um tipo de retorno de um tipo de função, ou como um argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-126">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="4d1ee-127">Assim, a notação de tipo flexível é útil principalmente quando o tipo a que estiver aplicando é parte de um tipo mais complexo.</span><span class="sxs-lookup"><span data-stu-id="4d1ee-127">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="4d1ee-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4d1ee-128">See Also</span></span>

[<span data-ttu-id="4d1ee-129">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4d1ee-129">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4d1ee-130">Genéricos</span><span class="sxs-lookup"><span data-stu-id="4d1ee-130">Generics</span></span>](generics/index.md)
