---
title: Buffers de tamanho fixo (Guia de Programação em C#)
ms.date: 04/20/2018
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.openlocfilehash: 310c5eed5507f75239efc78b6132fbc91211d29e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33339586"
---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="b3c93-102">Buffers de tamanho fixo (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="b3c93-102">Fixed Size Buffers (C# Programming Guide)</span></span>

<span data-ttu-id="b3c93-103">No C#, você pode usar a instrução [fixed](../../language-reference/keywords/fixed-statement.md) para criar um buffer com uma matriz de tamanho fixo em uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="b3c93-103">In C#, you can use the [fixed](../../language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="b3c93-104">Os buffers de tamanho fixo são úteis ao escrever métodos que interoperam com fontes de dados de outras linguagens ou plataformas.</span><span class="sxs-lookup"><span data-stu-id="b3c93-104">Fixed size buffers are useful when you write methods that interop with data sources from other languages or platforms.</span></span> <span data-ttu-id="b3c93-105">A matriz fixa pode usar qualquer atributo ou modificador que for permitido para membros de struct regulares.</span><span class="sxs-lookup"><span data-stu-id="b3c93-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="b3c93-106">A única restrição é que o tipo da matriz deve ser `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="b3c93-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>

```csharp
private fixed char name[30];
```

## <a name="remarks"></a><span data-ttu-id="b3c93-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b3c93-107">Remarks</span></span>

<span data-ttu-id="b3c93-108">No código de seguro, um struct C# que contém uma matriz não contém os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="b3c93-108">In safe code, a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="b3c93-109">Em vez disso, o struct contém uma referência aos elementos.</span><span class="sxs-lookup"><span data-stu-id="b3c93-109">Instead, the struct contains a reference to the elements.</span></span> <span data-ttu-id="b3c93-110">Você pode inserir uma matriz de tamanho fixo em um [struct](../../language-reference/keywords/struct.md) quando ele é usado em um bloco de código [não seguro](../../language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="b3c93-110">You can embed an array of fixed size in a [struct](../../language-reference/keywords/struct.md) when it is used in an [unsafe](../../language-reference/keywords/unsafe.md) code block.</span></span>

<span data-ttu-id="b3c93-111">O seguinte `struct` tem 8 bytes de tamanho.</span><span class="sxs-lookup"><span data-stu-id="b3c93-111">The following `struct` is 8 bytes in size.</span></span> <span data-ttu-id="b3c93-112">A matriz `pathName` é uma referência:</span><span class="sxs-lookup"><span data-stu-id="b3c93-112">The `pathName` array is a reference:</span></span>

[!code-csharp[Struct with embedded array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#6)]

<span data-ttu-id="b3c93-113">Um `struct` pode conter uma matriz inserida em código não seguro.</span><span class="sxs-lookup"><span data-stu-id="b3c93-113">A `struct` can contain an embedded array in unsafe code.</span></span> <span data-ttu-id="b3c93-114">No exemplo a seguir, a matriz `fixedBuffer` tem tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="b3c93-114">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="b3c93-115">É possível uma instrução `fixed` para estabelecer um ponteiro para o primeiro elemento.</span><span class="sxs-lookup"><span data-stu-id="b3c93-115">You use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="b3c93-116">Os elementos da matriz são acessados por este ponteiro.</span><span class="sxs-lookup"><span data-stu-id="b3c93-116">You access the elements of the array through this pointer.</span></span> <span data-ttu-id="b3c93-117">A instrução `fixed` fixa o campo da instância `fixedBuffer` em um local específico na memória.</span><span class="sxs-lookup"><span data-stu-id="b3c93-117">The `fixed` statement pins the `fixedBuffer` instance field to a specific location in memory.</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#7)]

<span data-ttu-id="b3c93-118">O tamanho da matriz `char` de 128 elementos é 256 bytes.</span><span class="sxs-lookup"><span data-stu-id="b3c93-118">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="b3c93-119">Buffers de [char](../../language-reference/keywords/char.md) de tamanho fixo sempre têm dois bytes por caractere, independentemente da codificação.</span><span class="sxs-lookup"><span data-stu-id="b3c93-119">Fixed size [char](../../language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="b3c93-120">Isso vale mesmo quando os buffers de char passam por marshaling para structs ou métodos de API com `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="b3c93-120">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="b3c93-121">Para obter mais informações, consulte <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="b3c93-121">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>

<span data-ttu-id="b3c93-122">O exemplo anterior demonstra o acesso a campos `fixed` sem fixação, que estão disponíveis começando com o C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="b3c93-122">The  preceding example demonstrates accessing `fixed` fields without pinning, which is available starting with C# 7.3..</span></span>

<span data-ttu-id="b3c93-123">Outra matriz de tamanho fixo comum é a matriz [bool](../../language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="b3c93-123">Another common fixed-size array is the [bool](../../language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="b3c93-124">Os elementos em uma matriz `bool` sempre têm um byte de tamanho.</span><span class="sxs-lookup"><span data-stu-id="b3c93-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="b3c93-125">Matrizes `bool` não são adequadas para criar buffers ou matrizes de bits.</span><span class="sxs-lookup"><span data-stu-id="b3c93-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>

> [!NOTE]
> <span data-ttu-id="b3c93-126">Exceto pela memória criada usando [stackalloc](../../language-reference/keywords/stackalloc.md), o compilador C# e o CLR (Common Language Runtime) não executam nenhuma verificação de estouro de buffer de segurança.</span><span class="sxs-lookup"><span data-stu-id="b3c93-126">Except for memory created by using [stackalloc](../../language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="b3c93-127">Assim como acontece com qualquer código não seguro, tenha cuidado.</span><span class="sxs-lookup"><span data-stu-id="b3c93-127">As with all unsafe code, use caution.</span></span>

<span data-ttu-id="b3c93-128">Buffers não seguros diferem de matrizes regulares das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="b3c93-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>

- <span data-ttu-id="b3c93-129">Você só pode usar buffers não seguros em um contexto não seguro.</span><span class="sxs-lookup"><span data-stu-id="b3c93-129">You can only use unsafe buffers in an unsafe context.</span></span>
- <span data-ttu-id="b3c93-130">Buffers não seguros sempre são vetores ou matrizes unidimensionais.</span><span class="sxs-lookup"><span data-stu-id="b3c93-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>
- <span data-ttu-id="b3c93-131">A declaração de matriz deve incluir uma contagem, como `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="b3c93-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="b3c93-132">Não é possível usar `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="b3c93-132">You cannot use `char id[]`.</span></span>
- <span data-ttu-id="b3c93-133">Buffers não seguros só podem ser structs ou campos de instância em um contexto não seguro.</span><span class="sxs-lookup"><span data-stu-id="b3c93-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>

## <a name="see-also"></a><span data-ttu-id="b3c93-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3c93-134">See Also</span></span>

[<span data-ttu-id="b3c93-135">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b3c93-135">C# Programming Guide</span></span>](../index.md)  
[<span data-ttu-id="b3c93-136">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="b3c93-136">Unsafe Code and Pointers</span></span>](index.md)  
[<span data-ttu-id="b3c93-137">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="b3c93-137">fixed Statement</span></span>](../../language-reference/keywords/fixed-statement.md)  
[<span data-ttu-id="b3c93-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="b3c93-138">Interoperability</span></span>](../interop/index.md)
