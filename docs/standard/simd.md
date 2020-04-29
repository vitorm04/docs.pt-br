---
title: Tipos acelerados por SIMD no .NET
description: Este artigo descreve os tipos de habilitação para SIMD no .NET e demonstra como usar operações de hardware SIMD em C# e .NET.
author: FIVIL
ms.author: tagoo
ms.date: 04/28/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 27263931ff0338e194c8fd3d9ec5ba59bfafd9fe
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507778"
---
# <a name="use-simd-accelerated-numeric-types"></a><span data-ttu-id="3b32f-103">Usar tipos numéricos acelerados por SIMD</span><span class="sxs-lookup"><span data-stu-id="3b32f-103">Use SIMD-accelerated numeric types</span></span>

<span data-ttu-id="3b32f-104">O SIMD (instrução única, vários dados) fornece suporte de hardware para executar uma operação em vários dados, em paralelo, usando uma única instrução.</span><span class="sxs-lookup"><span data-stu-id="3b32f-104">SIMD (Single instruction, multiple data) provides hardware support for performing an operation on multiple pieces of data, in parallel, using a single instruction.</span></span> <span data-ttu-id="3b32f-105">No .NET, há um conjunto de tipos com aceleração SIMD no <xref:System.Numerics> namespace.</span><span class="sxs-lookup"><span data-stu-id="3b32f-105">In .NET, there's set of SIMD-accelerated types under the <xref:System.Numerics> namespace.</span></span> <span data-ttu-id="3b32f-106">As operações de SIMD podem ser paralelizadas no nível de hardware.</span><span class="sxs-lookup"><span data-stu-id="3b32f-106">SIMD operations can be parallelized at the hardware level.</span></span> <span data-ttu-id="3b32f-107">Isso aumenta a taxa de transferência dos cálculos vetorizadas, que são comuns em aplicativos matemáticos, científicos e gráficos.</span><span class="sxs-lookup"><span data-stu-id="3b32f-107">That increases the throughput of the vectorized computations, which are common in mathematical, scientific, and graphics apps.</span></span>

## <a name="net-simd-accelerated-types"></a><span data-ttu-id="3b32f-108">Tipos acelerados pelo .NET SIMD</span><span class="sxs-lookup"><span data-stu-id="3b32f-108">.NET SIMD-accelerated types</span></span>

<span data-ttu-id="3b32f-109">Os tipos acelerados do .NET SIMD incluem os seguintes tipos:</span><span class="sxs-lookup"><span data-stu-id="3b32f-109">The .NET SIMD-accelerated types include the following types:</span></span>

- <span data-ttu-id="3b32f-110">Os tipos <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3> e <xref:System.Numerics.Vector4>, que representam vetores com 2, 3 e 4 valores de <xref:System.Single>.</span><span class="sxs-lookup"><span data-stu-id="3b32f-110">The <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span>

- <span data-ttu-id="3b32f-111">Dois tipos de matriz <xref:System.Numerics.Matrix3x2>,, que representam uma matriz 3x2 e <xref:System.Numerics.Matrix4x4>, que representa uma matriz 4x4 de <xref:System.Single> valores.</span><span class="sxs-lookup"><span data-stu-id="3b32f-111">Two matrix types, <xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix of <xref:System.Single> values.</span></span>

- <span data-ttu-id="3b32f-112">O <xref:System.Numerics.Plane> tipo, que representa um plano em espaço tridimensional usando <xref:System.Single> valores.</span><span class="sxs-lookup"><span data-stu-id="3b32f-112">The <xref:System.Numerics.Plane> type, which represents a plane in three-dimensional space using <xref:System.Single> values.</span></span>

- <span data-ttu-id="3b32f-113">O <xref:System.Numerics.Quaternion> tipo, que representa um vetor que é usado para codificar rotações físicas tridimensionais usando <xref:System.Single> valores.</span><span class="sxs-lookup"><span data-stu-id="3b32f-113">The <xref:System.Numerics.Quaternion> type, which represents a vector that is used to encode three-dimensional physical rotations using <xref:System.Single> values.</span></span>

- <span data-ttu-id="3b32f-114">O tipo <xref:System.Numerics.Vector%601>, que representa um vetor de um tipo numérico especificado e fornece um amplo conjunto de operadores que se beneficiam de suporte a SIMD.</span><span class="sxs-lookup"><span data-stu-id="3b32f-114">The <xref:System.Numerics.Vector%601> type, which represents a vector of a specified numeric type and provides a broad set of operators that benefit from SIMD support.</span></span> <span data-ttu-id="3b32f-115">A contagem de uma <xref:System.Numerics.Vector%601> instância é fixa durante o tempo de vida de um aplicativo, mas <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> seu valor depende da CPU da máquina que executa o código.</span><span class="sxs-lookup"><span data-stu-id="3b32f-115">The count of a <xref:System.Numerics.Vector%601> instance is fixed for the lifetime of an application, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

  > [!NOTE]
  > <span data-ttu-id="3b32f-116">O <xref:System.Numerics.Vector%601> tipo não está incluído na .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3b32f-116">The <xref:System.Numerics.Vector%601> type is not included in the .NET Framework.</span></span> <span data-ttu-id="3b32f-117">Você deve instalar o pacote [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) do NuGet para obter acesso a esse tipo.</span><span class="sxs-lookup"><span data-stu-id="3b32f-117">You must install the [System.Numerics.Vectors](https://www.nuget.org/packages/System.Numerics.Vectors) NuGet package to get access to this type.</span></span>
  
<span data-ttu-id="3b32f-118">Os tipos com aceleração SIMD são implementados de forma que possam ser usados com hardware ou compiladores JIT que não são acelerados por SIMD.</span><span class="sxs-lookup"><span data-stu-id="3b32f-118">The SIMD-accelerated types are implemented in such a way that they can be used with non-SIMD-accelerated hardware or JIT compilers.</span></span> <span data-ttu-id="3b32f-119">Para aproveitar as instruções de SIMD, seus aplicativos de 64 bits devem ser executados pelo tempo de execução que usa o compilador **RyuJIT** .</span><span class="sxs-lookup"><span data-stu-id="3b32f-119">To take advantage of SIMD instructions, your 64-bit apps must be run by the runtime that uses the **RyuJIT** compiler.</span></span> <span data-ttu-id="3b32f-120">Um compilador **RyuJIT** está incluído no .NET Core e no .NET Framework 4,6 e posterior.</span><span class="sxs-lookup"><span data-stu-id="3b32f-120">A **RyuJIT** compiler is included in .NET Core and in .NET Framework 4.6 and later.</span></span> <span data-ttu-id="3b32f-121">O suporte a SIMD é fornecido apenas ao direcionar processadores de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="3b32f-121">SIMD support is only provided when targeting 64-bit processors.</span></span>

## <a name="how-to-use-simd"></a><span data-ttu-id="3b32f-122">Como usar o SIMD?</span><span class="sxs-lookup"><span data-stu-id="3b32f-122">How to use SIMD?</span></span>

<span data-ttu-id="3b32f-123">Antes de executar algoritmos de SIMD personalizados, é possível verificar se o computador host dá suporte a <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>SIMD usando o, <xref:System.Boolean>que retorna um.</span><span class="sxs-lookup"><span data-stu-id="3b32f-123">Before executing custom SIMD algorithms, it's possible to check if the host machine supports SIMD by using <xref:System.Numerics.Vector.IsHardwareAccelerated?displayProperty=nameWithType>, which returns a <xref:System.Boolean>.</span></span> <span data-ttu-id="3b32f-124">Isso não garante que a aceleração SIMD esteja habilitada para um tipo específico, mas é um indicador de que há suporte para alguns tipos.</span><span class="sxs-lookup"><span data-stu-id="3b32f-124">This doesn't guarantee that SIMD-acceleration is enabled for a specific type, but is an indicator that it's supported by some types.</span></span>

## <a name="simple-vectors"></a><span data-ttu-id="3b32f-125">Vetores simples</span><span class="sxs-lookup"><span data-stu-id="3b32f-125">Simple Vectors</span></span>

<span data-ttu-id="3b32f-126">Os tipos mais primitivos de SIMD mais rápidos no .NET <xref:System.Numerics.Vector2>são <xref:System.Numerics.Vector3>, e <xref:System.Numerics.Vector4> tipos, que representam vetores com 2, 3 e 4 <xref:System.Single> valores.</span><span class="sxs-lookup"><span data-stu-id="3b32f-126">The most primitive SIMD-accelerated types in .NET are <xref:System.Numerics.Vector2>, <xref:System.Numerics.Vector3>, and <xref:System.Numerics.Vector4> types, which represent vectors with 2, 3, and 4 <xref:System.Single> values.</span></span> <span data-ttu-id="3b32f-127">O exemplo a seguir <xref:System.Numerics.Vector2> usa para adicionar dois vetores.</span><span class="sxs-lookup"><span data-stu-id="3b32f-127">The example below uses <xref:System.Numerics.Vector2> to add two vectors.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl = v1 + v2;
```

<span data-ttu-id="3b32f-128">Também é possível usar vetores do .net para calcular outras propriedades matemáticas de vetores, como `Dot product`, `Transform` `Clamp` e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="3b32f-128">It's also possible to use .NET vectors to calculate other mathematical properties of vectors such as `Dot product`, `Transform`, `Clamp` and so on.</span></span>

```csharp
var v1 = new Vector2(0.1f, 0.2f);
var v2 = new Vector2(1.1f, 2.2f);
var vResutl1 = Vector2.Dot(v1, v2);
var vResutl2 = Vector2.Distance(v1, v2);
var vResutl3 = Vector2.Clamp(v1, Vector2.Zero, Vector2.One);
```

## <a name="matrix"></a><span data-ttu-id="3b32f-129">Matriz</span><span class="sxs-lookup"><span data-stu-id="3b32f-129">Matrix</span></span>

<span data-ttu-id="3b32f-130"><xref:System.Numerics.Matrix3x2>, que representa uma matriz 3x2 e <xref:System.Numerics.Matrix4x4>, que representa uma matriz 4x4.</span><span class="sxs-lookup"><span data-stu-id="3b32f-130"><xref:System.Numerics.Matrix3x2>, which represents a 3x2 matrix, and <xref:System.Numerics.Matrix4x4>, which represents a 4x4 matrix.</span></span> <span data-ttu-id="3b32f-131">Pode ser usado para cálculos relacionados à matriz.</span><span class="sxs-lookup"><span data-stu-id="3b32f-131">Can be used for matrix-related calculations.</span></span> <span data-ttu-id="3b32f-132">O exemplo a seguir demonstra a multiplicação de uma matriz em sua matriz de Transpose de correspondente usando o SIMD.</span><span class="sxs-lookup"><span data-stu-id="3b32f-132">The example below demonstrates multiplication of a matrix to its correspondent transpose matrix using SIMD.</span></span>

```csharp
var m1 = new Matrix4x4(
            1.1f, 1.2f, 1.3f, 1.4f,
            2.1f, 2.2f, 3.3f, 4.4f,
            3.1f, 3.2f, 3.3f, 3.4f,
            4.1f, 4.2f, 4.3f, 4.4f);

var m2 = Matrix4x4.Transpose(m1);
var mResult = Matrix4x4.Multiply(m1, m2);
```

## <a name="vectort"></a><span data-ttu-id="3b32f-133">>\<de vetor T</span><span class="sxs-lookup"><span data-stu-id="3b32f-133">Vector\<T></span></span>

<span data-ttu-id="3b32f-134">O <xref:System.Numerics.Vector%601> oferece a capacidade de usar vetores mais longos.</span><span class="sxs-lookup"><span data-stu-id="3b32f-134">The <xref:System.Numerics.Vector%601> gives the ability to use longer vectors.</span></span> <span data-ttu-id="3b32f-135">A contagem de uma <xref:System.Numerics.Vector%601> instância é fixa, mas seu valor <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depende da CPU da máquina que executa o código.</span><span class="sxs-lookup"><span data-stu-id="3b32f-135">The count of a <xref:System.Numerics.Vector%601> instance is fixed, but its value <xref:System.Numerics.Vector%601.Count%2A?displayProperty=nameWithType> depends on the CPU of the machine running the code.</span></span>

<span data-ttu-id="3b32f-136">O exemplo a seguir demonstra como adicionar elementos de <xref:System.Numerics.Vector%601>matrizes longos usando.</span><span class="sxs-lookup"><span data-stu-id="3b32f-136">The example below demonstrates adding long arrays elements using <xref:System.Numerics.Vector%601>.</span></span>

```csharp
double[] SimdVectorProd(double[] left, double[] right)
{
    var offset = Vector<double>.Count;
    double[] result = new double[left.Length];
    int i = 0;
    for (i = 0; i < left.Length; i += offset)
    {
        var v1 = new Vector<double>(left, i);
        var v2 = new Vector<double>(right, i);
        (v1 * v2).CopyTo(result, i);
    }

    //remaining items
    for (; i < left.Length; ++i)
    {
        result[i] = left[i] * right[i];
    }

    return result;
}
```

## <a name="remarks"></a><span data-ttu-id="3b32f-137">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b32f-137">Remarks</span></span>

<span data-ttu-id="3b32f-138">O SIMD tem mais probabilidade de remover um afunilamento e expor o próximo, por exemplo, a taxa de transferência de memória.</span><span class="sxs-lookup"><span data-stu-id="3b32f-138">SIMD is more likely to remove one bottleneck and expose the next, for example memory throughput.</span></span> <span data-ttu-id="3b32f-139">Em geral, o benefício de desempenho do uso de SIMD varia dependendo do cenário específico e, em alguns casos, ele pode até mesmo executar pior do que um código equivalente não-SIMD mais simples.</span><span class="sxs-lookup"><span data-stu-id="3b32f-139">In general the performance benefit of using SIMD varies depending on the specific scenario, and in some cases it can even perform worse than simpler non-SIMD equivalent code.</span></span>
