---
title: Buffers de tamanho fixo – Guia de Programação em C#
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 5920dd125ded34969d60feb299568b56402056ab
ms.sourcegitcommit: 839777281a281684a7e2906dccb3acd7f6a32023
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/24/2020
ms.locfileid: "82140550"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="67b1e-102">Buffers de tamanho fixo (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="67b1e-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="67b1e-103">No C#, você pode usar a instrução [fixed](../../language-reference/keywords/fixed-statement.md) para criar um buffer com uma matriz de tamanho fixo em uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="67b1e-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="67b1e-104">Os buffers de tamanho fixo são úteis ao escrever métodos que interoperam com fontes de dados de outras linguagens ou plataformas.</span><span class="sxs-lookup"><span data-stu-id="67b1e-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="67b1e-105">A matriz fixa pode usar qualquer atributo ou modificador que for permitido para membros de struct regulares.</span><span class="sxs-lookup"><span data-stu-id="67b1e-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="67b1e-106">A única restrição é que o tipo da matriz deve ser `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="67b1e-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="67b1e-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="67b1e-107">Remarks</span></span>

<span data-ttu-id="67b1e-108">No código de seguro, um struct C# que contém uma matriz não contém os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="67b1e-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="67b1e-109">Em vez disso, o struct contém uma referência aos elementos.</span><span class="sxs-lookup"><span data-stu-id="67b1e-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="67b1e-110">Você pode inserir uma matriz de tamanho fixo em um [struct](../../language-reference/builtin-types/struct.md) quando ele é usado em um bloco de código [não seguro](../../language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="67b1e-110">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="67b1e-111">O tamanho dos itens `struct` a seguir não depende do número de elementos na matriz, pois `pathName` é uma referência:</span><span class="sxs-lookup"><span data-stu-id="67b1e-111">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="67b1e-112">Um `struct` pode conter uma matriz inserida em código não seguro.</span><span class="sxs-lookup"><span data-stu-id="67b1e-112">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="67b1e-113">No exemplo a seguir, a matriz `fixedBuffer` tem tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="67b1e-113">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="67b1e-114">É possível uma instrução `fixed` para estabelecer um ponteiro para o primeiro elemento.</span><span class="sxs-lookup"><span data-stu-id="67b1e-114">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="67b1e-115">Os elementos da matriz são acessados por este ponteiro.</span><span class="sxs-lookup"><span data-stu-id="67b1e-115">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="67b1e-116">A instrução `fixed` fixa o campo da instância `fixedBuffer` em um local específico na memória.</span><span class="sxs-lookup"><span data-stu-id="67b1e-116">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="67b1e-117">O tamanho da matriz `char` de 128 elementos é 256 bytes.</span><span class="sxs-lookup"><span data-stu-id="67b1e-117">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="67b1e-118">Buffers de [char](../../language-reference/builtin-types/char.md) de tamanho fixo sempre têm dois bytes por caractere, independentemente da codificação.</span><span class="sxs-lookup"><span data-stu-id="67b1e-118">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="67b1e-119">Isso vale mesmo quando os buffers de char passam por marshaling para structs ou métodos de API com `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="67b1e-119">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="67b1e-120">Para obter mais informações, consulte <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="67b1e-120">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="67b1e-121">O exemplo anterior demonstra o acesso a campos `fixed` sem fixação, que estão disponíveis a partir do C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="67b1e-121">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="67b1e-122">Outra matriz de tamanho fixo comum é a matriz [bool](../../language-reference/builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="67b1e-122">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="67b1e-123">Os elementos em uma matriz `bool` sempre têm um byte de tamanho.</span><span class="sxs-lookup"><span data-stu-id="67b1e-123">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="67b1e-124">Matrizes `bool` não são adequadas para criar buffers ou matrizes de bits.</span><span class="sxs-lookup"><span data-stu-id="67b1e-124">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="67b1e-125">Buffers de tamanho fixo são compilados <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>com o, que instrui o Common Language Runtime (CLR) de que um tipo contém uma matriz não gerenciada que potencialmente pode exceder.</span><span class="sxs-lookup"><span data-stu-id="67b1e-125">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="67b1e-126">Isso é semelhante à memória criada usando [stackalloc](../../language-reference/operators/stackalloc.md), que habilita automaticamente os recursos de detecção de saturação de buffer no CLR.</span><span class="sxs-lookup"><span data-stu-id="67b1e-126">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="67b1e-127">O exemplo anterior mostra como um buffer de tamanho fixo pode existir em `unsafe struct`um.</span><span class="sxs-lookup"><span data-stu-id="67b1e-127">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="67b1e-128">O compilador gerou C# para `Buffer`, é atribuído da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="67b1e-128">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

```csharp
internal struct Buffer
{
    [StructLayout(LayoutKind.Sequential, Size = 256)]
    [CompilerGenerated]
    [UnsafeValueType]
    public struct <fixedBuffer>e__FixedBuffer
    {
        public char FixedElementField;
    }

    [FixedBuffer(typeof(char), 128)]
    public <fixedBuffer>e__FixedBuffer fixedBuffer;
}
```

<span data-ttu-id="67b1e-129">Buffers de tamanho fixo diferem de matrizes regulares das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="67b1e-129">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="67b1e-130">Só pode ser usado em um contexto sem [segurança](../../language-reference/keywords/unsafe.md) .</span><span class="sxs-lookup"><span data-stu-id="67b1e-130">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="67b1e-131">Só podem ser campos de instância de structs.</span><span class="sxs-lookup"><span data-stu-id="67b1e-131">May only be instance fields of structs.</span></span>
- <span data-ttu-id="67b1e-132">Eles são sempre vetores ou matrizes unidimensionais.</span><span class="sxs-lookup"><span data-stu-id="67b1e-132">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="67b1e-133">A declaração deve incluir o comprimento, como `fixed char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="67b1e-133">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="67b1e-134">Não é possível usar `fixed char id[]`.</span><span class="sxs-lookup"><span data-stu-id="67b1e-134">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="67b1e-135">Veja também</span><span class="sxs-lookup"><span data-stu-id="67b1e-135">See also</span></span>

- [<span data-ttu-id="67b1e-136">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="67b1e-136">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="67b1e-137">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="67b1e-137">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="67b1e-138">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="67b1e-138">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="67b1e-139">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="67b1e-139">Interoperability</span></span>](../interop/index.md)
