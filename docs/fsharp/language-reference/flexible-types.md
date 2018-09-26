---
title: Tipos flexíveis (F#)
description: 'Saiba como usar F # anotação de tipo flexível, que indica que um parâmetro, variável ou valor tem um tipo que é compatível com um tipo especificado.'
ms.date: 05/16/2016
ms.openlocfilehash: b6c97c3cc19f15b2c8db74b2c55660a16b2858f7
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2018
ms.locfileid: "47210039"
---
# <a name="flexible-types"></a><span data-ttu-id="7318e-103">Tipos flexíveis</span><span class="sxs-lookup"><span data-stu-id="7318e-103">Flexible Types</span></span>

<span data-ttu-id="7318e-104">Um *anotação de tipo flexível* indica que um parâmetro, variável ou valor tem um tipo que é compatível com um tipo especificado, onde a compatibilidade é determinada pela posição em uma hierarquia orientada a objeto de classes ou interfaces.</span><span class="sxs-lookup"><span data-stu-id="7318e-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="7318e-105">Tipos flexíveis são úteis, especialmente quando a conversão automática para tipos mais altos na hierarquia de tipos não ocorrerá, mas você ainda deseja habilitar sua funcionalidade trabalhar com qualquer tipo na hierarquia ou qualquer tipo que implementa uma interface.</span><span class="sxs-lookup"><span data-stu-id="7318e-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="7318e-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7318e-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="7318e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7318e-107">Remarks</span></span>

<span data-ttu-id="7318e-108">Na sintaxe anterior, *tipo* representa um tipo base ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="7318e-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="7318e-109">Um tipo flexível é equivalente a um tipo genérico que tem uma restrição que limita os tipos permitidos para tipos que são compatíveis com o tipo base ou interface.</span><span class="sxs-lookup"><span data-stu-id="7318e-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="7318e-110">Ou seja, as duas linhas de código a seguir são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="7318e-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="7318e-111">Tipos flexíveis são úteis em vários tipos de situações.</span><span class="sxs-lookup"><span data-stu-id="7318e-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="7318e-112">Por exemplo, quando você tem uma função de ordem superior (uma função que usa uma função como um argumento), muitas vezes é útil ter a função retornar um tipo flexível.</span><span class="sxs-lookup"><span data-stu-id="7318e-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="7318e-113">No exemplo a seguir, o uso de um tipo flexível com um argumento de sequência no `iterate2` permite que a função de ordem superior trabalhar com funções que geram sequências, matrizes, listas e qualquer outro tipo enumerável.</span><span class="sxs-lookup"><span data-stu-id="7318e-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="7318e-114">Considere duas funções a seguir, um de que retorna uma sequência, o outro retorna um tipo flexível.</span><span class="sxs-lookup"><span data-stu-id="7318e-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="7318e-115">Como outro exemplo, considere a [SEQ. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) função de biblioteca:</span><span class="sxs-lookup"><span data-stu-id="7318e-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="7318e-116">Você pode passar qualquer uma das seguintes sequências enumeráveis para essa função:</span><span class="sxs-lookup"><span data-stu-id="7318e-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="7318e-117">Uma lista de listas</span><span class="sxs-lookup"><span data-stu-id="7318e-117">A list of lists</span></span>
- <span data-ttu-id="7318e-118">Uma lista de matrizes</span><span class="sxs-lookup"><span data-stu-id="7318e-118">A list of arrays</span></span>
- <span data-ttu-id="7318e-119">Uma matriz de listas</span><span class="sxs-lookup"><span data-stu-id="7318e-119">An array of lists</span></span>
- <span data-ttu-id="7318e-120">Uma matriz de sequências</span><span class="sxs-lookup"><span data-stu-id="7318e-120">An array of sequences</span></span>
- <span data-ttu-id="7318e-121">Qualquer outra combinação de sequências enumeráveis</span><span class="sxs-lookup"><span data-stu-id="7318e-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="7318e-122">O seguinte código usa `Seq.concat` para demonstrar os cenários que você pode suportar usando tipos flexíveis.</span><span class="sxs-lookup"><span data-stu-id="7318e-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="7318e-123">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="7318e-123">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="7318e-124">No F #, como em outras linguagens orientadas a objeto, há contextos em que tipos que implementam interfaces ou tipos derivados são automaticamente convertidos em um tipo base ou interface.</span><span class="sxs-lookup"><span data-stu-id="7318e-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="7318e-125">Dessas conversões automáticas ocorrem nos argumentos diretos, mas não quando o tipo é em uma posição subordinada, como parte de um tipo mais complexo, como um tipo de retorno de um tipo de função, ou como um argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="7318e-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="7318e-126">Portanto, a notação de tipo flexível é útil principalmente quando o tipo que você está aplicando-o para é parte de um tipo mais complexo.</span><span class="sxs-lookup"><span data-stu-id="7318e-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="7318e-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7318e-127">See also</span></span>

- [<span data-ttu-id="7318e-128">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="7318e-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="7318e-129">Genéricos</span><span class="sxs-lookup"><span data-stu-id="7318e-129">Generics</span></span>](generics/index.md)
