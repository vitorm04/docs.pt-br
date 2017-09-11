---
title: Matrizes em C# - um tour pela linguagem C#
description: "Matrizes são o tipo mais básico de coleção da linguagem C#"
keywords: ".NET, csharp, matriz, coleção"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a440704c-9e88-4c75-97dd-bfe30ca0fb97
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 82362a3675c431423a99d3d728fb8dd1da58c9c7
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---

# <a name="arrays"></a><span data-ttu-id="7b899-104">Matrizes</span><span class="sxs-lookup"><span data-stu-id="7b899-104">Arrays</span></span>

<span data-ttu-id="7b899-105">Uma ***matriz*** é uma estrutura de dados que contém algumas variáveis acessadas por meio de índices calculados.</span><span class="sxs-lookup"><span data-stu-id="7b899-105">An ***array*** is a data structure that contains a number of variables that are accessed through computed indices.</span></span> <span data-ttu-id="7b899-106">As variáveis contidas em uma matriz, também chamadas de ***elementos*** da matriz, são todas do mesmo tipo, e esse tipo é chamado de ***tipo de elemento*** da matriz.</span><span class="sxs-lookup"><span data-stu-id="7b899-106">The variables contained in an array, also called the ***elements*** of the array, are all of the same type, and this type is called the ***element type*** of the array.</span></span>

<span data-ttu-id="7b899-107">Os tipos de matriz são tipos de referência, e a declaração de uma variável de matriz simplesmente reserva espaço para uma referência a uma instância de matriz.</span><span class="sxs-lookup"><span data-stu-id="7b899-107">Array types are reference types, and the declaration of an array variable simply sets aside space for a reference to an array instance.</span></span> <span data-ttu-id="7b899-108">As instâncias reais da matriz são criadas dinamicamente em tempo de execução usando o operador new.</span><span class="sxs-lookup"><span data-stu-id="7b899-108">Actual array instances are created dynamically at runtime using the new operator.</span></span> <span data-ttu-id="7b899-109">A operação new especifica a ***duração*** da nova instância de matriz, que depois fica fixa para o tempo de vida da instância.</span><span class="sxs-lookup"><span data-stu-id="7b899-109">The new operation specifies the ***length*** of the new array instance, which is then fixed for the lifetime of the instance.</span></span> <span data-ttu-id="7b899-110">Os índices dos elementos de uma matriz variam de `0` a `Length - 1`.</span><span class="sxs-lookup"><span data-stu-id="7b899-110">The indices of the elements of an array range from `0` to `Length - 1`.</span></span> <span data-ttu-id="7b899-111">O operador `new` inicializa automaticamente os elementos de uma matriz usando o valor padrão, que, por exemplo, é zero para todos os tipos numéricos e `null` para todos os tipos de referência.</span><span class="sxs-lookup"><span data-stu-id="7b899-111">The `new` operator automatically initializes the elements of an array to their default value, which, for example, is zero for all numeric types and `null` for all reference types.</span></span>

<span data-ttu-id="7b899-112">O exemplo a seguir cria uma matriz de elementos `int`, inicializa a matriz e imprime o conteúdo da matriz.</span><span class="sxs-lookup"><span data-stu-id="7b899-112">The following example creates an array of `int` elements, initializes the array, and prints out the contents of the array.</span></span>

<span data-ttu-id="7b899-113">[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]</span><span class="sxs-lookup"><span data-stu-id="7b899-113">[!code-csharp[ArraySample](../../../samples/snippets/csharp/tour/arrays/Program.cs#L3-L18)]</span></span>

<span data-ttu-id="7b899-114">Este exemplo cria e opera em uma ***matriz unidimensional***.</span><span class="sxs-lookup"><span data-stu-id="7b899-114">This example creates and operates on a ***single-dimensional array***.</span></span> <span data-ttu-id="7b899-115">O C# também oferece suporte a ***matrizes multidimensionais***.</span><span class="sxs-lookup"><span data-stu-id="7b899-115">C# also supports ***multi-dimensional arrays***.</span></span> <span data-ttu-id="7b899-116">O número de dimensões de um tipo de matriz, também conhecido como ***classificação*** do tipo de matriz, é o número um mais o número de vírgulas escrito entre os colchetes do tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="7b899-116">The number of dimensions of an array type, also known as the ***rank*** of the array type, is one plus the number of commas written between the square brackets of the array type.</span></span> <span data-ttu-id="7b899-117">O exemplo a seguir aloca uma matriz unidimensional, bidimensional e tridimensional, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="7b899-117">The following example allocates a single-dimensional, a two-dimensional, and a three-dimensional array, respectively.</span></span>

<span data-ttu-id="7b899-118">[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]</span><span class="sxs-lookup"><span data-stu-id="7b899-118">[!code-csharp[ArrayRank](../../../samples/snippets/csharp/tour/arrays/Program.cs#L24-L26)]</span></span>

<span data-ttu-id="7b899-119">A matriz `a1` contém 10 elementos, a matriz `a2` contém 50 (10 × 5) elementos e a matriz `a3` contém 100 (10 × 5 × 2) elementos.</span><span class="sxs-lookup"><span data-stu-id="7b899-119">The `a1` array contains 10 elements, the `a2` array contains 50 (10 × 5) elements, and the `a3` array contains 100 (10 × 5 × 2) elements.</span></span>
<span data-ttu-id="7b899-120">O tipo do elemento de uma matriz pode ser qualquer tipo, incluindo um tipo de matriz.</span><span class="sxs-lookup"><span data-stu-id="7b899-120">The element type of an array can be any type, including an array type.</span></span> <span data-ttu-id="7b899-121">Uma matriz com elementos de um tipo de matriz é chamada às vezes de ***matriz denteada***, pois os tamanhos das matrizes do elemento nem sempre precisam ser iguais.</span><span class="sxs-lookup"><span data-stu-id="7b899-121">An array with elements of an array type is sometimes called a ***jagged array*** because the lengths of the element arrays do not all have to be the same.</span></span> <span data-ttu-id="7b899-122">O exemplo a seguir aloca uma matriz de matrizes de `int`:</span><span class="sxs-lookup"><span data-stu-id="7b899-122">The following example allocates an array of arrays of `int`:</span></span>

<span data-ttu-id="7b899-123">[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]</span><span class="sxs-lookup"><span data-stu-id="7b899-123">[!code-csharp[ArrayAllocation](../../../samples/snippets/csharp/tour/arrays/Program.cs#L31-L34)]</span></span>

<span data-ttu-id="7b899-124">A primeira linha cria uma matriz com três elementos, cada um do tipo `int[]`, e cada um com um valor inicial de `null`.</span><span class="sxs-lookup"><span data-stu-id="7b899-124">The first line creates an array with three elements, each of type `int[]` and each with an initial value of `null`.</span></span> <span data-ttu-id="7b899-125">As linhas subsequentes inicializam os três elementos com referências às instâncias individuais da matriz de tamanhos variados.</span><span class="sxs-lookup"><span data-stu-id="7b899-125">The subsequent lines then initialize the three elements with references to individual array instances of varying lengths.</span></span>

<span data-ttu-id="7b899-126">O operador new permite que os valores iniciais dos elementos da matriz sejam especificados com um ***inicializador de matriz***, que é uma lista de expressões escritas entre os delimitadores `{` e `}`.</span><span class="sxs-lookup"><span data-stu-id="7b899-126">The new operator permits the initial values of the array elements to be specified using an ***array initializer***, which is a list of expressions written between the delimiters `{` and `}`.</span></span> <span data-ttu-id="7b899-127">O exemplo a seguir aloca e inicializa um `int[]` com três elementos.</span><span class="sxs-lookup"><span data-stu-id="7b899-127">The following example allocates and initializes an `int[]` with three elements.</span></span>

<span data-ttu-id="7b899-128">[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]</span><span class="sxs-lookup"><span data-stu-id="7b899-128">[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L39-L39)]</span></span>

<span data-ttu-id="7b899-129">Observe que o tamanho da matriz é inferido do número de expressões entre { e }.</span><span class="sxs-lookup"><span data-stu-id="7b899-129">Note that the length of the array is inferred from the number of expressions between { and }.</span></span> <span data-ttu-id="7b899-130">A variável local e declarações de campo podem ser reduzidas ainda mais, de modo que o tipo de matriz não precise ser redefinido.</span><span class="sxs-lookup"><span data-stu-id="7b899-130">Local variable and field declarations can be shortened further such that the array type does not have to be restated.</span></span>

<span data-ttu-id="7b899-131">[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]</span><span class="sxs-lookup"><span data-stu-id="7b899-131">[!code-csharp[ArrayInitialization](../../../samples/snippets/csharp/tour/arrays/Program.cs#L44-L44)]</span></span>

<span data-ttu-id="7b899-132">Os dois exemplos anteriores são equivalentes ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="7b899-132">Both of the previous examples are equivalent to the following:</span></span>

<span data-ttu-id="7b899-133">[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]</span><span class="sxs-lookup"><span data-stu-id="7b899-133">[!code-csharp[ArrayAssignment](../../../samples/snippets/csharp/tour/arrays/Program.cs#L49-L53)]</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="7b899-134">[Anterior](structs.md)
[Próximo](interfaces.md)</span><span class="sxs-lookup"><span data-stu-id="7b899-134">[Previous](structs.md)
[Next](interfaces.md)</span></span>

