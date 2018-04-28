---
title: 'Loops: expressão for...in (F#)'
description: 'Veja como o F # loop for... na expressão de construção de loop é usado para iterar sobre a correspondência de um padrão de uma coleção enumerável.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: eaf0f4fc6419d8e0bff46795120ee5e42c4efe1d
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="loops-forin-expression"></a><span data-ttu-id="4edd7-103">Loops: expressão for...in</span><span class="sxs-lookup"><span data-stu-id="4edd7-103">Loops: for...in Expression</span></span>

<span data-ttu-id="4edd7-104">Esta construção de loop é usada para iterar sobre a correspondência de um padrão de uma coleção enumerável como uma expressão de intervalo, sequência, lista, matriz ou outra construção que oferece suporte à enumeração.</span><span class="sxs-lookup"><span data-stu-id="4edd7-104">This looping construct is used to iterate over the matches of a pattern in an enumerable collection such as a range expression, sequence, list, array, or other construct that supports enumeration.</span></span>


## <a name="syntax"></a><span data-ttu-id="4edd7-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4edd7-105">Syntax</span></span>

```fsharp
for pattern in enumerable-expression do
    body-expression
```

## <a name="remarks"></a><span data-ttu-id="4edd7-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="4edd7-106">Remarks</span></span>
<span data-ttu-id="4edd7-107">O `for...in` expressão pode ser comparada com o `for each` instrução em outras linguagens .NET porque ele é usado para executar um loop sobre os valores em uma coleção enumerável.</span><span class="sxs-lookup"><span data-stu-id="4edd7-107">The `for...in` expression can be compared to the `for each` statement in other .NET languages because it is used to loop over the values in an enumerable collection.</span></span> <span data-ttu-id="4edd7-108">No entanto, `for...in` também oferece suporte a padrões correspondentes na coleção em vez de apenas iteração pela coleção inteira.</span><span class="sxs-lookup"><span data-stu-id="4edd7-108">However, `for...in` also supports pattern matching over the collection instead of just iteration over the whole collection.</span></span>

<span data-ttu-id="4edd7-109">A expressão enumerável pode ser especificada como uma coleção enumerável ou, usando o `..` operador, como um intervalo de um tipo integral.</span><span class="sxs-lookup"><span data-stu-id="4edd7-109">The enumerable expression can be specified as an enumerable collection or, by using the `..` operator, as a range on an integral type.</span></span> <span data-ttu-id="4edd7-110">Coleções enumeráveis incluem listas, as sequências, matrizes, conjuntos, mapas e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="4edd7-110">Enumerable collections include lists, sequences, arrays, sets, maps, and so on.</span></span> <span data-ttu-id="4edd7-111">Qualquer tipo que implementa `System.Collections.IEnumerable` pode ser usado.</span><span class="sxs-lookup"><span data-stu-id="4edd7-111">Any type that implements `System.Collections.IEnumerable` can be used.</span></span>

<span data-ttu-id="4edd7-112">Quando você expressar um intervalo usando os `..` operador, você pode usar a sintaxe a seguir.</span><span class="sxs-lookup"><span data-stu-id="4edd7-112">When you express a range by using the `..` operator, you can use the following syntax.</span></span>

<span data-ttu-id="4edd7-113">*Iniciar* ...</span><span class="sxs-lookup"><span data-stu-id="4edd7-113">*start* ..</span></span> <span data-ttu-id="4edd7-114">*Concluir*</span><span class="sxs-lookup"><span data-stu-id="4edd7-114">*finish*</span></span>

<span data-ttu-id="4edd7-115">Você também pode usar uma versão que inclui um incremento chamado o *ignorar*, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4edd7-115">You can also use a version that includes an increment called the *skip*, as in the following code.</span></span>

<span data-ttu-id="4edd7-116">*Iniciar* ...</span><span class="sxs-lookup"><span data-stu-id="4edd7-116">*start* ..</span></span> <span data-ttu-id="4edd7-117">*Ignorar* ...</span><span class="sxs-lookup"><span data-stu-id="4edd7-117">*skip* ..</span></span> <span data-ttu-id="4edd7-118">*Concluir*</span><span class="sxs-lookup"><span data-stu-id="4edd7-118">*finish*</span></span>

<span data-ttu-id="4edd7-119">Quando você usa intervalos integrais e uma variável de contador simples como padrão, o comportamento típico é para incrementar a variável de contador em 1 em cada iteração, mas se o intervalo inclui um valor skip, o contador é incrementado pelo valor skip em vez disso.</span><span class="sxs-lookup"><span data-stu-id="4edd7-119">When you use integral ranges and a simple counter variable as a pattern, the typical behavior is to increment the counter variable by 1 on each iteration, but if the range includes a skip value, the counter is incremented by the skip value instead.</span></span>

<span data-ttu-id="4edd7-120">Valores que correspondam ao padrão também podem ser usados na expressão de corpo.</span><span class="sxs-lookup"><span data-stu-id="4edd7-120">Values matched in the pattern can also be used in the body expression.</span></span>

<span data-ttu-id="4edd7-121">Os exemplos de código a seguir ilustram o uso do `for...in` expressão.</span><span class="sxs-lookup"><span data-stu-id="4edd7-121">The following code examples illustrate the use of the `for...in` expression.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5201.fs)]

<span data-ttu-id="4edd7-122">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="4edd7-122">The output is as follows.</span></span>

```
1
5
100
450
788
```

<span data-ttu-id="4edd7-123">O exemplo a seguir mostra como criar um loop em uma sequência e como usar um padrão de tupla em vez de uma variável simple.</span><span class="sxs-lookup"><span data-stu-id="4edd7-123">The following example shows how to loop over a sequence, and how to use a tuple pattern instead of a simple variable.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5202.fs)]

<span data-ttu-id="4edd7-124">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="4edd7-124">The output is as follows.</span></span>

```
1 squared is 1
2 squared is 4
3 squared is 9
4 squared is 16
5 squared is 25
6 squared is 36
7 squared is 49
8 squared is 64
9 squared is 81
10 squared is 100
```

<span data-ttu-id="4edd7-125">O exemplo a seguir mostra como criar um loop em um intervalo de inteiros simples.</span><span class="sxs-lookup"><span data-stu-id="4edd7-125">The following example shows how to loop over a simple integer range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5203.fs)]

<span data-ttu-id="4edd7-126">A saída de function1 é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="4edd7-126">The output of function1 is as follows.</span></span>

```
1 2 3 4 5 6 7 8 9 10
```

<span data-ttu-id="4edd7-127">O exemplo a seguir mostra como criar um loop em um intervalo com um salto de 2, que inclui todos os outros elementos do intervalo.</span><span class="sxs-lookup"><span data-stu-id="4edd7-127">The following example shows how to loop over a range with a skip of 2, which includes every other element of the range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5204.fs)]

<span data-ttu-id="4edd7-128">A saída de `function2` é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="4edd7-128">The output of `function2` is as follows.</span></span>

```
1 3 5 7 9
```

<span data-ttu-id="4edd7-129">O exemplo a seguir mostra como usar um intervalo de caracteres.</span><span class="sxs-lookup"><span data-stu-id="4edd7-129">The following example shows how to use a character range.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5205.fs)]

<span data-ttu-id="4edd7-130">A saída de `function3` é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="4edd7-130">The output of `function3` is as follows.</span></span>

```
a b c d e f g h i j k l m n o p q r s t u v w x y z
```

<span data-ttu-id="4edd7-131">O exemplo a seguir mostra como usar um valor negativo skip para uma iteração inversa.</span><span class="sxs-lookup"><span data-stu-id="4edd7-131">The following example shows how to use a negative skip value for a reverse iteration.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5208.fs)]

<span data-ttu-id="4edd7-132">A saída de `function4` é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="4edd7-132">The output of `function4` is as follows.</span></span>

```
10 9 8 7 6 5 4 3 2 1 ... Lift off!
```

<span data-ttu-id="4edd7-133">O início e fim do intervalo também podem ser expressões, como funções, como no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="4edd7-133">The beginning and ending of the range can also be expressions, such as functions, as in the following code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5206.fs)]

<span data-ttu-id="4edd7-134">A saída de `function5` com essa entrada é o seguinte.</span><span class="sxs-lookup"><span data-stu-id="4edd7-134">The output of `function5` with this input is as follows.</span></span>

```
2 3 4 5 6 7 8 9 10 11 12 13 14 15 16 17 18
```

<span data-ttu-id="4edd7-135">O exemplo a seguir mostra o uso de um caractere curinga (_) quando o elemento não é necessária no loop.</span><span class="sxs-lookup"><span data-stu-id="4edd7-135">The next example shows the use of a wildcard character (_) when the element is not needed in the loop.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet5207.fs)]

<span data-ttu-id="4edd7-136">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="4edd7-136">The output is as follows.</span></span>

```
Number of elements in list1: 5
```

<span data-ttu-id="4edd7-137">`Note` Você pode usar `for...in` em expressões de sequência e outras expressões de cálculo, caso em que uma versão personalizada do `for...in` expressão é usada.</span><span class="sxs-lookup"><span data-stu-id="4edd7-137">`Note` You can use `for...in` in sequence expressions and other computation expressions, in which case a customized version of the `for...in` expression is used.</span></span> <span data-ttu-id="4edd7-138">Para obter mais informações, consulte [sequências](sequences.md), [fluxos de trabalho assíncronos](asynchronous-workflows.md), e [expressões de computação](computation-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="4edd7-138">For more information, see [Sequences](sequences.md), [Asynchronous Workflows](asynchronous-workflows.md), and [Computation Expressions](computation-expressions.md).</span></span>


## <a name="see-also"></a><span data-ttu-id="4edd7-139">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4edd7-139">See Also</span></span>
[<span data-ttu-id="4edd7-140">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="4edd7-140">F# Language Reference</span></span>](index.md)

[<span data-ttu-id="4edd7-141">Loops: `for...to` expressão</span><span class="sxs-lookup"><span data-stu-id="4edd7-141">Loops: `for...to` Expression</span></span>](loops-for-to-expression.md)

[<span data-ttu-id="4edd7-142">Loops: `while...do` expressão</span><span class="sxs-lookup"><span data-stu-id="4edd7-142">Loops: `while...do` Expression</span></span>](loops-while-do-expression.md)
