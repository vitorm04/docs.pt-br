---
title: Matrizes
description: 'Saiba como criar e usar matrizes na linguagem de programação F #.'
ms.date: 08/13/2020
ms.openlocfilehash: 37f781ccd2c7bc2ca2c7b93bda53bbb3ea93b504
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608507"
---
# <a name="arrays"></a><span data-ttu-id="5e667-103">Matrizes</span><span class="sxs-lookup"><span data-stu-id="5e667-103">Arrays</span></span>

<span data-ttu-id="5e667-104">As matrizes são coleções de tamanho fixo, com base em zero e mutáveis de elementos de dados consecutivos que são do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="5e667-104">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="create-arrays"></a><span data-ttu-id="5e667-105">Criar matrizes</span><span class="sxs-lookup"><span data-stu-id="5e667-105">Create arrays</span></span>

<span data-ttu-id="5e667-106">Você pode criar matrizes de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="5e667-106">You can create arrays in several ways.</span></span> <span data-ttu-id="5e667-107">Você pode criar uma pequena matriz listando valores consecutivos entre `[|` e `|]` e separados por ponto e vírgula, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="5e667-107">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="5e667-108">Você também pode colocar cada elemento em uma linha separada; nesse caso, o separador de ponto-e-vírgula é opcional.</span><span class="sxs-lookup"><span data-stu-id="5e667-108">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="5e667-109">O tipo dos elementos da matriz é inferido a partir dos literais usados e deve ser consistente.</span><span class="sxs-lookup"><span data-stu-id="5e667-109">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="5e667-110">O código a seguir causa um erro porque 1,0 é um float e 2 e 3 são inteiros.</span><span class="sxs-lookup"><span data-stu-id="5e667-110">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="5e667-111">Você também pode usar expressões de sequência para criar matrizes.</span><span class="sxs-lookup"><span data-stu-id="5e667-111">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="5e667-112">Veja a seguir um exemplo que cria uma matriz de quadrados de inteiros de 1 a 10.</span><span class="sxs-lookup"><span data-stu-id="5e667-112">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="5e667-113">Para criar uma matriz na qual todos os elementos são inicializados como zero, use `Array.zeroCreate` .</span><span class="sxs-lookup"><span data-stu-id="5e667-113">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="access-elements"></a><span data-ttu-id="5e667-114">Elementos de acesso</span><span class="sxs-lookup"><span data-stu-id="5e667-114">Access elements</span></span>

<span data-ttu-id="5e667-115">Você pode acessar elementos de matriz usando um operador de ponto ( `.` ) e colchetes ( `[` e `]` ).</span><span class="sxs-lookup"><span data-stu-id="5e667-115">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="5e667-116">Os índices de matriz começam em 0.</span><span class="sxs-lookup"><span data-stu-id="5e667-116">Array indexes start at 0.</span></span>

<span data-ttu-id="5e667-117">Você também pode acessar elementos de matriz usando a notação de fatia, que permite especificar um subintervalo da matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-117">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="5e667-118">Seguem exemplos de notação de fatia.</span><span class="sxs-lookup"><span data-stu-id="5e667-118">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="5e667-119">Quando a notação de fatia é usada, uma nova cópia da matriz é criada.</span><span class="sxs-lookup"><span data-stu-id="5e667-119">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="5e667-120">Módulos e tipos de matriz</span><span class="sxs-lookup"><span data-stu-id="5e667-120">Array types and modules</span></span>

<span data-ttu-id="5e667-121">O tipo de todas as matrizes F # é o tipo de .NET Framework <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e667-121">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="5e667-122">Portanto, as matrizes F # oferecem suporte a todas as funcionalidades disponíveis no <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e667-122">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="5e667-123">O [ `Array` módulo](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) dá suporte a operações em matrizes unidimensionais.</span><span class="sxs-lookup"><span data-stu-id="5e667-123">The [`Array` module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="5e667-124">Os módulos `Array2D` , `Array3D` e `Array4D` contêm funções que dão suporte a operações em matrizes de duas, três e quatro dimensões, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5e667-124">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="5e667-125">Você pode criar matrizes de classificação maior que quatro usando <xref:System.Array?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5e667-125">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="5e667-126">Funções simples</span><span class="sxs-lookup"><span data-stu-id="5e667-126">Simple functions</span></span>

<span data-ttu-id="5e667-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) Obtém um elemento.</span><span class="sxs-lookup"><span data-stu-id="5e667-127">[`Array.get`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#get) gets an element.</span></span> <span data-ttu-id="5e667-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) fornece o comprimento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-128">[`Array.length`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#length) gives the length of an array.</span></span> <span data-ttu-id="5e667-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) define um elemento para um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="5e667-129">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="5e667-130">O exemplo de código a seguir ilustra o uso dessas funções.</span><span class="sxs-lookup"><span data-stu-id="5e667-130">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="5e667-131">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-131">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="5e667-132">Funções que criam matrizes</span><span class="sxs-lookup"><span data-stu-id="5e667-132">Functions that create arrays</span></span>

<span data-ttu-id="5e667-133">Várias funções criam matrizes sem a necessidade de uma matriz existente.</span><span class="sxs-lookup"><span data-stu-id="5e667-133">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="5e667-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) Cria uma nova matriz que não contém nenhum elemento.</span><span class="sxs-lookup"><span data-stu-id="5e667-134">[`Array.empty`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#empty) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="5e667-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) Cria uma matriz de um tamanho especificado e define todos os elementos para os valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="5e667-135">[`Array.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#create) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="5e667-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) Cria uma matriz, dada uma dimensão e uma função para gerar os elementos.</span><span class="sxs-lookup"><span data-stu-id="5e667-136">[`Array.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#init) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="5e667-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) Cria uma matriz na qual todos os elementos são inicializados com o valor zero para o tipo da matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-137">[`Array.zeroCreate`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zeroCreate) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="5e667-138">O código a seguir demonstra essas funções.</span><span class="sxs-lookup"><span data-stu-id="5e667-138">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="5e667-139">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-139">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="5e667-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) Cria uma nova matriz que contém elementos que são copiados de uma matriz existente.</span><span class="sxs-lookup"><span data-stu-id="5e667-140">[`Array.copy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#copy) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="5e667-141">Observe que a cópia é uma cópia superficial, o que significa que se o tipo de elemento for um tipo de referência, somente a referência será copiada, não o objeto subjacente.</span><span class="sxs-lookup"><span data-stu-id="5e667-141">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="5e667-142">O exemplo de código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="5e667-142">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="5e667-143">A saída do código anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="5e667-143">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="5e667-144">A cadeia de caracteres `Test1` aparece apenas na primeira matriz porque a operação de criação de um novo elemento substitui a referência em `firstArray` , mas não afeta a referência original a uma cadeia de caracteres vazia que ainda está presente no `secondArray` .</span><span class="sxs-lookup"><span data-stu-id="5e667-144">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="5e667-145">A cadeia de caracteres `Test2` aparece em ambas as matrizes porque a `Insert` operação no <xref:System.Text.StringBuilder?displayProperty=nameWithType> tipo afeta o <xref:System.Text.StringBuilder?displayProperty=nameWithType> objeto subjacente, que é referenciado em ambas as matrizes.</span><span class="sxs-lookup"><span data-stu-id="5e667-145">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="5e667-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) gera uma nova matriz de um subintervalo de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-146">[`Array.sub`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sub) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="5e667-147">Você especifica o subintervalo fornecendo o índice inicial e o comprimento.</span><span class="sxs-lookup"><span data-stu-id="5e667-147">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="5e667-148">O código a seguir demonstra o uso de `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="5e667-148">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="5e667-149">A saída mostra que a submatriz começa no elemento 5 e contém 10 elementos.</span><span class="sxs-lookup"><span data-stu-id="5e667-149">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="5e667-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) Cria uma nova matriz combinando duas matrizes existentes.</span><span class="sxs-lookup"><span data-stu-id="5e667-150">[`Array.append`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#append) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="5e667-151">O código a seguir demonstra o **array. Append**.</span><span class="sxs-lookup"><span data-stu-id="5e667-151">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="5e667-152">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-152">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="5e667-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) seleciona os elementos de uma matriz para incluir em uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-153">[`Array.choose`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#choose) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="5e667-154">O código a seguir demonstra `Array.choose` .</span><span class="sxs-lookup"><span data-stu-id="5e667-154">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="5e667-155">Observe que o tipo de elemento da matriz não precisa corresponder ao tipo de valor retornado no tipo de opção.</span><span class="sxs-lookup"><span data-stu-id="5e667-155">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="5e667-156">Neste exemplo, o tipo de elemento é `int` e a opção é o resultado de uma função polinomial, `elem*elem - 1` , como um número de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="5e667-156">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="5e667-157">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-157">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="5e667-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) executa uma função especificada em cada elemento da matriz de uma matriz existente e, em seguida, coleta os elementos gerados pela função e os combina em uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-158">[`Array.collect`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#collect) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="5e667-159">O código a seguir demonstra `Array.collect` .</span><span class="sxs-lookup"><span data-stu-id="5e667-159">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="5e667-160">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-160">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="5e667-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) usa uma sequência de matrizes e as combina em uma única matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-161">[`Array.concat`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#concat) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="5e667-162">O código a seguir demonstra `Array.concat` .</span><span class="sxs-lookup"><span data-stu-id="5e667-162">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="5e667-163">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-163">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="5e667-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) usa uma função de condição booliana e gera uma nova matriz que contém somente os elementos da matriz de entrada para a qual a condição é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="5e667-164">[`Array.filter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#filter) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="5e667-165">O código a seguir demonstra `Array.filter` .</span><span class="sxs-lookup"><span data-stu-id="5e667-165">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="5e667-166">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-166">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="5e667-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) gera uma nova matriz revertendo a ordem de uma matriz existente.</span><span class="sxs-lookup"><span data-stu-id="5e667-167">[`Array.rev`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#rev) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="5e667-168">O código a seguir demonstra `Array.rev` .</span><span class="sxs-lookup"><span data-stu-id="5e667-168">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="5e667-169">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-169">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="5e667-170">Você pode combinar facilmente funções no módulo de matriz que transformam matrizes usando o operador de pipeline ( `|>` ), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="5e667-170">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="5e667-171">A saída é</span><span class="sxs-lookup"><span data-stu-id="5e667-171">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="5e667-172">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="5e667-172">Multidimensional arrays</span></span>

<span data-ttu-id="5e667-173">Uma matriz multidimensional pode ser criada, mas não há nenhuma sintaxe para gravar um literal de matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="5e667-173">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="5e667-174">Use o operador [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) para criar uma matriz de uma sequência de sequências de elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-174">Use the operator [`array2D`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="5e667-175">As sequências podem ser literais de matriz ou lista.</span><span class="sxs-lookup"><span data-stu-id="5e667-175">The sequences can be array or list literals.</span></span> <span data-ttu-id="5e667-176">Por exemplo, o código a seguir cria uma matriz bidimensional.</span><span class="sxs-lookup"><span data-stu-id="5e667-176">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="5e667-177">Você também pode usar a função [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) para inicializar matrizes de duas dimensões e funções semelhantes estão disponíveis para matrizes de três e quatro dimensões.</span><span class="sxs-lookup"><span data-stu-id="5e667-177">You can also use the function [`Array2D.init`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#init) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="5e667-178">Essas funções usam uma função que é usada para criar os elementos.</span><span class="sxs-lookup"><span data-stu-id="5e667-178">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="5e667-179">Para criar uma matriz bidimensional que contém elementos definidos como um valor inicial em vez de especificar uma função, use a [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) função, que também está disponível para matrizes de até quatro dimensões.</span><span class="sxs-lookup"><span data-stu-id="5e667-179">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-array2dmodule.html#create) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="5e667-180">O exemplo de código a seguir mostra primeiro como criar uma matriz de matrizes que contêm os elementos desejados e, em seguida, usa `Array2D.init` para gerar a matriz bidimensional desejada.</span><span class="sxs-lookup"><span data-stu-id="5e667-180">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="5e667-181">A indexação de matriz e a sintaxe de divisão têm suporte para matrizes até a classificação 4.</span><span class="sxs-lookup"><span data-stu-id="5e667-181">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="5e667-182">Quando você especifica um índice em várias dimensões, usa vírgulas para separar os índices, conforme ilustrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="5e667-182">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="5e667-183">O tipo de uma matriz bidimensional é escrito como `<type>[,]` (por exemplo, `int[,]` `double[,]` ), e o tipo de uma matriz tridimensional é escrito como `<type>[,,]` e assim por diante para matrizes de dimensões superiores.</span><span class="sxs-lookup"><span data-stu-id="5e667-183">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="5e667-184">Somente um subconjunto das funções disponíveis para matrizes unidimensionais também está disponível para matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="5e667-184">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="5e667-185">Fatias de matrizes e matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="5e667-185">Array slicing and multidimensional arrays</span></span>

<span data-ttu-id="5e667-186">Em uma matriz bidimensional (uma matriz), você pode extrair uma submatriz especificando intervalos e usando um caractere curinga ( `*` ) para especificar linhas ou colunas inteiras.</span><span class="sxs-lookup"><span data-stu-id="5e667-186">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
// Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="5e667-187">Você pode decompor uma matriz multidimensional em subconjuntos da mesma dimensão ou menor.</span><span class="sxs-lookup"><span data-stu-id="5e667-187">You can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="5e667-188">Por exemplo, você pode obter um vetor de uma matriz especificando uma única linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="5e667-188">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="5e667-189">Você pode usar essa sintaxe de divisão para tipos que implementam os operadores de acesso do elemento e os métodos sobrecarregados `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="5e667-189">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="5e667-190">Por exemplo, o código a seguir cria um tipo de matriz que encapsula a matriz 2D F #, implementa uma propriedade item para fornecer suporte para indexação de matriz e implementa três versões do `GetSlice` .</span><span class="sxs-lookup"><span data-stu-id="5e667-190">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="5e667-191">Se você puder usar esse código como um modelo para os tipos de matriz, poderá usar todas as operações de divisão que esta seção descreve.</span><span class="sxs-lookup"><span data-stu-id="5e667-191">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

```fsharp
type Matrix<'T>(N: int, M: int) =
    let internalArray = Array2D.zeroCreate<'T> N M

    member this.Item
        with get(a: int, b: int) = internalArray.[a, b]
        and set(a: int, b: int) (value:'T) = internalArray.[a, b] <- value

    member this.GetSlice(rowStart: int option, rowFinish : int option, colStart: int option, colFinish : int option) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[rowStart..rowFinish, colStart..colFinish]

    member this.GetSlice(row: int, colStart: int option, colFinish: int option) =
        let colStart =
            match colStart with
            | Some(v) -> v
            | None -> 0
        let colFinish =
            match colFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(1) - 1
        internalArray.[row, colStart..colFinish]

    member this.GetSlice(rowStart: int option, rowFinish: int option, col: int) =
        let rowStart =
            match rowStart with
            | Some(v) -> v
            | None -> 0
        let rowFinish =
            match rowFinish with
            | Some(v) -> v
            | None -> internalArray.GetLength(0) - 1
        internalArray.[rowStart..rowFinish, col]

module test =
    let generateTestMatrix x y =
        let matrix = new Matrix<float>(3, 3)
        for i in 0..2 do
            for j in 0..2 do
                matrix.[i, j] <- float(i) * x - float(j) * y
        matrix

    let test1 = generateTestMatrix 2.3 1.1
    let submatrix = test1.[0..1, 0..1]
    printfn "%A" submatrix

    let firstRow = test1.[0,*]
    let secondRow = test1.[1,*]
    let firstCol = test1.[*,0]
    printfn "%A" firstCol
```

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="5e667-192">Funções booleanas em matrizes</span><span class="sxs-lookup"><span data-stu-id="5e667-192">Boolean functions on arrays</span></span>

<span data-ttu-id="5e667-193">As funções [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) e os [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) elementos de teste em uma ou duas matrizes, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="5e667-193">The functions [`Array.exists`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists) and [`Array.exists2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#exists2) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="5e667-194">Essas funções usam uma função de teste e retornam `true` se há um elemento (ou par de elementos para `Array.exists2` ) que satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="5e667-194">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="5e667-195">O código a seguir demonstra o uso de `Array.exists` e `Array.exists2` .</span><span class="sxs-lookup"><span data-stu-id="5e667-195">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="5e667-196">Nesses exemplos, novas funções são criadas aplicando-se apenas um dos argumentos, nesses casos, o argumento da função.</span><span class="sxs-lookup"><span data-stu-id="5e667-196">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="5e667-197">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-197">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="5e667-198">Da mesma forma, a função [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) testa uma matriz para determinar se cada elemento atende a uma condição booliana.</span><span class="sxs-lookup"><span data-stu-id="5e667-198">Similarly, the function [`Array.forall`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="5e667-199">A variação [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) faz a mesma coisa usando uma função booleana que envolve elementos de duas matrizes de comprimento igual.</span><span class="sxs-lookup"><span data-stu-id="5e667-199">The variation [`Array.forall2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#forall2) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="5e667-200">O código a seguir ilustra o uso dessas funções.</span><span class="sxs-lookup"><span data-stu-id="5e667-200">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="5e667-201">A saída desses exemplos é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-201">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="search-arrays"></a><span data-ttu-id="5e667-202">Pesquisar matrizes</span><span class="sxs-lookup"><span data-stu-id="5e667-202">Search arrays</span></span>

<span data-ttu-id="5e667-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) usa uma função booliana e retorna o primeiro elemento para o qual a função retorna `true` , ou gera um <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> elemento If nenhum que satisfaça a condição é encontrado.</span><span class="sxs-lookup"><span data-stu-id="5e667-203">[`Array.find`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#find) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="5e667-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) é como `Array.find` , exceto pelo fato de que ele retorna o índice do elemento em vez do próprio elemento.</span><span class="sxs-lookup"><span data-stu-id="5e667-204">[`Array.findIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#findIndex) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="5e667-205">O código a seguir usa `Array.find` e `Array.findIndex` para localizar um número que seja um cubo perfeito e um quadrado perfeitos.</span><span class="sxs-lookup"><span data-stu-id="5e667-205">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="5e667-206">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-206">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="5e667-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) é como `Array.find` , exceto que seu resultado é um tipo de opção e retorna `None` se nenhum elemento for encontrado.</span><span class="sxs-lookup"><span data-stu-id="5e667-207">[`Array.tryFind`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFind) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="5e667-208">`Array.tryFind` deve ser usado em vez de `Array.find` quando você não sabe se um elemento correspondente está na matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-208">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="5e667-209">Da mesma forma, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) é como, `Array.findIndex` exceto que o tipo de opção é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="5e667-209">Similarly, [`Array.tryFindIndex`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryFindIndex) is like `Array.findIndex` except that the option type is the return value.</span></span> <span data-ttu-id="5e667-210">Se nenhum elemento for encontrado, a opção será `None` .</span><span class="sxs-lookup"><span data-stu-id="5e667-210">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="5e667-211">O código a seguir demonstra o uso de `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="5e667-211">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="5e667-212">Esse código depende do código anterior.</span><span class="sxs-lookup"><span data-stu-id="5e667-212">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="5e667-213">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-213">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
Failed to find a matching element.
```

<span data-ttu-id="5e667-214">Use [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) quando precisar transformar um elemento, além de localizá-lo.</span><span class="sxs-lookup"><span data-stu-id="5e667-214">Use [`Array.tryPick`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#tryPick) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="5e667-215">O resultado é o primeiro elemento para o qual a função retorna o elemento transformado como um valor de opção ou `None` se nenhum elemento desse tipo é encontrado.</span><span class="sxs-lookup"><span data-stu-id="5e667-215">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="5e667-216">O código a seguir demonstra o uso de `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="5e667-216">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="5e667-217">Nesse caso, em vez de uma expressão lambda, várias funções auxiliares locais são definidas para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="5e667-217">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="5e667-218">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-218">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
Did not find an element that is both a perfect square and a perfect cube.
```

### <a name="perform-computations-on-arrays"></a><span data-ttu-id="5e667-219">Executar cálculos em matrizes</span><span class="sxs-lookup"><span data-stu-id="5e667-219">Perform computations on arrays</span></span>

<span data-ttu-id="5e667-220">A [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) função retorna a média de cada elemento em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-220">The [`Array.average`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#average) function returns the average of each element in an array.</span></span> <span data-ttu-id="5e667-221">Ele é limitado a tipos de elementos que dão suporte à divisão exata por um inteiro, que inclui tipos de ponto flutuante, mas não tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="5e667-221">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="5e667-222">A [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) função retorna a média dos resultados da chamada de uma função em cada elemento.</span><span class="sxs-lookup"><span data-stu-id="5e667-222">The [`Array.averageBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#averageBy) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="5e667-223">Para uma matriz de tipo integral, você pode usar `Array.averageBy` e fazer com que a função Converta cada elemento em um tipo de ponto flutuante para a computação.</span><span class="sxs-lookup"><span data-stu-id="5e667-223">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="5e667-224">Use [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) ou [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) para obter o elemento máximo ou mínimo, se o tipo de elemento oferecer suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="5e667-224">Use [`Array.max`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#max) or [`Array.min`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#min) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="5e667-225">Da mesma forma, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) e [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) permite que uma função seja executada primeiro, talvez para transformar em um tipo que dê suporte à comparação.</span><span class="sxs-lookup"><span data-stu-id="5e667-225">Similarly, [`Array.maxBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#maxBy) and [`Array.minBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#minBy) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="5e667-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) Adiciona os elementos de uma matriz e [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) chama uma função em cada elemento e adiciona os resultados juntos.</span><span class="sxs-lookup"><span data-stu-id="5e667-226">[`Array.sum`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sum) adds the elements of an array, and [`Array.sumBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sumBy) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="5e667-227">Para executar uma função em cada elemento em uma matriz sem armazenar os valores de retorno, use [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter) .</span><span class="sxs-lookup"><span data-stu-id="5e667-227">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter).</span></span> <span data-ttu-id="5e667-228">Para uma função que envolva duas matrizes de comprimento igual, use [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2) .</span><span class="sxs-lookup"><span data-stu-id="5e667-228">For a function involving two arrays of equal length, use [`Array.iter2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iter2).</span></span> <span data-ttu-id="5e667-229">Se você também precisar manter uma matriz dos resultados da função, use [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) ou [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2) , que opera em duas matrizes por vez.</span><span class="sxs-lookup"><span data-stu-id="5e667-229">If you also need to keep an array of the results of the function, use [`Array.map`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map) or [`Array.map2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#map2), which operates on two arrays at a time.</span></span>

<span data-ttu-id="5e667-230">As variações [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) e [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) permitem que o índice do elemento esteja envolvido na computação; o mesmo é verdadeiro para [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) e [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2) .</span><span class="sxs-lookup"><span data-stu-id="5e667-230">The variations [`Array.iteri`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri) and [`Array.iteri2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#iteri2) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi) and [`Array.mapi2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#mapi2).</span></span>

<span data-ttu-id="5e667-231">As funções [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold) , [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack) , [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce) , [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack) , [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan) e [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) executam algoritmos que envolvem todos os elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-231">The functions [`Array.fold`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold), [`Array.foldBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack), [`Array.reduce`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduce), [`Array.reduceBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#reduceBack), [`Array.scan`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scan), and [`Array.scanBack`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#scanBack) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="5e667-232">Da mesma forma, as variações [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) e [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) executam cálculos em duas matrizes.</span><span class="sxs-lookup"><span data-stu-id="5e667-232">Similarly, the variations [`Array.fold2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fold2) and [`Array.foldBack2`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#foldBack2) perform computations on two arrays.</span></span>

<span data-ttu-id="5e667-233">Essas funções para executar computações correspondem às funções de mesmo nome no módulo de [lista](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span><span class="sxs-lookup"><span data-stu-id="5e667-233">These functions for performing computations correspond to the functions of the same name in the [List module](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-listmodule.html).</span></span> <span data-ttu-id="5e667-234">Para obter exemplos de uso, consulte [listas](lists.md).</span><span class="sxs-lookup"><span data-stu-id="5e667-234">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modify-arrays"></a><span data-ttu-id="5e667-235">Modificar matrizes</span><span class="sxs-lookup"><span data-stu-id="5e667-235">Modify arrays</span></span>

<span data-ttu-id="5e667-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) define um elemento para um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="5e667-236">[`Array.set`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#set) sets an element to a specified value.</span></span> <span data-ttu-id="5e667-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) define um intervalo de elementos em uma matriz para um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="5e667-237">[`Array.fill`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#fill) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="5e667-238">O código a seguir fornece um exemplo de `Array.fill` .</span><span class="sxs-lookup"><span data-stu-id="5e667-238">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="5e667-239">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="5e667-239">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="5e667-240">Você pode usar [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) para copiar uma subseção de uma matriz para outra matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-240">You can use [`Array.blit`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#blit) to copy a subsection of one array to another array.</span></span>

### <a name="convert-to-and-from-other-types"></a><span data-ttu-id="5e667-241">Converter de e para outros tipos</span><span class="sxs-lookup"><span data-stu-id="5e667-241">Convert to and from other types</span></span>

<span data-ttu-id="5e667-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) Cria uma matriz de uma lista.</span><span class="sxs-lookup"><span data-stu-id="5e667-242">[`Array.ofList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofList) creates an array from a list.</span></span> <span data-ttu-id="5e667-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) Cria uma matriz de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="5e667-243">[`Array.ofSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#ofSeq) creates an array from a sequence.</span></span> <span data-ttu-id="5e667-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) e [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) converter para esses outros tipos de coleção do tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-244">[`Array.toList`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toList) and [`Array.toSeq`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#toSeq) convert to these other collection types from the array type.</span></span>

### <a name="sort-arrays"></a><span data-ttu-id="5e667-245">Classificar matrizes</span><span class="sxs-lookup"><span data-stu-id="5e667-245">Sort arrays</span></span>

<span data-ttu-id="5e667-246">Use [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) para classificar uma matriz usando a função de comparação genérica.</span><span class="sxs-lookup"><span data-stu-id="5e667-246">Use [`Array.sort`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sort) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="5e667-247">Use [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) para especificar uma função que gera um valor, chamado de *chave*, para classificar usando a função de comparação genérica na chave.</span><span class="sxs-lookup"><span data-stu-id="5e667-247">Use [`Array.sortBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortBy) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="5e667-248">Use [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) se você quiser fornecer uma função de comparação personalizada.</span><span class="sxs-lookup"><span data-stu-id="5e667-248">Use [`Array.sortWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortWith) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="5e667-249">`Array.sort`, `Array.sortBy` e `Array.sortWith` todos retornam a matriz classificada como uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="5e667-249">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="5e667-250">As variações [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace) , [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy) e [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modificam a matriz existente em vez de retornar uma nova.</span><span class="sxs-lookup"><span data-stu-id="5e667-250">The variations [`Array.sortInPlace`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlace), [`Array.sortInPlaceBy`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceBy), and [`Array.sortInPlaceWith`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#sortInPlaceWith) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="5e667-251">Matrizes e tuplas</span><span class="sxs-lookup"><span data-stu-id="5e667-251">Arrays and tuples</span></span>

<span data-ttu-id="5e667-252">As funções [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) e [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convertem matrizes de pares de tupla para tuplas de matrizes e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="5e667-252">The functions [`Array.zip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip) and [`Array.unzip`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="5e667-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) e [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) são semelhantes, exceto que funcionam com tuplas de três elementos ou tuplas de três matrizes.</span><span class="sxs-lookup"><span data-stu-id="5e667-253">[`Array.zip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#zip3) and [`Array.unzip3`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule.html#unzip3) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="5e667-254">Cálculos paralelos em matrizes</span><span class="sxs-lookup"><span data-stu-id="5e667-254">Parallel computations on arrays</span></span>

<span data-ttu-id="5e667-255">O módulo [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contém funções para executar cálculos paralelos em matrizes.</span><span class="sxs-lookup"><span data-stu-id="5e667-255">The module [`Array.Parallel`](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-collections-arraymodule-parallel.html) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="5e667-256">Este módulo não está disponível em aplicativos que visam versões do .NET Framework antes da versão 4.</span><span class="sxs-lookup"><span data-stu-id="5e667-256">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="5e667-257">Veja também</span><span class="sxs-lookup"><span data-stu-id="5e667-257">See also</span></span>

- [<span data-ttu-id="5e667-258">Referência de linguagem F #</span><span class="sxs-lookup"><span data-stu-id="5e667-258">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="5e667-259">Tipos F#</span><span class="sxs-lookup"><span data-stu-id="5e667-259">F# Types</span></span>](fsharp-types.md)
