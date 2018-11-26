---
title: Matrizes (F#)
description: Saiba como criar e usar matrizes no F# linguagem de programação.
ms.date: 05/16/2016
ms.openlocfilehash: 0f72718988ee401631c53b74f02948030e83aac1
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297186"
---
# <a name="arrays"></a><span data-ttu-id="8137b-103">Matrizes</span><span class="sxs-lookup"><span data-stu-id="8137b-103">Arrays</span></span>

> [!NOTE]
> <span data-ttu-id="8137b-104">O link de referência da API levará você até o MSDN.</span><span class="sxs-lookup"><span data-stu-id="8137b-104">The API reference link will take you to MSDN.</span></span>  <span data-ttu-id="8137b-105">A referência da API docs.microsoft.com não está completa.</span><span class="sxs-lookup"><span data-stu-id="8137b-105">The docs.microsoft.com API reference is not complete.</span></span>

<span data-ttu-id="8137b-106">Matrizes são coleções de tamanho fixo, com base em zero, mutáveis de elementos de dados consecutivos que são todos do mesmo tipo.</span><span class="sxs-lookup"><span data-stu-id="8137b-106">Arrays are fixed-size, zero-based, mutable collections of consecutive data elements that are all of the same type.</span></span>

## <a name="creating-arrays"></a><span data-ttu-id="8137b-107">Criando matrizes</span><span class="sxs-lookup"><span data-stu-id="8137b-107">Creating Arrays</span></span>

<span data-ttu-id="8137b-108">Você pode criar matrizes de várias maneiras.</span><span class="sxs-lookup"><span data-stu-id="8137b-108">You can create arrays in several ways.</span></span> <span data-ttu-id="8137b-109">Você pode criar uma matriz pequena listando valores consecutivos entre `[|` e `|]` e separados por ponto e vírgula, conforme mostrado nos exemplos a seguir.</span><span class="sxs-lookup"><span data-stu-id="8137b-109">You can create a small array by listing consecutive values between `[|` and `|]` and separated by semicolons, as shown in the following examples.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet1.fs)]

<span data-ttu-id="8137b-110">Você também pode colocar cada elemento em uma linha separada, nesse caso o separador de ponto e vírgula é opcional.</span><span class="sxs-lookup"><span data-stu-id="8137b-110">You can also put each element on a separate line, in which case the semicolon separator is optional.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet2.fs)]

<span data-ttu-id="8137b-111">O tipo dos elementos da matriz é inferido dos literais usados e deve ser consistente.</span><span class="sxs-lookup"><span data-stu-id="8137b-111">The type of the array elements is inferred from the literals used and must be consistent.</span></span> <span data-ttu-id="8137b-112">O código a seguir causa um erro porque 1,0 é um float e 2 e 3 são números inteiros.</span><span class="sxs-lookup"><span data-stu-id="8137b-112">The following code causes an error because 1.0 is a float and 2 and 3 are integers.</span></span>

```fsharp
// Causes an error.
// let array2 = [| 1.0; 2; 3 |]
```

<span data-ttu-id="8137b-113">Você também pode usar expressões de sequência para criar matrizes.</span><span class="sxs-lookup"><span data-stu-id="8137b-113">You can also use sequence expressions to create arrays.</span></span> <span data-ttu-id="8137b-114">A seguir está um exemplo que cria uma matriz de quadrados de inteiros de 1 a 10.</span><span class="sxs-lookup"><span data-stu-id="8137b-114">Following is an example that creates an array of squares of integers from 1 to 10.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet3.fs)]

<span data-ttu-id="8137b-115">Para criar uma matriz em que todos os elementos são inicializados a zero, use `Array.zeroCreate`.</span><span class="sxs-lookup"><span data-stu-id="8137b-115">To create an array in which all the elements are initialized to zero, use `Array.zeroCreate`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet4.fs)]

## <a name="accessing-elements"></a><span data-ttu-id="8137b-116">Acessando elementos</span><span class="sxs-lookup"><span data-stu-id="8137b-116">Accessing Elements</span></span>

<span data-ttu-id="8137b-117">Você pode acessar elementos da matriz usando um operador ponto (`.`) e colchetes (`[` e `]`).</span><span class="sxs-lookup"><span data-stu-id="8137b-117">You can access array elements by using a dot operator (`.`) and brackets (`[` and `]`).</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet5.fs)]

<span data-ttu-id="8137b-118">Índices de matriz iniciam em 0.</span><span class="sxs-lookup"><span data-stu-id="8137b-118">Array indexes start at 0.</span></span>

<span data-ttu-id="8137b-119">Você também pode acessar elementos da matriz, usando a notação de fatia, que permite que você especifique uma subclassificação da matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-119">You can also access array elements by using slice notation, which enables you to specify a subrange of the array.</span></span> <span data-ttu-id="8137b-120">Seguem exemplos de notação de fatia.</span><span class="sxs-lookup"><span data-stu-id="8137b-120">Examples of slice notation follow.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet51.fs)]

<span data-ttu-id="8137b-121">Quando a notação de fatia é usada, uma nova cópia da matriz é criada.</span><span class="sxs-lookup"><span data-stu-id="8137b-121">When slice notation is used, a new copy of the array is created.</span></span>

## <a name="array-types-and-modules"></a><span data-ttu-id="8137b-122">Módulos e tipos de matriz</span><span class="sxs-lookup"><span data-stu-id="8137b-122">Array Types and Modules</span></span>

<span data-ttu-id="8137b-123">O tipo de todos os F# matrizes é o tipo do .NET Framework <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8137b-123">The type of all F# arrays is the .NET Framework type <xref:System.Array?displayProperty=nameWithType>.</span></span> <span data-ttu-id="8137b-124">Portanto, F# toda a funcionalidade disponível no suportam a matrizes <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8137b-124">Therefore, F# arrays support all the functionality available in <xref:System.Array?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="8137b-125">O módulo de biblioteca [ `Microsoft.FSharp.Collections.Array` ](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) dá suporte a operações em matrizes unidimensionais.</span><span class="sxs-lookup"><span data-stu-id="8137b-125">The library module [`Microsoft.FSharp.Collections.Array`](https://msdn.microsoft.com/library/0cda8040-9396-40dd-8dcd-cf48542165a1) supports operations on one-dimensional arrays.</span></span> <span data-ttu-id="8137b-126">Os módulos `Array2D`, `Array3D`, e `Array4D` contêm funções que dão suporte a operações em matrizes de duas, três e quatro dimensões, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8137b-126">The modules `Array2D`, `Array3D`, and `Array4D` contain functions that support operations on arrays of two, three, and four dimensions, respectively.</span></span> <span data-ttu-id="8137b-127">Você pode criar matrizes de classificação maior do que quatro usando <xref:System.Array?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="8137b-127">You can create arrays of rank greater than four by using <xref:System.Array?displayProperty=nameWithType>.</span></span>

### <a name="simple-functions"></a><span data-ttu-id="8137b-128">Funções simples</span><span class="sxs-lookup"><span data-stu-id="8137b-128">Simple Functions</span></span>

<span data-ttu-id="8137b-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) Obtém um elemento.</span><span class="sxs-lookup"><span data-stu-id="8137b-129">[`Array.get`](https://msdn.microsoft.com/library/dd93e85d-7e80-4d76-8de0-b6d45bcf07bc) gets an element.</span></span> <span data-ttu-id="8137b-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) Retorna o comprimento de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-130">[`Array.length`](https://msdn.microsoft.com/library/0d775b6a-4a8f-4bd1-83e5-843b3251725f) gives the length of an array.</span></span> <span data-ttu-id="8137b-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) define um elemento com um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="8137b-131">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="8137b-132">O exemplo de código a seguir ilustra o uso dessas funções.</span><span class="sxs-lookup"><span data-stu-id="8137b-132">The following code example illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet9.fs)]

<span data-ttu-id="8137b-133">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="8137b-133">The output is as follows.</span></span>

```
0 1 2 3 4 5 6 7 8 9
```

### <a name="functions-that-create-arrays"></a><span data-ttu-id="8137b-134">Funções que cria matrizes</span><span class="sxs-lookup"><span data-stu-id="8137b-134">Functions That Create Arrays</span></span>

<span data-ttu-id="8137b-135">Várias funções criam matrizes sem a necessidade de uma matriz existente.</span><span class="sxs-lookup"><span data-stu-id="8137b-135">Several functions create arrays without requiring an existing array.</span></span> <span data-ttu-id="8137b-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) cria uma nova matriz que não contém quaisquer elementos.</span><span class="sxs-lookup"><span data-stu-id="8137b-136">[`Array.empty`](https://msdn.microsoft.com/library/c3694b92-1c16-4c54-9bf2-fe398fadce32) creates a new array that does not contain any elements.</span></span> <span data-ttu-id="8137b-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) cria uma matriz de um tamanho especificado e define todos os elementos para valores fornecidos.</span><span class="sxs-lookup"><span data-stu-id="8137b-137">[`Array.create`](https://msdn.microsoft.com/library/e848c8d6-1142-4080-9727-8dacc26066be) creates an array of a specified size and sets all the elements to provided values.</span></span> <span data-ttu-id="8137b-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) cria uma matriz, dada uma dimensão e uma função para gerar os elementos.</span><span class="sxs-lookup"><span data-stu-id="8137b-138">[`Array.init`](https://msdn.microsoft.com/library/ee898089-63b0-40aa-910c-5ae7e32f6665) creates an array, given a dimension and a function to generate the elements.</span></span> <span data-ttu-id="8137b-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) cria uma matriz na qual todos os elementos são inicializados para o valor zero para o tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-139">[`Array.zeroCreate`](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2) creates an array in which all the elements are initialized to the zero value for the array's type.</span></span> <span data-ttu-id="8137b-140">O código a seguir demonstra essas funções.</span><span class="sxs-lookup"><span data-stu-id="8137b-140">The following code demonstrates these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet91.fs)]

<span data-ttu-id="8137b-141">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="8137b-141">The output is as follows.</span></span>

```
Length of empty array: 0
Area of floats set to 5.0: [|5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0; 5.0|]
Array of squares: [|0; 1; 4; 9; 16; 25; 36; 49; 64; 81|]
```

<span data-ttu-id="8137b-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) cria uma nova matriz que contém elementos copiados de uma matriz existente.</span><span class="sxs-lookup"><span data-stu-id="8137b-142">[`Array.copy`](https://msdn.microsoft.com/library/9d0202f1-1ea0-475e-9d66-4f8ccc3c5b5f) creates a new array that contains elements that are copied from an existing array.</span></span> <span data-ttu-id="8137b-143">Observe que a cópia é uma cópia superficial, o que significa que, se o tipo de elemento for um tipo de referência, somente a referência será copiada, não o objeto subjacente.</span><span class="sxs-lookup"><span data-stu-id="8137b-143">Note that the copy is a shallow copy, which means that if the element type is a reference type, only the reference is copied, not the underlying object.</span></span> <span data-ttu-id="8137b-144">O exemplo de código a seguir ilustra isso.</span><span class="sxs-lookup"><span data-stu-id="8137b-144">The following code example illustrates this.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet11.fs)]

<span data-ttu-id="8137b-145">A saída do código anterior é da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="8137b-145">The output of the preceding code is as follows:</span></span>

```
[|Test1; Test2; |]
[|; Test2; |]
```

<span data-ttu-id="8137b-146">A cadeia de caracteres `Test1` é exibido apenas na primeira matriz porque a operação de criação de um novo elemento substitui a referência na `firstArray` mas não afeta a referência original para uma cadeia de caracteres vazia que ainda está presente no `secondArray`.</span><span class="sxs-lookup"><span data-stu-id="8137b-146">The string `Test1` appears only in the first array because the operation of creating a new element overwrites the reference in `firstArray` but does not affect the original reference to an empty string that is still present in `secondArray`.</span></span> <span data-ttu-id="8137b-147">A cadeia de caracteres `Test2` aparece em ambas as matrizes porque o `Insert` operação na <xref:System.Text.StringBuilder?displayProperty=nameWithType> afeta o tipo subjacente <xref:System.Text.StringBuilder?displayProperty=nameWithType> objeto, que é referenciado em ambas as matrizes.</span><span class="sxs-lookup"><span data-stu-id="8137b-147">The string `Test2` appears in both arrays because the `Insert` operation on the <xref:System.Text.StringBuilder?displayProperty=nameWithType> type affects the underlying <xref:System.Text.StringBuilder?displayProperty=nameWithType> object, which is referenced in both arrays.</span></span>

<span data-ttu-id="8137b-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) gera uma nova matriz de um subintervalo de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-148">[`Array.sub`](https://msdn.microsoft.com/library/40fb12ba-41d7-4ef0-b33a-56727deeef9d) generates a new array from a subrange of an array.</span></span> <span data-ttu-id="8137b-149">Especifica a subclassificação fornecendo o índice inicial e o comprimento.</span><span class="sxs-lookup"><span data-stu-id="8137b-149">You specify the subrange by providing the starting index and the length.</span></span> <span data-ttu-id="8137b-150">O código a seguir demonstra o uso de `Array.sub`.</span><span class="sxs-lookup"><span data-stu-id="8137b-150">The following code demonstrates the use of `Array.sub`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet12.fs)]

<span data-ttu-id="8137b-151">A saída mostra que a submatriz começa no elemento 5 e contém 10 elementos.</span><span class="sxs-lookup"><span data-stu-id="8137b-151">The output shows that the subarray starts at element 5 and contains 10 elements.</span></span>

```
[|5; 6; 7; 8; 9; 10; 11; 12; 13; 14|]
```
<span data-ttu-id="8137b-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) cria uma nova matriz combinando duas matrizes existentes.</span><span class="sxs-lookup"><span data-stu-id="8137b-152">[`Array.append`](https://msdn.microsoft.com/library/08836310-5036-4474-b9a2-2c73e2293911) creates a new array by combining two existing arrays.</span></span>

<span data-ttu-id="8137b-153">O código a seguir demonstra **array. Append**.</span><span class="sxs-lookup"><span data-stu-id="8137b-153">The following code demonstrates **Array.append**.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet13.fs)]

<span data-ttu-id="8137b-154">A saída do código anterior é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8137b-154">The output of the preceding code is as follows.</span></span>

```
[|1; 2; 3; 4; 5; 6|]
```

<span data-ttu-id="8137b-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) Seleciona os elementos de uma matriz para incluir em uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-155">[`Array.choose`](https://msdn.microsoft.com/library/f5c8a5e2-637f-44d4-b35c-be96a6618b09) selects elements of an array to include in a new array.</span></span> <span data-ttu-id="8137b-156">O código a seguir demonstra `Array.choose`.</span><span class="sxs-lookup"><span data-stu-id="8137b-156">The following code demonstrates `Array.choose`.</span></span> <span data-ttu-id="8137b-157">Observe que o tipo de elemento da matriz não precisa corresponder ao tipo do valor retornado no tipo de opção.</span><span class="sxs-lookup"><span data-stu-id="8137b-157">Note that the element type of the array does not have to match the type of the value returned in the option type.</span></span> <span data-ttu-id="8137b-158">Neste exemplo, o tipo de elemento é `int` e a opção é o resultado de uma função polinomial, `elem*elem - 1`, como flutuante número de ponto.</span><span class="sxs-lookup"><span data-stu-id="8137b-158">In this example, the element type is `int` and the option is the result of a polynomial function, `elem*elem - 1`, as a floating point number.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet14.fs)]

<span data-ttu-id="8137b-159">A saída do código anterior é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8137b-159">The output of the preceding code is as follows.</span></span>

```
[|3.0; 15.0; 35.0; 63.0; 99.0|]
```

<span data-ttu-id="8137b-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) executa uma função especificada em cada elemento da matriz de uma matriz existente e, em seguida, obtém os elementos gerados pela função e as combina em uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-160">[`Array.collect`](https://msdn.microsoft.com/library/c3b60c3b-9455-48c9-bc2b-e88f0434342a) runs a specified function on each array element of an existing array and then collects the elements generated by the function and combines them into a new array.</span></span> <span data-ttu-id="8137b-161">O código a seguir demonstra `Array.collect`.</span><span class="sxs-lookup"><span data-stu-id="8137b-161">The following code demonstrates `Array.collect`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet15.fs)]

<span data-ttu-id="8137b-162">A saída do código anterior é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8137b-162">The output of the preceding code is as follows.</span></span>

```
[|0; 1; 0; 1; 2; 3; 4; 5; 0; 1; 2; 3; 4; 5; 6; 7; 8; 9; 10|]
```

<span data-ttu-id="8137b-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) usa uma sequência de matrizes e as combina em uma única matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-163">[`Array.concat`](https://msdn.microsoft.com/library/f7219b79-1ec8-4a25-96b1-edbedb358302) takes a sequence of arrays and combines them into a single array.</span></span> <span data-ttu-id="8137b-164">O código a seguir demonstra `Array.concat`.</span><span class="sxs-lookup"><span data-stu-id="8137b-164">The following code demonstrates `Array.concat`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet16.fs)]

<span data-ttu-id="8137b-165">A saída do código anterior é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8137b-165">The output of the preceding code is as follows.</span></span>

```
[|(1, 1, 1); (1, 2, 2); (1, 3, 3); (2, 1, 2); (2, 2, 4); (2, 3, 6); (3, 1, 3);
(3, 2, 6); (3, 3, 9)|]
```

<span data-ttu-id="8137b-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) usa uma função de condição booleana e gerencia uma nova matriz que contém apenas os elementos da matriz de entrada para o qual a condição for verdadeira.</span><span class="sxs-lookup"><span data-stu-id="8137b-166">[`Array.filter`](https://msdn.microsoft.com/library/b885b214-47fc-4639-9664-b8c183a39ede) takes a Boolean condition function and generates a new array that contains only those elements from the input array for which the condition is true.</span></span> <span data-ttu-id="8137b-167">O código a seguir demonstra `Array.filter`.</span><span class="sxs-lookup"><span data-stu-id="8137b-167">The following code demonstrates `Array.filter`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet17.fs)]

<span data-ttu-id="8137b-168">A saída do código anterior é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8137b-168">The output of the preceding code is as follows.</span></span>

```
[|2; 4; 6; 8; 10|]
```

<span data-ttu-id="8137b-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) gera uma nova matriz invertendo a ordem de uma matriz existente.</span><span class="sxs-lookup"><span data-stu-id="8137b-169">[`Array.rev`](https://msdn.microsoft.com/library/1bbf822c-763b-4794-af21-97d2e48ef709) generates a new array by reversing the order of an existing array.</span></span> <span data-ttu-id="8137b-170">O código a seguir demonstra `Array.rev`.</span><span class="sxs-lookup"><span data-stu-id="8137b-170">The following code demonstrates `Array.rev`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet18.fs)]  

<span data-ttu-id="8137b-171">A saída do código anterior é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8137b-171">The output of the preceding code is as follows.</span></span>

```
"Hello world!"
```

<span data-ttu-id="8137b-172">Você pode facilmente combinar funções no módulo de matriz que tornam matrizes usando o operador de pipeline (`|>`), conforme mostrado no exemplo a seguir.</span><span class="sxs-lookup"><span data-stu-id="8137b-172">You can easily combine functions in the array module that transform arrays by using the pipeline operator (`|>`), as shown in the following example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet19.fs)]

<span data-ttu-id="8137b-173">A saída é</span><span class="sxs-lookup"><span data-stu-id="8137b-173">The output is</span></span>

```
[|100; 36; 16; 4|]
```

### <a name="multidimensional-arrays"></a><span data-ttu-id="8137b-174">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="8137b-174">Multidimensional Arrays</span></span>

<span data-ttu-id="8137b-175">Uma matriz multidimensional pode ser criada, mas não há nenhuma sintaxe para gravar um literal de matriz multidimensional.</span><span class="sxs-lookup"><span data-stu-id="8137b-175">A multidimensional array can be created, but there is no syntax for writing a multidimensional array literal.</span></span> <span data-ttu-id="8137b-176">Use o operador [ `array2D` ](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) para criar uma matriz de uma sequência de sequências de elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-176">Use the operator [`array2D`](https://msdn.microsoft.com/library/1d52503d-2990-49fc-8fd3-6b0e508aa236) to create an array from a sequence of sequences of array elements.</span></span> <span data-ttu-id="8137b-177">As sequências podem ser literais de matriz ou lista.</span><span class="sxs-lookup"><span data-stu-id="8137b-177">The sequences can be array or list literals.</span></span> <span data-ttu-id="8137b-178">Por exemplo, o código a seguir cria uma matriz bidimensional.</span><span class="sxs-lookup"><span data-stu-id="8137b-178">For example, the following code creates a two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet20.fs)]

<span data-ttu-id="8137b-179">Você também pode usar a função [ `Array2D.init` ](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) para inicializar matrizes de duas dimensões e semelhante funções estão disponíveis para matrizes de três e quatro dimensões.</span><span class="sxs-lookup"><span data-stu-id="8137b-179">You can also use the function [`Array2D.init`](https://msdn.microsoft.com/library/9de07e95-bc21-4927-b5b4-08fdec882c7b) to initialize arrays of two dimensions, and similar functions are available for arrays of three and four dimensions.</span></span> <span data-ttu-id="8137b-180">Essas funções usam uma função que é usada para criar os elementos.</span><span class="sxs-lookup"><span data-stu-id="8137b-180">These functions take a function that is used to create the elements.</span></span> <span data-ttu-id="8137b-181">Para criar uma matriz bidimensional que contém os elementos definidos para um valor inicial em vez de especificar uma função, use o [ `Array2D.create` ](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) função, que também está disponível para matrizes até quatro dimensões.</span><span class="sxs-lookup"><span data-stu-id="8137b-181">To create a two-dimensional array that contains elements set to an initial value instead of specifying a function, use the [`Array2D.create`](https://msdn.microsoft.com/library/36c9d980-b241-4a20-bc64-bcfa0205d804) function, which is also available for arrays up to four dimensions.</span></span> <span data-ttu-id="8137b-182">O exemplo de código a seguir primeiro mostra como criar uma matriz de matrizes que contêm os elementos desejados e, em seguida, usa `Array2D.init` para gerar a matriz bidimensional desejada.</span><span class="sxs-lookup"><span data-stu-id="8137b-182">The following code example first shows how to create an array of arrays that contain the desired elements, and then uses `Array2D.init` to generate the desired two-dimensional array.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet21.fs)]

<span data-ttu-id="8137b-183">Matriz de indexação e fatiando sintaxe tem suporte para matrizes até a posição 4.</span><span class="sxs-lookup"><span data-stu-id="8137b-183">Array indexing and slicing syntax is supported for arrays up to rank 4.</span></span> <span data-ttu-id="8137b-184">Quando você especifica um índice em várias dimensões, você use vírgulas para separar os índices, conforme ilustrado no exemplo de código a seguir.</span><span class="sxs-lookup"><span data-stu-id="8137b-184">When you specify an index in multiple dimensions, you use commas to separate the indexes, as illustrated in the following code example.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet22.fs)]

<span data-ttu-id="8137b-185">O tipo de uma matriz bidimensional é escrito como `<type>[,]` (por exemplo, `int[,]`, `double[,]`), e o tipo de uma matriz tridimensional é escrito como `<type>[,,]`, e assim por diante para matrizes das dimensões acima.</span><span class="sxs-lookup"><span data-stu-id="8137b-185">The type of a two-dimensional array is written out as `<type>[,]` (for example, `int[,]`, `double[,]`), and the type of a three-dimensional array is written as `<type>[,,]`, and so on for arrays of higher dimensions.</span></span>

<span data-ttu-id="8137b-186">Apenas um subconjunto das funções disponíveis para matrizes unidimensionais também está disponível para matrizes multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="8137b-186">Only a subset of the functions available for one-dimensional arrays is also available for multidimensional arrays.</span></span> <span data-ttu-id="8137b-187">Para obter mais informações, consulte [ `Collections.Array Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [ `Collections.Array2D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [ `Collections.Array3D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), e [ `Collections.Array4D Module` ](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span><span class="sxs-lookup"><span data-stu-id="8137b-187">For more information, see [`Collections.Array Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array-module-%5bfsharp%5d), [`Collections.Array2D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array2d-module-%5bfsharp%5d), [`Collections.Array3D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array3d-module-%5bfsharp%5d), and [`Collections.Array4D Module`](https://msdn.microsoft.com/visualfsharpdocs/conceptual/collections.array4d-module-%5bfsharp%5d).</span></span>

### <a name="array-slicing-and-multidimensional-arrays"></a><span data-ttu-id="8137b-188">Recorte de matriz e matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="8137b-188">Array Slicing and Multidimensional Arrays</span></span>

<span data-ttu-id="8137b-189">Em uma matriz bidimensional (uma matriz), você pode extrair uma submatriz ao especificar intervalos e usar um caractere curinga (`*`) para especificar colunas ou linhas inteiras.</span><span class="sxs-lookup"><span data-stu-id="8137b-189">In a two-dimensional array (a matrix), you can extract a sub-matrix by specifying ranges and using a wildcard (`*`) character to specify whole rows or columns.</span></span>

```fsharp
/ Get rows 1 to N from an NxM matrix (returns a matrix):
matrix.[1.., *]

// Get rows 1 to 3 from a matrix (returns a matrix):
matrix.[1..3, *]

// Get columns 1 to 3 from a matrix (returns a matrix):
matrix.[*, 1..3]

// Get a 3x3 submatrix:
matrix.[1..3, 1..3]
```

<span data-ttu-id="8137b-190">Como de F# 3.1, você pode decompor uma matriz multidimensional em submatrizes da mesma dimensão ou menor.</span><span class="sxs-lookup"><span data-stu-id="8137b-190">As of F# 3.1, you can decompose a multidimensional array into subarrays of the same or lower dimension.</span></span> <span data-ttu-id="8137b-191">Por exemplo, você pode obter um vetor de uma matriz, especificando uma única linha ou coluna.</span><span class="sxs-lookup"><span data-stu-id="8137b-191">For example, you can obtain a vector from a matrix by specifying a single row or column.</span></span>

```fsharp
// Get row 3 from a matrix as a vector:
matrix.[3, *]

// Get column 3 from a matrix as a vector:
matrix.[*, 3]
```

<span data-ttu-id="8137b-192">Você pode usar essa sintaxe de corte para tipos que implementam os operadores de acesso de elemento e sobrecarregados `GetSlice` métodos.</span><span class="sxs-lookup"><span data-stu-id="8137b-192">You can use this slicing syntax for types that implement the element access operators and overloaded `GetSlice` methods.</span></span> <span data-ttu-id="8137b-193">Por exemplo, o código a seguir cria um tipo de matriz que encapsula a F# matriz 2D, implementa uma propriedade de Item para fornecer suporte para indexação de matriz e implementa três versões do `GetSlice`.</span><span class="sxs-lookup"><span data-stu-id="8137b-193">For example, the following code creates a Matrix type that wraps the F# 2D array, implements an Item property to provide support for array indexing, and implements three versions of `GetSlice`.</span></span> <span data-ttu-id="8137b-194">Se você pode usar esse código como um modelo para seus tipos de matriz, você pode usar todas as operações de divisão descritos nesta seção.</span><span class="sxs-lookup"><span data-stu-id="8137b-194">If you can use this code as a template for your matrix types, you can use all the slicing operations that this section describes.</span></span>

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

### <a name="boolean-functions-on-arrays"></a><span data-ttu-id="8137b-195">Funções booleanas em matrizes</span><span class="sxs-lookup"><span data-stu-id="8137b-195">Boolean Functions on Arrays</span></span>

<span data-ttu-id="8137b-196">As funções [ `Array.exists` ](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) e [ `Array.exists2` ](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) testar elementos em uma ou duas matrizes, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="8137b-196">The functions [`Array.exists`](https://msdn.microsoft.com/library/8e47ad6c-c065-4876-8cb4-ec960ec3e5c9) and [`Array.exists2`](https://msdn.microsoft.com/library/2e384a6a-f99d-4e23-b677-250ffbc1dd8e) test elements in either one or two arrays, respectively.</span></span> <span data-ttu-id="8137b-197">Essas funções usam uma função de teste e retornam `true` se não houver um elemento (ou par de elementos para `Array.exists2`) que satisfaz a condição.</span><span class="sxs-lookup"><span data-stu-id="8137b-197">These functions take a test function and return `true` if there is an element (or element pair for `Array.exists2`) that satisfies the condition.</span></span>

<span data-ttu-id="8137b-198">O código a seguir demonstra o uso de `Array.exists` e `Array.exists2`.</span><span class="sxs-lookup"><span data-stu-id="8137b-198">The following code demonstrates the use of `Array.exists` and `Array.exists2`.</span></span> <span data-ttu-id="8137b-199">Nestes exemplos, novas funções são criadas por meio da aplicação de apenas um dos argumentos, nesses casos, o argumento da função.</span><span class="sxs-lookup"><span data-stu-id="8137b-199">In these examples, new functions are created by applying only one of the arguments, in these cases, the function argument.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet23.fs)]

<span data-ttu-id="8137b-200">A saída do código anterior é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8137b-200">The output of the preceding code is as follows.</span></span>

```
true
false
false
true
```

<span data-ttu-id="8137b-201">Da mesma forma, a função [ `Array.forall` ](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) testa uma matriz para determinar se cada elemento satisfaz uma condição booleana.</span><span class="sxs-lookup"><span data-stu-id="8137b-201">Similarly, the function [`Array.forall`](https://msdn.microsoft.com/library/d88f2cd0-fa7f-45cf-ac15-31eae9086cc4) tests an array to determine whether every element satisfies a Boolean condition.</span></span> <span data-ttu-id="8137b-202">A variação [ `Array.forall2` ](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) faz a mesma coisa usando uma função booleana que quebra os elementos de duas matrizes de comprimento igual.</span><span class="sxs-lookup"><span data-stu-id="8137b-202">The variation [`Array.forall2`](https://msdn.microsoft.com/library/c68f61a1-030c-4024-b705-c4768b6c96b9) does the same thing by using a Boolean function that involves elements of two arrays of equal length.</span></span> <span data-ttu-id="8137b-203">O código a seguir ilustra o uso dessas funções.</span><span class="sxs-lookup"><span data-stu-id="8137b-203">The following code illustrates the use of these functions.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet24.fs)]

<span data-ttu-id="8137b-204">A saída para esses exemplos é da seguinte maneira.</span><span class="sxs-lookup"><span data-stu-id="8137b-204">The output for these examples is as follows.</span></span>

```
false
true
true
false
```

### <a name="searching-arrays"></a><span data-ttu-id="8137b-205">Procurando matrizes</span><span class="sxs-lookup"><span data-stu-id="8137b-205">Searching Arrays</span></span>

<span data-ttu-id="8137b-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) usa uma função booleana e retorna o primeiro elemento para o qual a função retornará `true`, ou gera uma <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> se nenhum elemento que satisfaz a condição for encontrado.</span><span class="sxs-lookup"><span data-stu-id="8137b-206">[`Array.find`](https://msdn.microsoft.com/library/db6d920a-de19-4520-85a4-d83de77c1b33) takes a Boolean function and returns the first element for which the function returns `true`, or raises a <xref:System.Collections.Generic.KeyNotFoundException?displayProperty=nameWithType> if no element that satisfies the condition is found.</span></span> <span data-ttu-id="8137b-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) é como `Array.find`, exceto que ele retorna o índice do elemento, em vez do próprio elemento.</span><span class="sxs-lookup"><span data-stu-id="8137b-207">[`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) is like `Array.find`, except that it returns the index of the element instead of the element itself.</span></span>

<span data-ttu-id="8137b-208">O seguinte código usa `Array.find` e `Array.findIndex` para localizar um número que é um quadrado perfeito e um cubo perfeito.</span><span class="sxs-lookup"><span data-stu-id="8137b-208">The following code uses `Array.find` and `Array.findIndex` to locate a number that is both a perfect square and perfect cube.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet25.fs)]

<span data-ttu-id="8137b-209">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="8137b-209">The output is as follows.</span></span>

```
The first element that is both a square and a cube is 64 and its index is 62.
```

<span data-ttu-id="8137b-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) é como `Array.find`, exceto que o resultado é um tipo de opção e retorna `None` se nenhum elemento for encontrado.</span><span class="sxs-lookup"><span data-stu-id="8137b-210">[`Array.tryFind`](https://msdn.microsoft.com/library/7bd65f6c-df77-454c-ac3a-6f7baecec9d9) is like `Array.find`, except that its result is an option type, and it returns `None` if no element is found.</span></span> <span data-ttu-id="8137b-211">`Array.tryFind` deve ser usado em vez de `Array.find` quando você não souber se um elemento correspondente está na matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-211">`Array.tryFind` should be used instead of `Array.find` when you do not know whether a matching element is in the array.</span></span> <span data-ttu-id="8137b-212">Da mesma forma, [ `Array.tryFindIndex` ](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) é como [ `Array.findIndex` ](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) , exceto que o tipo de opção é o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="8137b-212">Similarly, [`Array.tryFindIndex`](https://msdn.microsoft.com/library/da82f7fe-95e9-4fd5-a924-cd3c9d10618a) is like [`Array.findIndex`](https://msdn.microsoft.com/library/5ae3a8f9-7b8f-44ea-a740-d5700f4d899f) except that the option type is the return value.</span></span> <span data-ttu-id="8137b-213">Se nenhum elemento for encontrado, a opção é `None`.</span><span class="sxs-lookup"><span data-stu-id="8137b-213">If no element is found, the option is `None`.</span></span>

<span data-ttu-id="8137b-214">O código a seguir demonstra o uso de `Array.tryFind`.</span><span class="sxs-lookup"><span data-stu-id="8137b-214">The following code demonstrates the use of `Array.tryFind`.</span></span> <span data-ttu-id="8137b-215">Esse código depende do código anterior.</span><span class="sxs-lookup"><span data-stu-id="8137b-215">This code depends on the previous code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet26.fs)]

<span data-ttu-id="8137b-216">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="8137b-216">The output is as follows.</span></span>

```
Found an element: 1
Found an element: 729
```

<span data-ttu-id="8137b-217">Use [ `Array.tryPick` ](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) quando você precisar transformar um elemento além do localizá-lo.</span><span class="sxs-lookup"><span data-stu-id="8137b-217">Use [`Array.tryPick`](https://msdn.microsoft.com/library/72d45f85-037b-43a9-97fd-17239f72713e) when you need to transform an element in addition to finding it.</span></span> <span data-ttu-id="8137b-218">O resultado é o primeiro elemento para o qual a função retorna o elemento transformado como um valor de opção ou `None` se esse elemento não for encontrado.</span><span class="sxs-lookup"><span data-stu-id="8137b-218">The result is the first element for which the function returns the transformed element as an option value, or `None` if no such element is found.</span></span>

<span data-ttu-id="8137b-219">O código a seguir demonstra o uso de `Array.tryPick`.</span><span class="sxs-lookup"><span data-stu-id="8137b-219">The following code shows the use of `Array.tryPick`.</span></span> <span data-ttu-id="8137b-220">Nesse caso, em vez de uma expressão lambda, várias funções auxiliares locais são definidas para simplificar o código.</span><span class="sxs-lookup"><span data-stu-id="8137b-220">In this case, instead of a lambda expression, several local helper functions are defined to simplify the code.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet27.fs)]

<span data-ttu-id="8137b-221">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="8137b-221">The output is as follows.</span></span>

```
Found an element 1 with square root 1 and cube root 1.
Found an element 64 with square root 8 and cube root 4.
Found an element 729 with square root 27 and cube root 9.
Found an element 4096 with square root 64 and cube root 16.
```

### <a name="performing-computations-on-arrays"></a><span data-ttu-id="8137b-222">Realizando cálculos em matrizes</span><span class="sxs-lookup"><span data-stu-id="8137b-222">Performing Computations on Arrays</span></span>

<span data-ttu-id="8137b-223">O [ `Array.average` ](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) função retorna a média de cada elemento em uma matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-223">The [`Array.average`](https://msdn.microsoft.com/library/7029f2b9-91ea-41cb-be1b-466a5a0db20e) function returns the average of each element in an array.</span></span> <span data-ttu-id="8137b-224">Ele é limitado a tipos de elementos que dão suporte à divisão exata por um inteiro, que inclui tipos de ponto flutuante, mas não tipos integrais.</span><span class="sxs-lookup"><span data-stu-id="8137b-224">It is limited to element types that support exact division by an integer, which includes floating point types but not integral types.</span></span> <span data-ttu-id="8137b-225">O [ `Array.averageBy` ](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) função retorna a média dos resultados de chamar uma função em cada elemento.</span><span class="sxs-lookup"><span data-stu-id="8137b-225">The [`Array.averageBy`](https://msdn.microsoft.com/library/e9d64609-06a3-48f0-bc07-226ab0f85c54) function returns the average of the results of calling a function on each element.</span></span> <span data-ttu-id="8137b-226">Para uma matriz do tipo integral, você pode usar `Array.averageBy` e fazer com que a função converter cada elemento de flutuante tipo para o cálculo de ponto.</span><span class="sxs-lookup"><span data-stu-id="8137b-226">For an array of integral type, you can use `Array.averageBy` and have the function convert each element to a floating point type for the computation.</span></span>

<span data-ttu-id="8137b-227">Use [ `Array.max` ](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) ou [ `Array.min` ](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) para obter o elemento mínimo ou máximo, se o tipo de elemento suportá-lo.</span><span class="sxs-lookup"><span data-stu-id="8137b-227">Use [`Array.max`](https://msdn.microsoft.com/library/f03fbda0-fce6-40e2-a85d-79c9d81f710b) or [`Array.min`](https://msdn.microsoft.com/library/d6b3da5f-bac0-4355-9846-4b72d95bc3fd) to get the maximum or minimum element, if the element type supports it.</span></span> <span data-ttu-id="8137b-228">Da mesma forma, [ `Array.maxBy` ](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) e [ `Array.minBy` ](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) permitem que uma função a ser executado pela primeira vez, talvez para se transformar em um tipo que dá suporte à comparação.</span><span class="sxs-lookup"><span data-stu-id="8137b-228">Similarly, [`Array.maxBy`](https://msdn.microsoft.com/library/18dbe7c5-482e-4766-8e01-12a76f847045) and [`Array.minBy`](https://msdn.microsoft.com/library/24091583-be78-4cc9-9fab-de6d7506af4f) allow a function to be executed first, perhaps to transform to a type that supports comparison.</span></span>

<span data-ttu-id="8137b-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) Adiciona os elementos de uma matriz, e [ `Array.sumBy` ](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) chama uma função em cada elemento e adiciona os resultados juntos.</span><span class="sxs-lookup"><span data-stu-id="8137b-229">[`Array.sum`](https://msdn.microsoft.com/library/4ffdb8c8-cd94-4b0b-9e5c-a7c9c17963c2) adds the elements of an array, and [`Array.sumBy`](https://msdn.microsoft.com/library/41698ba6-1adc-4169-8cc5-7a0e3f8de56b) calls a function on each element and adds the results together.</span></span>

<span data-ttu-id="8137b-230">Para executar uma função em cada elemento em uma matriz sem armazenar os valores de retorno, use [ `Array.iter` ](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span><span class="sxs-lookup"><span data-stu-id="8137b-230">To execute a function on each element in an array without storing the return values, use [`Array.iter`](https://msdn.microsoft.com/library/94eba0f1-ecd7-459f-b89f-ed2a2923e516).</span></span> <span data-ttu-id="8137b-231">Para uma função que envolva duas matrizes de comprimento igual, use [ `Array.iter2` ](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span><span class="sxs-lookup"><span data-stu-id="8137b-231">For a function involving two arrays of equal length, use [`Array.iter2`](https://msdn.microsoft.com/library/018aa9b9-f186-4142-be8a-a62462794fdc).</span></span> <span data-ttu-id="8137b-232">Se você também precisa manter uma matriz dos resultados da função, use [ `Array.map` ](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) ou [ `Array.map2` ](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), que opera em duas matrizes de cada vez.</span><span class="sxs-lookup"><span data-stu-id="8137b-232">If you also need to keep an array of the results of the function, use [`Array.map`](https://msdn.microsoft.com/library/38cbe824-0480-47be-85fd-df3afdd97a45) or [`Array.map2`](https://msdn.microsoft.com/library/bb7aafe8-4a1f-45b9-92fc-1af9eafbea5c), which operates on two arrays at a time.</span></span>

<span data-ttu-id="8137b-233">As variações [ `Array.iteri` ](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) e [ `Array.iteri2` ](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) permitem que o índice do elemento a ser envolvido no cálculo; o mesmo é verdadeiro para [ `Array.mapi` ](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) e [ `Array.mapi2` ](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span><span class="sxs-lookup"><span data-stu-id="8137b-233">The variations [`Array.iteri`](https://msdn.microsoft.com/library/8bbe2ed4-ada7-4906-ac3e-cb09f9db6486) and [`Array.iteri2`](https://msdn.microsoft.com/library/c041b91f-6080-45b7-867b-2ed983a90405) allow the index of the element to be involved in the computation; the same is true for [`Array.mapi`](https://msdn.microsoft.com/library/f7e45994-b0a1-49e6-8fb5-5641cea8fde4) and [`Array.mapi2`](https://msdn.microsoft.com/library/5edb33d2-47da-44e1-9290-40c00c47d5b0).</span></span>

<span data-ttu-id="8137b-234">As funções [ `Array.fold` ](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [ `Array.foldBack` ](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [ `Array.reduce` ](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [ `Array.reduceBack` ](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [ `Array.scan` ](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), e [ `Array.scanBack` ](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) executam os algoritmos que envolvem todos os elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-234">The functions [`Array.fold`](https://msdn.microsoft.com/library/5ed9dd3b-3694-4567-94d0-fd9a24474e09), [`Array.foldBack`](https://msdn.microsoft.com/library/1121a453-dead-4711-a0ca-cc147752989c), [`Array.reduce`](https://msdn.microsoft.com/library/fd62a985-89fe-4f49-a9d4-0c808ac6749d), [`Array.reduceBack`](https://msdn.microsoft.com/library/4fdd4cbe-2238-4c5c-b286-597a7e9036f9), [`Array.scan`](https://msdn.microsoft.com/library/f6893608-9146-450d-9ebb-a0016803fbb0), and [`Array.scanBack`](https://msdn.microsoft.com/library/7610f406-7a5c-41db-a0ca-8e2a2a4826ad) execute algorithms that involve all the elements of an array.</span></span> <span data-ttu-id="8137b-235">Da mesma forma, as variações [ `Array.fold2` ](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) e [ `Array.foldBack2` ](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) executam cálculos em duas matrizes.</span><span class="sxs-lookup"><span data-stu-id="8137b-235">Similarly, the variations [`Array.fold2`](https://msdn.microsoft.com/library/5c845087-d041-476e-8cc4-53ae6849ef79) and [`Array.foldBack2`](https://msdn.microsoft.com/library/aa51b405-df20-4c51-9998-a6530f7db862) perform computations on two arrays.</span></span>

<span data-ttu-id="8137b-236">Essas funções para executar cálculos correspondem às funções de mesmo nome na [módulo lista](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span><span class="sxs-lookup"><span data-stu-id="8137b-236">These functions for performing computations correspond to the functions of the same name in the [List module](https://msdn.microsoft.com/library/a2264ba3-2d45-40dd-9040-4f7aa2ad9788).</span></span> <span data-ttu-id="8137b-237">Para obter exemplos de uso, consulte [lista](lists.md).</span><span class="sxs-lookup"><span data-stu-id="8137b-237">For usage examples, see [Lists](lists.md).</span></span>

### <a name="modifying-arrays"></a><span data-ttu-id="8137b-238">Modificando matrizes</span><span class="sxs-lookup"><span data-stu-id="8137b-238">Modifying Arrays</span></span>

<span data-ttu-id="8137b-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) define um elemento com um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="8137b-239">[`Array.set`](https://msdn.microsoft.com/library/847edc0d-4dc5-4a39-98c7-d4320c60e790) sets an element to a specified value.</span></span> <span data-ttu-id="8137b-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) define um intervalo de elementos em uma matriz com um valor especificado.</span><span class="sxs-lookup"><span data-stu-id="8137b-240">[`Array.fill`](https://msdn.microsoft.com/library/c83c9886-81d9-44f9-a195-61c7b87f7df2) sets a range of elements in an array to a specified value.</span></span> <span data-ttu-id="8137b-241">O código a seguir fornece um exemplo de `Array.fill`.</span><span class="sxs-lookup"><span data-stu-id="8137b-241">The following code provides an example of `Array.fill`.</span></span>

[!code-fsharp[Main](../../../samples/snippets/fsharp/arrays/snippet28.fs)]

<span data-ttu-id="8137b-242">A saída é a seguinte.</span><span class="sxs-lookup"><span data-stu-id="8137b-242">The output is as follows.</span></span>

```
[|1; 2; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 0; 23; 24; 25|]
```

<span data-ttu-id="8137b-243">Você pode usar [ `Array.blit` ](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) para copiar uma subseção de uma matriz a outra matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-243">You can use [`Array.blit`](https://msdn.microsoft.com/library/675e13e4-7fb9-4e0d-a5be-a112830de667) to copy a subsection of one array to another array.</span></span>

### <a name="converting-to-and-from-other-types"></a><span data-ttu-id="8137b-244">Conversão de e para outros tipos</span><span class="sxs-lookup"><span data-stu-id="8137b-244">Converting to and from Other Types</span></span>

<span data-ttu-id="8137b-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) cria uma matriz de uma lista.</span><span class="sxs-lookup"><span data-stu-id="8137b-245">[`Array.ofList`](https://msdn.microsoft.com/library/e7225239-f561-45a4-b0b5-69a1cdcae78b) creates an array from a list.</span></span> <span data-ttu-id="8137b-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) cria uma matriz de uma sequência.</span><span class="sxs-lookup"><span data-stu-id="8137b-246">[`Array.ofSeq`](https://msdn.microsoft.com/library/6bedf5e0-4b22-46da-b09c-6aa09eff220c) creates an array from a sequence.</span></span> <span data-ttu-id="8137b-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) e [ `Array.toSeq` ](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) converter para esses outros tipos de coleção do tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-247">[`Array.toList`](https://msdn.microsoft.com/library/4deff724-0be4-4688-92e7-9d67a1097786) and [`Array.toSeq`](https://msdn.microsoft.com/library/ac28dbab-406c-4fe0-ab08-c1ce5e247af4) convert to these other collection types from the array type.</span></span>

### <a name="sorting-arrays"></a><span data-ttu-id="8137b-248">Matrizes de classificação</span><span class="sxs-lookup"><span data-stu-id="8137b-248">Sorting Arrays</span></span>

<span data-ttu-id="8137b-249">Use [ `Array.sort` ](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) para classificar uma matriz usando a função de comparação genérica.</span><span class="sxs-lookup"><span data-stu-id="8137b-249">Use [`Array.sort`](https://msdn.microsoft.com/library/c6679075-e7eb-463c-9be5-c89be140c312) to sort an array by using the generic comparison function.</span></span> <span data-ttu-id="8137b-250">Use [ `Array.sortBy` ](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) especificar uma função que gera um valor, conhecido como um *chave*, para classificar por meio da função de comparação genérica na chave.</span><span class="sxs-lookup"><span data-stu-id="8137b-250">Use [`Array.sortBy`](https://msdn.microsoft.com/library/144498dc-091d-4575-a229-c0bcbd61426b) to specify a function that generates a value, referred to as a *key*, to sort by using the generic comparison function on the key.</span></span> <span data-ttu-id="8137b-251">Use [ `Array.sortWith` ](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) se você quiser fornecer uma função de comparação personalizada.</span><span class="sxs-lookup"><span data-stu-id="8137b-251">Use [`Array.sortWith`](https://msdn.microsoft.com/library/699d3638-4244-4f42-8496-45f53d43ce95) if you want to provide a custom comparison function.</span></span> <span data-ttu-id="8137b-252">`Array.sort`, `Array.sortBy`, e `Array.sortWith` todos retornam a matriz classificada como uma nova matriz.</span><span class="sxs-lookup"><span data-stu-id="8137b-252">`Array.sort`, `Array.sortBy`, and `Array.sortWith` all return the sorted array as a new array.</span></span> <span data-ttu-id="8137b-253">As variações [ `Array.sortInPlace` ](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [ `Array.sortInPlaceBy` ](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), e [ `Array.sortInPlaceWith` ](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modificam a matriz existente em vez de retornar um novo.</span><span class="sxs-lookup"><span data-stu-id="8137b-253">The variations [`Array.sortInPlace`](https://msdn.microsoft.com/library/36f39947-8a88-4823-9e9b-e9d838d292e0), [`Array.sortInPlaceBy`](https://msdn.microsoft.com/library/7fb9d2dd-d461-4c67-8b43-b5c59fc12c3f), and [`Array.sortInPlaceWith`](https://msdn.microsoft.com/library/454f9e11-972d-47a6-a854-8031cb0c7b0b) modify the existing array instead of returning a new one.</span></span>

### <a name="arrays-and-tuples"></a><span data-ttu-id="8137b-254">Matrizes e Tuples</span><span class="sxs-lookup"><span data-stu-id="8137b-254">Arrays and Tuples</span></span>

<span data-ttu-id="8137b-255">As funções [ `Array.zip` ](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) e [ `Array.unzip` ](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) converter matrizes de pares de tupla em tuplas de matrizes e vice-versa.</span><span class="sxs-lookup"><span data-stu-id="8137b-255">The functions [`Array.zip`](https://msdn.microsoft.com/library/23e086b8-b266-4db2-8b68-e88e6a8e2187) and [`Array.unzip`](https://msdn.microsoft.com/library/a529b47c-2e2b-4f79-ad44-c578432d2f48) convert arrays of tuple pairs to tuples of arrays and vice versa.</span></span> <span data-ttu-id="8137b-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) e [ `Array.unzip3` ](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) são semelhantes, exceto que eles funcionam com tuples de três elementos ou tuples de três matrizes.</span><span class="sxs-lookup"><span data-stu-id="8137b-256">[`Array.zip3`](https://msdn.microsoft.com/library/1745744a-d2ca-4c3e-b825-3f15d9f4000d) and [`Array.unzip3`](https://msdn.microsoft.com/library/bc3e6db0-f334-444f-8c30-813942880677) are similar except that they work with tuples of three elements or tuples of three arrays.</span></span>

## <a name="parallel-computations-on-arrays"></a><span data-ttu-id="8137b-257">Cálculos paralelos em matrizes</span><span class="sxs-lookup"><span data-stu-id="8137b-257">Parallel Computations on Arrays</span></span>

<span data-ttu-id="8137b-258">O módulo [ `Array.Parallel` ](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contém funções para executar cálculos paralelos em matrizes.</span><span class="sxs-lookup"><span data-stu-id="8137b-258">The module [`Array.Parallel`](https://msdn.microsoft.com/library/60f30b77-5af4-4050-9a5c-bcdb3f5cbb09) contains functions for performing parallel computations on arrays.</span></span> <span data-ttu-id="8137b-259">Esse módulo não está disponível em aplicativos destinados a versões do .NET Framework anteriores à versão 4.</span><span class="sxs-lookup"><span data-stu-id="8137b-259">This module is not available in applications that target versions of the .NET Framework prior to version 4.</span></span>

## <a name="see-also"></a><span data-ttu-id="8137b-260">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8137b-260">See also</span></span>

- [<span data-ttu-id="8137b-261">Referência da Linguagem F#</span><span class="sxs-lookup"><span data-stu-id="8137b-261">F# Language Reference</span></span>](index.md)
- [<span data-ttu-id="8137b-262">F#; Tipos</span><span class="sxs-lookup"><span data-stu-id="8137b-262">F#; Types</span></span>](fsharp-types.md)
