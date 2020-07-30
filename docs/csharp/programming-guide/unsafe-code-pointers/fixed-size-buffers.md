---
title: Buffers de tamanho fixo – Guia de Programação em C#
description: Saiba mais sobre buffers de tamanho fixo. Buffers de tamanho fixo são usados para escrever métodos que interoperam com fontes de dados de outras linguagens.
ms.date: 04/23/2020
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 1d4f5068121cdc98976954f2d99f4ac020c3b2a8
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381236"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="31b1b-104">Buffers de tamanho fixo (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="31b1b-104">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="31b1b-105">No C#, você pode usar a instrução [fixed](../../language-reference/keywords/fixed-statement.md) para criar um buffer com uma matriz de tamanho fixo em uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="31b1b-105">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="31b1b-106">Os buffers de tamanho fixo são úteis ao escrever métodos que interoperam com fontes de dados de outras linguagens ou plataformas.</span><span class="sxs-lookup"><span data-stu-id="31b1b-106">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="31b1b-107">A matriz fixa pode usar qualquer atributo ou modificador que for permitido para membros de struct regulares.</span><span class="sxs-lookup"><span data-stu-id="31b1b-107">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="31b1b-108">A única restrição é que o tipo da matriz deve ser `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="31b1b-108">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="31b1b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="31b1b-109">Remarks</span></span>

<span data-ttu-id="31b1b-110">No código de seguro, um struct C# que contém uma matriz não contém os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="31b1b-110">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="31b1b-111">Em vez disso, o struct contém uma referência aos elementos.</span><span class="sxs-lookup"><span data-stu-id="31b1b-111">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="31b1b-112">Você pode inserir uma matriz de tamanho fixo em um [struct](../../language-reference/builtin-types/struct.md) quando ele é usado em um bloco de código [não seguro](../../language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="31b1b-112">You can embed an array of fixed size in a [struct](../../language-reference/builtin-types/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="31b1b-113">O tamanho dos itens a seguir `struct` não depende do número de elementos na matriz, pois `pathName` é uma referência:</span><span class="sxs-lookup"><span data-stu-id="31b1b-113">Size of the following `struct` doesn't depend on the number of elements in the array, since `pathName` is a reference:</span></span>

[!code-csharp[Struct with embedded array](snippets/FixedKeywordExamples.cs#6)]

<span data-ttu-id="31b1b-114">Um `struct` pode conter uma matriz inserida em código não seguro.</span><span class="sxs-lookup"><span data-stu-id="31b1b-114">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="31b1b-115">No exemplo a seguir, a matriz `fixedBuffer` tem tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="31b1b-115">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="31b1b-116">É possível uma instrução `fixed` para estabelecer um ponteiro para o primeiro elemento.</span><span class="sxs-lookup"><span data-stu-id="31b1b-116">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="31b1b-117">Os elementos da matriz são acessados por este ponteiro.</span><span class="sxs-lookup"><span data-stu-id="31b1b-117">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="31b1b-118">A instrução `fixed` fixa o campo da instância `fixedBuffer` em um local específico na memória.</span><span class="sxs-lookup"><span data-stu-id="31b1b-118">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#7)]

<span data-ttu-id="31b1b-119">O tamanho da matriz `char` de 128 elementos é 256 bytes.</span><span class="sxs-lookup"><span data-stu-id="31b1b-119">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="31b1b-120">Buffers de [char](../../language-reference/builtin-types/char.md) de tamanho fixo sempre têm dois bytes por caractere, independentemente da codificação.</span><span class="sxs-lookup"><span data-stu-id="31b1b-120">Fixed size [char](../../language-reference/builtin-types/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="31b1b-121">Isso vale mesmo quando os buffers de char passam por marshaling para structs ou métodos de API com `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="31b1b-121">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="31b1b-122">Para obter mais informações, consulte <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="31b1b-122">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="31b1b-123">O exemplo anterior demonstra o acesso a campos `fixed` sem fixação, que estão disponíveis a partir do C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="31b1b-123">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3.</span></span>

<span data-ttu-id="31b1b-124">Outra matriz de tamanho fixo comum é a matriz [bool](../../language-reference/builtin-types/bool.md).</span><span class="sxs-lookup"><span data-stu-id="31b1b-124">Another common fixed-size array is the [bool](../../language-reference/builtin-types/bool.md) array.</span></span> <span data-ttu-id="31b1b-125">Os elementos em uma matriz `bool` sempre têm um byte de tamanho.</span><span class="sxs-lookup"><span data-stu-id="31b1b-125">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="31b1b-126">Matrizes `bool` não são adequadas para criar buffers ou matrizes de bits.</span><span class="sxs-lookup"><span data-stu-id="31b1b-126">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

<span data-ttu-id="31b1b-127">Buffers de tamanho fixo são compilados com o <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType> , que instrui o Common Language Runtime (CLR) de que um tipo contém uma matriz não gerenciada que potencialmente pode exceder.</span><span class="sxs-lookup"><span data-stu-id="31b1b-127">Fixed size buffers are compiled with the <xref:System.Runtime.CompilerServices.UnsafeValueTypeAttribute?displayProperty=nameWithType>, which instructs the common language runtime (CLR) that a type contains an unmanaged array that can potentially overflow.</span></span> <span data-ttu-id="31b1b-128">Isso é semelhante à memória criada usando [stackalloc](../../language-reference/operators/stackalloc.md), que habilita automaticamente os recursos de detecção de saturação de buffer no CLR.</span><span class="sxs-lookup"><span data-stu-id="31b1b-128">This is similar to memory created using [stackalloc](../../language-reference/operators/stackalloc.md), which automatically enables buffer overrun detection features in the CLR.</span></span> <span data-ttu-id="31b1b-129">O exemplo anterior mostra como um buffer de tamanho fixo pode existir em um `unsafe struct` .</span><span class="sxs-lookup"><span data-stu-id="31b1b-129">The previous example shows how a fixed size buffer could exist in an `unsafe struct`.</span></span>

```csharp
internal unsafe struct Buffer
{
    public fixed char fixedBuffer[128];
}
```

<span data-ttu-id="31b1b-130">O compilador gerou C# para `Buffer` , é atribuído da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="31b1b-130">The compiler generated C# for `Buffer`, is attributed as follows:</span></span>

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

<span data-ttu-id="31b1b-131">Buffers de tamanho fixo diferem de matrizes regulares das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="31b1b-131">Fixed size buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="31b1b-132">Só pode ser usado em um contexto sem [segurança](../../language-reference/keywords/unsafe.md) .</span><span class="sxs-lookup"><span data-stu-id="31b1b-132">May only be used in an [unsafe](../../language-reference/keywords/unsafe.md) context.</span></span>
- <span data-ttu-id="31b1b-133">Só podem ser campos de instância de structs.</span><span class="sxs-lookup"><span data-stu-id="31b1b-133">May only be instance fields of structs.</span></span>
- <span data-ttu-id="31b1b-134">Eles são sempre vetores ou matrizes unidimensionais.</span><span class="sxs-lookup"><span data-stu-id="31b1b-134">They're always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="31b1b-135">A declaração deve incluir o comprimento, como `fixed char id[8]` .</span><span class="sxs-lookup"><span data-stu-id="31b1b-135">The declaration should include the length, such as `fixed char id[8]`.</span></span> <span data-ttu-id="31b1b-136">Não é possível usar `fixed char id[]`.</span><span class="sxs-lookup"><span data-stu-id="31b1b-136">You cannot use `fixed char id[]`.</span></span>

## <a name="see-also"></a><span data-ttu-id="31b1b-137">Veja também</span><span class="sxs-lookup"><span data-stu-id="31b1b-137">See also</span></span>

- [<span data-ttu-id="31b1b-138">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="31b1b-138">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="31b1b-139">Código e ponteiros inseguros</span><span class="sxs-lookup"><span data-stu-id="31b1b-139">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="31b1b-140">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="31b1b-140">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="31b1b-141">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="31b1b-141">Interoperability</span></span>](../interop/index.md)
