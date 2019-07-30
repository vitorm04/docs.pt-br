---
title: Tipos flexíveis
description: Saiba como usar F# a anotação de tipo flexível, que indica que um parâmetro, uma variável ou um valor tem um tipo compatível com um tipo especificado.
ms.date: 05/16/2016
ms.openlocfilehash: 43caa6cd35630df648beda5cc43cffae2ecd6f6a
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630269"
---
# <a name="flexible-types"></a><span data-ttu-id="e046b-103">Tipos flexíveis</span><span class="sxs-lookup"><span data-stu-id="e046b-103">Flexible Types</span></span>

<span data-ttu-id="e046b-104">Uma *anotação de tipo flexível* indica que um parâmetro, uma variável ou um valor tem um tipo compatível com um tipo especificado, onde a compatibilidade é determinada pela posição em uma hierarquia orientada a objeto de classes ou interfaces.</span><span class="sxs-lookup"><span data-stu-id="e046b-104">A *flexible type annotation* indicates that a parameter, variable, or value has a type that is compatible with a specified type, where compatibility is determined by position in an object-oriented hierarchy of classes or interfaces.</span></span> <span data-ttu-id="e046b-105">Tipos flexíveis são úteis especificamente quando a conversão automática para tipos mais altos na hierarquia de tipos não ocorre, mas você ainda deseja habilitar sua funcionalidade para trabalhar com qualquer tipo na hierarquia ou qualquer tipo que implemente uma interface.</span><span class="sxs-lookup"><span data-stu-id="e046b-105">Flexible types are useful specifically when the automatic conversion to types higher in the type hierarchy does not occur but you still want to enable your functionality to work with any type in the hierarchy or any type that implements an interface.</span></span>

## <a name="syntax"></a><span data-ttu-id="e046b-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e046b-106">Syntax</span></span>

```fsharp
#type
```

## <a name="remarks"></a><span data-ttu-id="e046b-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="e046b-107">Remarks</span></span>

<span data-ttu-id="e046b-108">Na sintaxe anterior, *Type* representa um tipo base ou uma interface.</span><span class="sxs-lookup"><span data-stu-id="e046b-108">In the previous syntax, *type* represents a base type or an interface.</span></span>

<span data-ttu-id="e046b-109">Um tipo flexível é equivalente a um tipo genérico que tem uma restrição que limita os tipos permitidos a tipos que são compatíveis com o tipo base ou de interface.</span><span class="sxs-lookup"><span data-stu-id="e046b-109">A flexible type is equivalent to a generic type that has a constraint that limits the allowed types to types that are compatible with the base or interface type.</span></span> <span data-ttu-id="e046b-110">Ou seja, as duas linhas de código a seguir são equivalentes.</span><span class="sxs-lookup"><span data-stu-id="e046b-110">That is, the following two lines of code are equivalent.</span></span>

```fsharp
#SomeType

'T when 'T :> SomeType
```

<span data-ttu-id="e046b-111">Tipos flexíveis são úteis em vários tipos de situações.</span><span class="sxs-lookup"><span data-stu-id="e046b-111">Flexible types are useful in several types of situations.</span></span> <span data-ttu-id="e046b-112">Por exemplo, quando você tem uma função de ordem mais alta (uma função que usa uma função como um argumento), muitas vezes é útil fazer com que a função retorne um tipo flexível.</span><span class="sxs-lookup"><span data-stu-id="e046b-112">For example, when you have a higher order function (a function that takes a function as an argument), it is often useful to have the function return a flexible type.</span></span> <span data-ttu-id="e046b-113">No exemplo a seguir, o uso de um tipo flexível com um argumento Sequence em `iterate2` permite que a função de ordem superior funcione com funções que geram sequências, matrizes, listas e qualquer outro tipo enumerável.</span><span class="sxs-lookup"><span data-stu-id="e046b-113">In the following example, the use of a flexible type with a sequence argument in `iterate2` enables the higher order function to work with functions that generate sequences, arrays, lists, and any other enumerable type.</span></span>

<span data-ttu-id="e046b-114">Considere as duas funções a seguir, uma das quais retorna uma sequência, a outra que retorna um tipo flexível.</span><span class="sxs-lookup"><span data-stu-id="e046b-114">Consider the following two functions, one of which returns a sequence, the other of which returns a flexible type.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4101.fs)]

<span data-ttu-id="e046b-115">Como outro exemplo, considere a função de biblioteca [Seq. Concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) :</span><span class="sxs-lookup"><span data-stu-id="e046b-115">As another example, consider the [Seq.concat](https://msdn.microsoft.com/library/2eeb69a9-fc2f-4b7d-8dee-101fa2b00712) library function:</span></span>

```fsharp
val concat: sequences:seq<#seq<'T>> -> seq<'T>
```

<span data-ttu-id="e046b-116">Você pode passar qualquer uma das sequências enumeráveis a seguir para esta função:</span><span class="sxs-lookup"><span data-stu-id="e046b-116">You can pass any of the following enumerable sequences to this function:</span></span>

- <span data-ttu-id="e046b-117">Uma lista de listas</span><span class="sxs-lookup"><span data-stu-id="e046b-117">A list of lists</span></span>
- <span data-ttu-id="e046b-118">Uma lista de matrizes</span><span class="sxs-lookup"><span data-stu-id="e046b-118">A list of arrays</span></span>
- <span data-ttu-id="e046b-119">Uma matriz de listas</span><span class="sxs-lookup"><span data-stu-id="e046b-119">An array of lists</span></span>
- <span data-ttu-id="e046b-120">Uma matriz de sequências</span><span class="sxs-lookup"><span data-stu-id="e046b-120">An array of sequences</span></span>
- <span data-ttu-id="e046b-121">Qualquer outra combinação de sequências enumeráveis</span><span class="sxs-lookup"><span data-stu-id="e046b-121">Any other combination of enumerable sequences</span></span>

<span data-ttu-id="e046b-122">O código a seguir `Seq.concat` usa o para demonstrar os cenários para os quais você pode dar suporte usando tipos flexíveis.</span><span class="sxs-lookup"><span data-stu-id="e046b-122">The following code uses `Seq.concat` to demonstrate the scenarios that you can support by using flexible types.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet4102.fs)]

<span data-ttu-id="e046b-123">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="e046b-123">The output is as follows.</span></span>

```
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
seq [1; 2; 3; 4; ...]
```

<span data-ttu-id="e046b-124">No F#, como em outras linguagens orientadas a objeto, há contextos nos quais tipos ou tipos derivados que implementam interfaces são convertidos automaticamente em um tipo base ou tipo de interface.</span><span class="sxs-lookup"><span data-stu-id="e046b-124">In F#, as in other object-oriented languages, there are contexts in which derived types or types that implement interfaces are automatically converted to a base type or interface type.</span></span> <span data-ttu-id="e046b-125">Essas conversões automáticas ocorrem em argumentos diretos, mas não quando o tipo está em uma posição subordinada, como parte de um tipo mais complexo, como um tipo de retorno de um tipo de função, ou como um argumento de tipo.</span><span class="sxs-lookup"><span data-stu-id="e046b-125">These automatic conversions occur in direct arguments, but not when the type is in a subordinate position, as part of a more complex type such as a return type of a function type, or as a type argument.</span></span> <span data-ttu-id="e046b-126">Assim, a notação de tipo flexível é útil principalmente quando o tipo para o qual você está aplicando faz parte de um tipo mais complexo.</span><span class="sxs-lookup"><span data-stu-id="e046b-126">Thus, the flexible type notation is primarily useful when the type you are applying it to is part of a more complex type.</span></span>

## <a name="see-also"></a><span data-ttu-id="e046b-127">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e046b-127">See also</span></span>

- [<span data-ttu-id="e046b-128">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="e046b-128">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="e046b-129">Genéricos</span><span class="sxs-lookup"><span data-stu-id="e046b-129">Generics</span></span>](./generics/index.md)
