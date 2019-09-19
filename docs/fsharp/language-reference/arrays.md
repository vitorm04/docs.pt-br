---
title: Matrizes
description: Saiba como criar e usar matrizes na linguagem F# de programação.
ms.date: 05/16/2016
ms.openlocfilehash: ae8f3cfc84fbba4cac496d4221d140dadec25e10
ms.sourcegitcommit: a2d0e1f66367367065bc8dc0dde488ab536da73f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/18/2019
ms.locfileid: "71082961"
---
# <a name="arrays"></a><span data-ttu-id="c4f56-103">Matrizes</span><span class="sxs-lookup"><span data-stu-id="c4f56-103">Arrays</span></span>

> [!NOTE]
> <span data-ttu-id="c4f56-104">O link de referência da API levará você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="c4f56-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="c4f56-105">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="c4f56-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="c4f56-106">As matrizes são coleções de tamanho fixo, com base em zero e mutáveis de elementos de dados consecutivos que são do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="c4f56-106">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="c4f56-107">Criando matrizes</span><span class="sxs-lookup"><span data-stu-id="c4f56-107">Creating Arrays</span></span>

<span data-ttu-id="c4f56-108">Você pode criar matrizes de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="c4f56-108">You can create arrays in several ways.</span></span> <span data-ttu-id="c4f56-109">Você pode criar uma pequena matriz listando valores consecutivos `[|` entre `|]` e e separados por ponto e vírgula, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4f56-109">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="c4f56-110">Você também pode colocar cada elemento em uma linha separada; nesse caso, o separador de ponto-e-vírgula é opcional.</span><span class="sxs-lookup"><span data-stu-id="c4f56-110">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="c4f56-111">O tipo dos elementos da matriz é inferido a partir dos literais usados e deve ser consistente.</span><span class="sxs-lookup"><span data-stu-id="c4f56-111">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="c4f56-112">O código a seguir causa um erro porque 1,0 é um float e 2 e 3 são inteiros.</span><span class="sxs-lookup"><span data-stu-id="c4f56-112">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="c4f56-113">Você também pode usar expressões de sequência para criar matrizes.</span><span class="sxs-lookup"><span data-stu-id="c4f56-113">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="c4f56-114">Veja a seguir um exemplo que cria uma matriz de quadrados de inteiros de 1 a 10.</span><span class="sxs-lookup"><span data-stu-id="c4f56-114">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="c4f56-115">Para criar uma matriz na qual todos os elementos são inicializados como zero, `Array.zeroCreate`use.</span><span class="sxs-lookup"><span data-stu-id="c4f56-115">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a><span data-ttu-id="c4f56-116">Acessando elementos</span><span class="sxs-lookup"><span data-stu-id="c4f56-116">Accessing Elements</span></span>

<span data-ttu-id="c4f56-117">Você pode acessar elementos de matriz usando um operador de ponto`.`() e colchetes`[` ( `]`e).</span><span class="sxs-lookup"><span data-stu-id="c4f56-117">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="c4f56-118">Os índices de matriz começam em 0.</span><span class="sxs-lookup"><span data-stu-id="c4f56-118">Array indexes start at 0.</span></span>

<span data-ttu-id="c4f56-119">Você também pode acessar elementos de matriz usando a notação de fatia, que permite especificar um subintervalo da matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-119">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="c4f56-120">Seguem exemplos de notação de fatia.</span><span class="sxs-lookup"><span data-stu-id="c4f56-120">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="c4f56-121">Quando a notação de fatia é usada, uma nova cópia da matriz é criada.</span><span class="sxs-lookup"><span data-stu-id="c4f56-121">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="c4f56-122">Módulos e tipos de matriz</span><span class="sxs-lookup"><span data-stu-id="c4f56-122">Array Types and Modules</span></span>

<span data-ttu-id="c4f56-123">O tipo de todas F# as matrizes é o <xref:System.Array?displayProperty=nameWithType>tipo de .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c4f56-123">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="c4f56-124">Portanto, F# as matrizes oferecem suporte a todas <xref:System.Array?displayProperty=nameWithType>as funcionalidades disponíveis no.</span><span class="sxs-lookup"><span data-stu-id="c4f56-124">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="c4f56-125">O módulo [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) de biblioteca dá suporte a operações em matrizes unidimensionais.</span><span class="sxs-lookup"><span data-stu-id="c4f56-125">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="c4f56-126">Os módulos `Array2D`, `Array3D`e `Array4D` contêm funções que dão suporte a operações em matrizes de duas, três e quatro dimensões, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c4f56-126">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="c4f56-127">Você pode criar matrizes de classificação maior que quatro usando <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="c4f56-127">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="c4f56-128">Funções simples</span><span class="sxs-lookup"><span data-stu-id="c4f56-128">Simple Functions</span></span>

<span data-ttu-id="c4f56-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc)Obtém um elemento.</span><span class="sxs-lookup"><span data-stu-id="c4f56-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="c4f56-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f)fornece o comprimento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="c4f56-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)define um elemento para um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="c4f56-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="c4f56-132">O exemplo de código a seguir ilustra o uso dessas funções.</span><span class="sxs-lookup"><span data-stu-id="c4f56-132">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="c4f56-133">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-133">The output is as follows.</span></span>

```console
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="c4f56-134">Funções que criam matrizes</span><span class="sxs-lookup"><span data-stu-id="c4f56-134">Functions That Create Arrays</span></span>

<span data-ttu-id="c4f56-135">Várias funções criam matrizes sem a necessidade de uma matriz existente.</span><span class="sxs-lookup"><span data-stu-id="c4f56-135">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="c4f56-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32)Cria uma nova matriz que não contém nenhum elemento.</span><span class="sxs-lookup"><span data-stu-id="c4f56-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="c4f56-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be)Cria uma matriz de um tamanho especificado e define todos os elementos para os valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="c4f56-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="c4f56-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665)Cria uma matriz, dada uma dimensão e uma função para gerar os elementos.</span><span class="sxs-lookup"><span data-stu-id="c4f56-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="c4f56-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2)Cria uma matriz na qual todos os elementos são inicializados com o valor zero para o tipo da matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="c4f56-140">O código a seguir demonstra essas funções.</span><span class="sxs-lookup"><span data-stu-id="c4f56-140">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="c4f56-141">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-141">The output is as follows.</span></span>

```console
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="c4f56-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f)Cria uma nova matriz que contém elementos que são copiados de uma matriz existente.</span><span class="sxs-lookup"><span data-stu-id="c4f56-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="c4f56-143">Observe que a cópia é uma cópia superficial, o que significa que se o tipo de elemento for um tipo de referência, somente a referência será copiada, não o objeto subjacente.</span><span class="sxs-lookup"><span data-stu-id="c4f56-143">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="c4f56-144">O exemplo de código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="c4f56-144">The following code example illustrates this.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="c4f56-145">A saída do código anterior é a seguinte:</span><span class="sxs-lookup"><span data-stu-id="c4f56-145">The output of the preceding code is as follows:</span></span>

```console
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="c4f56-146">A cadeia `Test1` de caracteres aparece apenas na primeira matriz porque a operação de criação de um novo elemento substitui a referência em `firstArray` , mas não afeta a referência original a uma cadeia de caracteres vazia que ainda está `secondArray`presente no.</span><span class="sxs-lookup"><span data-stu-id="c4f56-146">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="c4f56-147">A cadeia `Test2` de caracteres aparece em ambas as `Insert` matrizes porque <xref:System.Text.StringBuilder?displayProperty=nameWithType> a operação no tipo <xref:System.Text.StringBuilder?displayProperty=nameWithType> afeta o objeto subjacente, que é referenciado em ambas as matrizes.</span><span class="sxs-lookup"><span data-stu-id="c4f56-147">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="c4f56-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d)gera uma nova matriz de um subintervalo de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="c4f56-149">Você especifica o subintervalo fornecendo o índice inicial e o comprimento.</span><span class="sxs-lookup"><span data-stu-id="c4f56-149">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="c4f56-150">O código a seguir demonstra o uso de `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="c4f56-150">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="c4f56-151">A saída mostra que a submatriz começa no elemento 5 e contém 10 elementos.</span><span class="sxs-lookup"><span data-stu-id="c4f56-151">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```console
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```

<span data-ttu-id="c4f56-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911)Cria uma nova matriz combinando duas matrizes existentes.</span><span class="sxs-lookup"><span data-stu-id="c4f56-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="c4f56-153">O código a seguir demonstra o **array. Append**.</span><span class="sxs-lookup"><span data-stu-id="c4f56-153">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="c4f56-154">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-154">The output of the preceding code is as follows.</span></span>

```console
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="c4f56-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09)seleciona os elementos de uma matriz para incluir em uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="c4f56-156">O código a seguir `Array.choose`demonstra.</span><span class="sxs-lookup"><span data-stu-id="c4f56-156">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="c4f56-157">Observe que o tipo de elemento da matriz não precisa corresponder ao tipo de valor retornado no tipo de opção.</span><span class="sxs-lookup"><span data-stu-id="c4f56-157">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="c4f56-158">Neste exemplo, o tipo de elemento é `int` e a opção é o resultado de uma função polinomial `elem*elem - 1`,, como um número de ponto flutuante.</span><span class="sxs-lookup"><span data-stu-id="c4f56-158">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="c4f56-159">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-159">The output of the preceding code is as follows.</span></span>

```console
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="c4f56-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a)executa uma função especificada em cada elemento da matriz de uma matriz existente e, em seguida, coleta os elementos gerados pela função e os combina em uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="c4f56-161">O código a seguir `Array.collect`demonstra.</span><span class="sxs-lookup"><span data-stu-id="c4f56-161">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="c4f56-162">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-162">The output of the preceding code is as follows.</span></span>

```console
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="c4f56-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302)usa uma sequência de matrizes e as combina em uma única matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="c4f56-164">O código a seguir `Array.concat`demonstra.</span><span class="sxs-lookup"><span data-stu-id="c4f56-164">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="c4f56-165">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-165">The output of the preceding code is as follows.</span></span>

```console
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="c4f56-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede)usa uma função de condição booliana e gera uma nova matriz que contém somente os elementos da matriz de entrada para a qual a condição é verdadeira.</span><span class="sxs-lookup"><span data-stu-id="c4f56-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="c4f56-167">O código a seguir `Array.filter`demonstra.</span><span class="sxs-lookup"><span data-stu-id="c4f56-167">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="c4f56-168">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-168">The output of the preceding code is as follows.</span></span>

```console
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="c4f56-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709)gera uma nova matriz revertendo a ordem de uma matriz existente.</span><span class="sxs-lookup"><span data-stu-id="c4f56-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="c4f56-170">O código a seguir `Array.rev`demonstra.</span><span class="sxs-lookup"><span data-stu-id="c4f56-170">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet18.fs)]

<span data-ttu-id="c4f56-171">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-171">The output of the preceding code is as follows.</span></span>

```console
"Hello world!"
```

<span data-ttu-id="c4f56-172">Você pode combinar facilmente funções no módulo de matriz que transformam matrizes usando o operador`|>`de pipeline (), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4f56-172">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="c4f56-173">A saída é</span><span class="sxs-lookup"><span data-stu-id="c4f56-173">The output is</span></span>

```console
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="c4f56-174">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="c4f56-174">Multidimensional Arrays</span></span>

<span data-ttu-id="c4f56-175">Uma matriz multidimensional pode ser criada, mas não há nenhuma sintaxe para gravar um literal de matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="c4f56-175">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="c4f56-176">Use o operador [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) para criar uma matriz de uma sequência de sequências de elementos de matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-176">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="c4f56-177">As sequências podem ser literais de matriz ou lista.</span><span class="sxs-lookup"><span data-stu-id="c4f56-177">The sequences can be array or list literals.</span></span> <span data-ttu-id="c4f56-178">Por exemplo, o código a seguir cria uma matriz bidimensional.</span><span class="sxs-lookup"><span data-stu-id="c4f56-178">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="c4f56-179">Você também pode usar a função [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) para inicializar matrizes de duas dimensões e funções semelhantes estão disponíveis para matrizes de três e quatro dimensões.</span><span class="sxs-lookup"><span data-stu-id="c4f56-179">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="c4f56-180">Essas funções usam uma função que é usada para criar os elementos.</span><span class="sxs-lookup"><span data-stu-id="c4f56-180">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="c4f56-181">Para criar uma matriz bidimensional que contém elementos definidos como um valor inicial em vez de especificar uma função, use [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) a função, que também está disponível para matrizes de até quatro dimensões.</span><span class="sxs-lookup"><span data-stu-id="c4f56-181">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="c4f56-182">O exemplo de código a seguir mostra primeiro como criar uma matriz de matrizes que contêm os elementos desejados `Array2D.init` e, em seguida, usa para gerar a matriz bidimensional desejada.</span><span class="sxs-lookup"><span data-stu-id="c4f56-182">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="c4f56-183">A indexação de matriz e a sintaxe de divisão têm suporte para matrizes até a classificação 4.</span><span class="sxs-lookup"><span data-stu-id="c4f56-183">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="c4f56-184">Quando você especifica um índice em várias dimensões, usa vírgulas para separar os índices, conforme ilustrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="c4f56-184">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="c4f56-185">O tipo de uma matriz bidimensional é `<type>[,]` escrito como (por exemplo `double[,]`, `int[,]`), e o tipo de uma matriz tridimensional é escrito como `<type>[,,]`e assim por diante para matrizes de dimensões superiores.</span><span class="sxs-lookup"><span data-stu-id="c4f56-185">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="c4f56-186">Somente um subconjunto das funções disponíveis para matrizes unidimensionais também está disponível para matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="c4f56-186">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="c4f56-187">Para obter mais informações, [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d)consulte [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d) [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d),, e [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="c4f56-187">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="c4f56-188">Fatias de matrizes e matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="c4f56-188">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="c4f56-189">Em uma matriz bidimensional (uma matriz), você pode extrair uma submatriz especificando intervalos e usando um caractere curinga (`*`) para especificar linhas ou colunas inteiras.</span><span class="sxs-lookup"><span data-stu-id="c4f56-189">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

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

<span data-ttu-id="c4f56-190">A partir F# de 3,1, você pode decompor uma matriz multidimensional em subconjuntos da mesma dimensão ou menor.</span><span class="sxs-lookup"><span data-stu-id="c4f56-190">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="c4f56-191">Por exemplo, você pode obter um vetor de uma matriz especificando uma única linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="c4f56-191">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="c4f56-192">Você pode usar essa sintaxe de divisão para tipos que implementam os operadores de acesso do elemento e `GetSlice` os métodos sobrecarregados.</span><span class="sxs-lookup"><span data-stu-id="c4f56-192">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="c4f56-193">Por exemplo, o código a seguir cria um tipo de matriz que encapsula F# a matriz 2D, implementa uma propriedade item para fornecer suporte para indexação de matriz e implementa três versões `GetSlice`do.</span><span class="sxs-lookup"><span data-stu-id="c4f56-193">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="c4f56-194">Se você puder usar esse código como um modelo para os tipos de matriz, poderá usar todas as operações de divisão que esta seção descreve.</span><span class="sxs-lookup"><span data-stu-id="c4f56-194">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

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

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="c4f56-195">Funções booleanas em matrizes</span><span class="sxs-lookup"><span data-stu-id="c4f56-195">Boolean Functions on Arrays</span></span>

<span data-ttu-id="c4f56-196">As funções [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) e [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) os elementos de teste em uma ou duas matrizes, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="c4f56-196">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="c4f56-197">Essas funções usam uma função de teste e `true` retornam se há um elemento (ou par de `Array.exists2`elementos para) que satisfaça a condição.</span><span class="sxs-lookup"><span data-stu-id="c4f56-197">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="c4f56-198">O código a seguir demonstra o uso `Array.exists` de `Array.exists2`e.</span><span class="sxs-lookup"><span data-stu-id="c4f56-198">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="c4f56-199">Nesses exemplos, novas funções são criadas aplicando-se apenas um dos argumentos, nesses casos, o argumento da função.</span><span class="sxs-lookup"><span data-stu-id="c4f56-199">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="c4f56-200">A saída do código anterior é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-200">The output of the preceding code is as follows.</span></span>

```console
true
false
false
true
```

<span data-ttu-id="c4f56-201">Da mesma forma, [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) a função testa uma matriz para determinar se cada elemento atende a uma condição booliana.</span><span class="sxs-lookup"><span data-stu-id="c4f56-201">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="c4f56-202">A variação [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) faz a mesma coisa usando uma função booleana que envolve elementos de duas matrizes de comprimento igual.</span><span class="sxs-lookup"><span data-stu-id="c4f56-202">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="c4f56-203">O código a seguir ilustra o uso dessas funções.</span><span class="sxs-lookup"><span data-stu-id="c4f56-203">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="c4f56-204">A saída desses exemplos é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-204">The output for these examples is as follows.</span></span>

```console
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="c4f56-205">Pesquisando matrizes</span><span class="sxs-lookup"><span data-stu-id="c4f56-205">Searching Arrays</span></span>

<span data-ttu-id="c4f56-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33)usa uma função booliana e retorna o primeiro elemento para o qual a `true`função retorna, ou <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> gera um elemento If nenhum que satisfaça a condição é encontrado.</span><span class="sxs-lookup"><span data-stu-id="c4f56-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="c4f56-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f)é como `Array.find`, exceto pelo fato de que ele retorna o índice do elemento em vez do próprio elemento.</span><span class="sxs-lookup"><span data-stu-id="c4f56-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="c4f56-208">O código a seguir `Array.find` usa `Array.findIndex` e para localizar um número que seja um cubo perfeito e um quadrado perfeitos.</span><span class="sxs-lookup"><span data-stu-id="c4f56-208">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="c4f56-209">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-209">The output is as follows.</span></span>

```console
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="c4f56-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9)é como `Array.find`, exceto que seu resultado é um tipo de opção e retorna `None` se nenhum elemento for encontrado.</span><span class="sxs-lookup"><span data-stu-id="c4f56-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="c4f56-211">`Array.tryFind`deve ser usado em vez `Array.find` de quando você não sabe se um elemento correspondente está na matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-211">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="c4f56-212">Da mesma [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) forma, [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) é como, exceto que o tipo de opção é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="c4f56-212">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="c4f56-213">Se nenhum elemento for encontrado, a opção será `None`.</span><span class="sxs-lookup"><span data-stu-id="c4f56-213">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="c4f56-214">O código a seguir demonstra o uso de `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="c4f56-214">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="c4f56-215">Esse código depende do código anterior.</span><span class="sxs-lookup"><span data-stu-id="c4f56-215">This code depends on the previous code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="c4f56-216">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-216">The output is as follows.</span></span>

```console
Found an element: 1
Found an element: 729
```

<span data-ttu-id="c4f56-217">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) quando precisar transformar um elemento, além de localizá-lo.</span><span class="sxs-lookup"><span data-stu-id="c4f56-217">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="c4f56-218">O resultado é o primeiro elemento para o qual a função retorna o elemento transformado como um valor `None` de opção ou se nenhum elemento desse tipo é encontrado.</span><span class="sxs-lookup"><span data-stu-id="c4f56-218">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="c4f56-219">O código a seguir demonstra o uso de `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="c4f56-219">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="c4f56-220">Nesse caso, em vez de uma expressão lambda, várias funções auxiliares locais são definidas para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="c4f56-220">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="c4f56-221">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-221">The output is as follows.</span></span>

```console
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="c4f56-222">Executando cálculos em matrizes</span><span class="sxs-lookup"><span data-stu-id="c4f56-222">Performing Computations on Arrays</span></span>

<span data-ttu-id="c4f56-223">A [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) função retorna a média de cada elemento em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-223">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="c4f56-224">Ele é limitado a tipos de elementos que dão suporte à divisão exata por um inteiro, que inclui tipos de ponto flutuante, mas não tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="c4f56-224">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="c4f56-225">A [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) função retorna a média dos resultados da chamada de uma função em cada elemento.</span><span class="sxs-lookup"><span data-stu-id="c4f56-225">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="c4f56-226">Para uma matriz de tipo integral, você pode usar `Array.averageBy` e fazer com que a função Converta cada elemento em um tipo de ponto flutuante para a computação.</span><span class="sxs-lookup"><span data-stu-id="c4f56-226">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="c4f56-227">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) [ou`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) para obter o elemento máximo ou mínimo, se o tipo de elemento oferecer suporte a ele.</span><span class="sxs-lookup"><span data-stu-id="c4f56-227">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="c4f56-228">Da mesma [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) forma [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) , e permite que uma função seja executada primeiro, talvez para transformar em um tipo que dê suporte à comparação.</span><span class="sxs-lookup"><span data-stu-id="c4f56-228">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="c4f56-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2)Adiciona os elementos de uma matriz e [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) chama uma função em cada elemento e adiciona os resultados juntos.</span><span class="sxs-lookup"><span data-stu-id="c4f56-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="c4f56-230">Para executar uma função em cada elemento em uma matriz sem armazenar os valores de retorno, [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516)use.</span><span class="sxs-lookup"><span data-stu-id="c4f56-230">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="c4f56-231">Para uma função que envolva duas matrizes de comprimento igual [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc), use.</span><span class="sxs-lookup"><span data-stu-id="c4f56-231">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="c4f56-232">Se você também precisar manter uma matriz dos resultados da função, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) ou [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), que opera em duas matrizes por vez.</span><span class="sxs-lookup"><span data-stu-id="c4f56-232">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="c4f56-233">As variações [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) e [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) permitem que o índice do elemento esteja envolvido na computação; o mesmo é verdadeiro para [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) e [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span><span class="sxs-lookup"><span data-stu-id="c4f56-233">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="c4f56-234">As funções [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9) [,e`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) executam algoritmos que envolvem todos os elementos de uma matriz. [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0)</span><span class="sxs-lookup"><span data-stu-id="c4f56-234">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="c4f56-235">Da mesma forma, [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) as [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) variações e executam cálculos em duas matrizes.</span><span class="sxs-lookup"><span data-stu-id="c4f56-235">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="c4f56-236">Essas funções para executar computações correspondem às funções de mesmo nome no módulo de [lista](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="c4f56-236">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="c4f56-237">Para obter exemplos de uso, consulte [listas](lists.md).</span><span class="sxs-lookup"><span data-stu-id="c4f56-237">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="c4f56-238">Modificando matrizes</span><span class="sxs-lookup"><span data-stu-id="c4f56-238">Modifying Arrays</span></span>

<span data-ttu-id="c4f56-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790)define um elemento para um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="c4f56-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="c4f56-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2)define um intervalo de elementos em uma matriz para um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="c4f56-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="c4f56-241">O código a seguir fornece um exemplo `Array.fill`de.</span><span class="sxs-lookup"><span data-stu-id="c4f56-241">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](~/samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="c4f56-242">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="c4f56-242">The output is as follows.</span></span>

```console
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="c4f56-243">Você pode usar [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) para copiar uma subseção de uma matriz para outra matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-243">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="c4f56-244">Convertendo de e para outros tipos</span><span class="sxs-lookup"><span data-stu-id="c4f56-244">Converting to and from Other Types</span></span>

<span data-ttu-id="c4f56-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b)Cria uma matriz de uma lista.</span><span class="sxs-lookup"><span data-stu-id="c4f56-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="c4f56-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c)Cria uma matriz de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="c4f56-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="c4f56-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786)e [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) converter para esses outros tipos de coleção do tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="c4f56-248">Classificando matrizes</span><span class="sxs-lookup"><span data-stu-id="c4f56-248">Sorting Arrays</span></span>

<span data-ttu-id="c4f56-249">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) para classificar uma matriz usando a função de comparação genérica.</span><span class="sxs-lookup"><span data-stu-id="c4f56-249">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="c4f56-250">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) para especificar uma função que gera um valor, chamado de *chave*, para classificar usando a função de comparação genérica na chave.</span><span class="sxs-lookup"><span data-stu-id="c4f56-250">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="c4f56-251">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) se você quiser fornecer uma função de comparação personalizada.</span><span class="sxs-lookup"><span data-stu-id="c4f56-251">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="c4f56-252">`Array.sort`, `Array.sortBy` e`Array.sortWith` todos retornam a matriz classificada como uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="c4f56-252">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="c4f56-253">As variações [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f)e [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modificam a matriz existente em vez de retornar uma nova.</span><span class="sxs-lookup"><span data-stu-id="c4f56-253">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="c4f56-254">Matrizes e tuplas</span><span class="sxs-lookup"><span data-stu-id="c4f56-254">Arrays and Tuples</span></span>

<span data-ttu-id="c4f56-255">As funções [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) e [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convertem matrizes de pares de tupla para tuplas de matrizes e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="c4f56-255">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="c4f56-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d)e [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) são semelhantes, exceto que funcionam com tuplas de três elementos ou tuplas de três matrizes.</span><span class="sxs-lookup"><span data-stu-id="c4f56-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="c4f56-257">Cálculos paralelos em matrizes</span><span class="sxs-lookup"><span data-stu-id="c4f56-257">Parallel Computations on Arrays</span></span>

<span data-ttu-id="c4f56-258">O módulo [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contém funções para executar cálculos paralelos em matrizes.</span><span class="sxs-lookup"><span data-stu-id="c4f56-258">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="c4f56-259">Este módulo não está disponível em aplicativos que visam versões do .NET Framework antes da versão 4.</span><span class="sxs-lookup"><span data-stu-id="c4f56-259">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="c4f56-260">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c4f56-260">See also</span></span>

- [<span data-ttu-id="c4f56-261">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="c4f56-261">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="c4f56-262">Tipos F#</span><span class="sxs-lookup"><span data-stu-id="c4f56-262">F# Types</span></span>](fsharp-types.md)
