---
title: Matrizes unidimensionais – Guia de Programação em C#
description: Crie uma matriz unidimensional em C# usando o novo operador especificando o tipo de elemento de matriz e o número de elementos.
ms.date: 06/03/2020
helpviewer_keywords:
- single-dimensional arrays [C#]
- arrays [C#], single-dimensional
ms.assetid: 2cec1196-1de0-49d2-baf2-c607c33310e8
ms.openlocfilehash: ada01262d57cbfebc8bfa1a5fee0639a10db5a4b
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474586"
---
# <a name="single-dimensional-arrays-c-programming-guide"></a><span data-ttu-id="55ce8-103">Matrizes unidimensionais (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="55ce8-103">Single-Dimensional Arrays (C# Programming Guide)</span></span>

<span data-ttu-id="55ce8-104">Você cria uma matriz unidimensional usando o [novo](../../language-reference/operators/new-operator.md) operador especificando o tipo de elemento de matriz e o número de elementos.</span><span class="sxs-lookup"><span data-stu-id="55ce8-104">You create a single-dimensional array using the [new](../../language-reference/operators/new-operator.md) operator specifying the array element type and the number of elements.</span></span> <span data-ttu-id="55ce8-105">O exemplo a seguir declara uma matriz de cinco inteiros:</span><span class="sxs-lookup"><span data-stu-id="55ce8-105">The following example declares an array of five integers:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntDeclaration":::

<span data-ttu-id="55ce8-106">Essa matriz contém os elementos de `array[0]` a `array[4]`.</span><span class="sxs-lookup"><span data-stu-id="55ce8-106">This array contains the elements from `array[0]` to `array[4]`.</span></span> <span data-ttu-id="55ce8-107">Os elementos da matriz são inicializados para o valor padrão do tipo de elemento, `0` para inteiros.</span><span class="sxs-lookup"><span data-stu-id="55ce8-107">The elements of the array are initialized to the default value of the element type, `0` for integers.</span></span>

<span data-ttu-id="55ce8-108">As matrizes podem armazenar qualquer tipo de elemento que você especificar, como o exemplo a seguir, que declara uma matriz de cadeias de caracteres:</span><span class="sxs-lookup"><span data-stu-id="55ce8-108">Arrays can store any element type you specify, such as the following example that declares an array of strings:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringDeclaration":::

## <a name="array-initialization"></a><span data-ttu-id="55ce8-109">Inicialização de Matriz</span><span class="sxs-lookup"><span data-stu-id="55ce8-109">Array Initialization</span></span>

<span data-ttu-id="55ce8-110">Você pode inicializar os elementos de uma matriz ao declarar a matriz.</span><span class="sxs-lookup"><span data-stu-id="55ce8-110">You can initialize the elements of an array when you declare the array.</span></span> <span data-ttu-id="55ce8-111">O especificador de comprimento não é necessário porque é inferido pelo número de elementos na lista de inicialização.</span><span class="sxs-lookup"><span data-stu-id="55ce8-111">The length specifier isn't needed because it's inferred by the number of elements in the initialization list.</span></span> <span data-ttu-id="55ce8-112">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="55ce8-112">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="IntInitialization":::

<span data-ttu-id="55ce8-113">O código a seguir mostra uma declaração de uma matriz de cadeia de caracteres em que cada elemento da matriz é inicializado por um nome de um dia:</span><span class="sxs-lookup"><span data-stu-id="55ce8-113">The following code shows a declaration of a string array where each array element is initialized by a name of a day:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="StringInitialization":::
  
<span data-ttu-id="55ce8-114">Você pode evitar a `new` expressão e o tipo de matriz ao inicializar uma matriz na declaração, conforme mostrado no código a seguir.</span><span class="sxs-lookup"><span data-stu-id="55ce8-114">You can avoid the `new` expression and the array type when you initialize an array upon declaration, as shown in the following code.</span></span> <span data-ttu-id="55ce8-115">Isso é chamado de [matriz tipada implicitamente](implicitly-typed-arrays.md):</span><span class="sxs-lookup"><span data-stu-id="55ce8-115">This is called an [implicitly typed array](implicitly-typed-arrays.md):</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="ShorthandInitialization":::

<span data-ttu-id="55ce8-116">Você pode declarar uma variável de matriz sem criá-la, mas deve usar o `new` operador ao atribuir uma nova matriz a essa variável.</span><span class="sxs-lookup"><span data-stu-id="55ce8-116">You can declare an array variable without creating it, but you must use the `new` operator when you assign a new array to this variable.</span></span> <span data-ttu-id="55ce8-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="55ce8-117">For example:</span></span>

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="DeclareAllocate":::

## <a name="value-type-and-reference-type-arrays"></a><span data-ttu-id="55ce8-118">Matrizes de tipo de valor e de tipo de referência</span><span class="sxs-lookup"><span data-stu-id="55ce8-118">Value Type and Reference Type Arrays</span></span>

<span data-ttu-id="55ce8-119">Considere a seguinte declaração de matriz:</span><span class="sxs-lookup"><span data-stu-id="55ce8-119">Consider the following array declaration:</span></span>  

:::code language="csharp" source="snippets/SingleDimensionArrays.cs" id="FinalInstantiation":::

<span data-ttu-id="55ce8-120">O resultado dessa instrução depende se `SomeType` é um tipo de valor ou um tipo de referência.</span><span class="sxs-lookup"><span data-stu-id="55ce8-120">The result of this statement depends on whether `SomeType` is a value type or a reference type.</span></span> <span data-ttu-id="55ce8-121">Se for um tipo de valor, a instrução criará uma matriz de 10 elementos, cada um com o tipo `SomeType` .</span><span class="sxs-lookup"><span data-stu-id="55ce8-121">If it's a value type, the statement creates an array of 10 elements, each of which has the type `SomeType`.</span></span> <span data-ttu-id="55ce8-122">Se `SomeType` for um tipo de referência, a instrução criará uma matriz de 10 elementos, cada um deles é inicializado com uma referência nula.</span><span class="sxs-lookup"><span data-stu-id="55ce8-122">If `SomeType` is a reference type, the statement creates an array of 10 elements, each of which is initialized to a null reference.</span></span> <span data-ttu-id="55ce8-123">Em ambas as instâncias, os elementos são inicializados para o valor padrão para o tipo de elemento.</span><span class="sxs-lookup"><span data-stu-id="55ce8-123">In both instances, the elements are initialized to the default value for the element type.</span></span> <span data-ttu-id="55ce8-124">Para obter mais informações sobre tipos de valor e tipos de referência, consulte [tipos de valor](../../language-reference/builtin-types/value-types.md) e [tipos de referência](../../language-reference/keywords/reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="55ce8-124">For more information about value types and reference types, see [Value types](../../language-reference/builtin-types/value-types.md) and [Reference types](../../language-reference/keywords/reference-types.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="55ce8-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55ce8-125">See also</span></span>

- <xref:System.Array>
- [<span data-ttu-id="55ce8-126">matrizes</span><span class="sxs-lookup"><span data-stu-id="55ce8-126">Arrays</span></span>](./index.md)
- [<span data-ttu-id="55ce8-127">Matrizes multidimensionais</span><span class="sxs-lookup"><span data-stu-id="55ce8-127">Multidimensional Arrays</span></span>](./multidimensional-arrays.md)
- [<span data-ttu-id="55ce8-128">Matrizes denteadas</span><span class="sxs-lookup"><span data-stu-id="55ce8-128">Jagged Arrays</span></span>](./jagged-arrays.md)
