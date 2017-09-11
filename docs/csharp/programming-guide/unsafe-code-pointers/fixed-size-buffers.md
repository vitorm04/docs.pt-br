---
title: "Buffers de tamanho fixo (Guia de Programação em C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- fixed size buffers [C#]
- unsafe buffers [C#]
- unsafe code [C#], fixed size buffers
ms.assetid: 6220d454-947c-4977-ac9d-9308c6ed5051
caps.latest.revision: 31
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: e1a3dcf953cb56fc3436fdd5e7ecb60478a12922
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="fixed-size-buffers-c-programming-guide"></a><span data-ttu-id="8d8b1-102">Buffers de tamanho fixo (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="8d8b1-102">Fixed Size Buffers (C# Programming Guide)</span></span>
<span data-ttu-id="8d8b1-103">No C#, você pode usar a instrução [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) para criar um buffer com uma matriz de tamanho fixo em uma estrutura de dados.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-103">In C#, you can use the [fixed](../../../csharp/language-reference/keywords/fixed-statement.md) statement to create a buffer with a fixed size array in a data structure.</span></span> <span data-ttu-id="8d8b1-104">Isso é útil quando você está trabalhando com o código existente, como código escrito em outras linguagens, DLLs preexistentes ou projetos COM.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-104">This is useful when you are working with existing code, such as code written in other languages, pre-existing DLLs or COM projects.</span></span> <span data-ttu-id="8d8b1-105">A matriz fixa pode usar qualquer atributo ou modificador que for permitido para membros de struct regulares.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-105">The fixed array can take any attributes or modifiers that are allowed for regular struct members.</span></span> <span data-ttu-id="8d8b1-106">A única restrição é que o tipo da matriz deve ser `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float` ou `double`.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-106">The only restriction is that the array type must be `bool`, `byte`, `char`, `short`, `int`, `long`, `sbyte`, `ushort`, `uint`, `ulong`, `float`, or `double`.</span></span>  
  
```  
private fixed char name[30];  
```  
  
## <a name="remarks"></a><span data-ttu-id="8d8b1-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8d8b1-107">Remarks</span></span>  
 <span data-ttu-id="8d8b1-108">Em versões anteriores do C#, declarar uma estrutura de tamanho fixo no estilo do C++ era difícil porque um struct C# que contém uma matriz não contém os elementos da matriz.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-108">In early versions of C#, declaring a C++ style fixed-size structure was difficult because a C# struct that contains an array does not contain the array elements.</span></span> <span data-ttu-id="8d8b1-109">Em vez disso, o struct contém uma referência aos elementos.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-109">Instead, the struct contains a reference to the elements.</span></span>  
  
 <span data-ttu-id="8d8b1-110">O C# 2.0 adicionou a capacidade de inserir uma matriz de tamanho fixo em um [struct](../../../csharp/language-reference/keywords/struct.md) quando ele é usado em um bloco de código [não seguro](../../../csharp/language-reference/keywords/unsafe.md).</span><span class="sxs-lookup"><span data-stu-id="8d8b1-110">C# 2.0 added the ability to embed an array of fixed size in a [struct](../../../csharp/language-reference/keywords/struct.md) when it is used in an [unsafe](../../../csharp/language-reference/keywords/unsafe.md) code block.</span></span>  
  
 <span data-ttu-id="8d8b1-111">Por exemplo, antes do C# 2.0, o seguinte `struct` teria um tamanho de 8 bytes.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-111">For example, before C# 2.0, the following `struct` would be 8 bytes in size.</span></span> <span data-ttu-id="8d8b1-112">A matriz `pathName` é uma referência à matriz alocada em heap:</span><span class="sxs-lookup"><span data-stu-id="8d8b1-112">The `pathName` array is a reference to the heap-allocated array:</span></span>  
  
 <span data-ttu-id="8d8b1-113">[!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="8d8b1-113">[!code-cs[csProgGuidePointers#19](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_1.cs)]</span></span>  
  
 <span data-ttu-id="8d8b1-114">A partir do C# 2.0, um `struct` pode conter uma matriz inserida.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-114">Beginning with C# 2.0, a `struct` can contain an embedded array.</span></span> <span data-ttu-id="8d8b1-115">No exemplo a seguir, a matriz `fixedBuffer` tem tamanho fixo.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-115">In the following example, the `fixedBuffer` array has a fixed size.</span></span> <span data-ttu-id="8d8b1-116">Para acessar os elementos da matriz, você deve usar uma instrução `fixed` para estabelecer um ponteiro para o primeiro elemento.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-116">To access the elements of the array, you use a `fixed` statement to establish a pointer to the first element.</span></span> <span data-ttu-id="8d8b1-117">A instrução `fixed` fixa uma instância de `fixedBuffer` a um local específico na memória.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-117">The `fixed` statement pins an instance of `fixedBuffer` to a specific location in memory.</span></span>  
  
 <span data-ttu-id="8d8b1-118">[!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="8d8b1-118">[!code-cs[csProgGuidePointers#20](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/fixed-size-buffers_2.cs)]</span></span>  
  
 <span data-ttu-id="8d8b1-119">O tamanho da matriz `char` de 128 elementos é 256 bytes.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-119">The size of the 128 element `char` array is 256 bytes.</span></span> <span data-ttu-id="8d8b1-120">Buffers de [char](../../../csharp/language-reference/keywords/char.md) de tamanho fixo sempre têm dois bytes por caractere, independentemente da codificação.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-120">Fixed size [char](../../../csharp/language-reference/keywords/char.md) buffers always take two bytes per character, regardless of the encoding.</span></span> <span data-ttu-id="8d8b1-121">Isso vale mesmo quando os buffers de char passam por marshaling para structs ou métodos de API com `CharSet = CharSet.Auto` ou `CharSet = CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-121">This is true even when char buffers are marshaled to API methods or structs with `CharSet = CharSet.Auto` or `CharSet = CharSet.Ansi`.</span></span> <span data-ttu-id="8d8b1-122">Para obter mais informações, consulte <xref:System.Runtime.InteropServices.CharSet>.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-122">For more information, see <xref:System.Runtime.InteropServices.CharSet>.</span></span>  
  
 <span data-ttu-id="8d8b1-123">Outra matriz de tamanho fixo comum é a matriz [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="8d8b1-123">Another common fixed-size array is the [bool](../../../csharp/language-reference/keywords/bool.md) array.</span></span> <span data-ttu-id="8d8b1-124">Os elementos em uma matriz `bool` sempre têm um byte de tamanho.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-124">The elements in a `bool` array are always one byte in size.</span></span> <span data-ttu-id="8d8b1-125">Matrizes `bool` não são adequadas para criar buffers ou matrizes de bits.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-125">`bool` arrays are not appropriate for creating bit arrays or buffers.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8d8b1-126">Exceto pela memória criada usando [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), o compilador C# e o CLR (Common Language Runtime) não executam nenhuma verificação de estouro de buffer de segurança.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-126">Except for memory created by using [stackalloc](../../../csharp/language-reference/keywords/stackalloc.md), the C# compiler and the common language runtime (CLR) do not perform any security buffer overrun checks.</span></span> <span data-ttu-id="8d8b1-127">Assim como acontece com qualquer código não seguro, tenha cuidado.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-127">As with all unsafe code, use caution.</span></span>  
  
 <span data-ttu-id="8d8b1-128">Buffers não seguros diferem de matrizes regulares das seguintes maneiras:</span><span class="sxs-lookup"><span data-stu-id="8d8b1-128">Unsafe buffers differ from regular arrays in the following ways:</span></span>  
  
-   <span data-ttu-id="8d8b1-129">Você só pode usar buffers não seguros em um contexto não seguro.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-129">You can only use unsafe buffers in an unsafe context.</span></span>  
  
-   <span data-ttu-id="8d8b1-130">Buffers não seguros sempre são vetores ou matrizes unidimensionais.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-130">Unsafe buffers are always vectors, or one-dimensional arrays.</span></span>  
  
-   <span data-ttu-id="8d8b1-131">A declaração de matriz deve incluir uma contagem, como `char id[8]`.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-131">The declaration of the array should include a count, such as `char id[8]`.</span></span> <span data-ttu-id="8d8b1-132">Não é possível usar `char id[]`.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-132">You cannot use `char id[]` instead.</span></span>  
  
-   <span data-ttu-id="8d8b1-133">Buffers não seguros só podem ser structs ou campos de instância em um contexto não seguro.</span><span class="sxs-lookup"><span data-stu-id="8d8b1-133">Unsafe buffers can only be instance fields of structs in an unsafe context.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8d8b1-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8d8b1-134">See Also</span></span>  
 <span data-ttu-id="8d8b1-135">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="8d8b1-135">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="8d8b1-136">[Código Não Seguro e Ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span><span class="sxs-lookup"><span data-stu-id="8d8b1-136">[Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md) </span></span>  
 <span data-ttu-id="8d8b1-137">[Instrução fixed](../../../csharp/language-reference/keywords/fixed-statement.md) </span><span class="sxs-lookup"><span data-stu-id="8d8b1-137">[fixed Statement](../../../csharp/language-reference/keywords/fixed-statement.md) </span></span>  
 [<span data-ttu-id="8d8b1-138">Interoperabilidade</span><span class="sxs-lookup"><span data-stu-id="8d8b1-138">Interoperability</span></span>](../../../csharp/programming-guide/interop/index.md)

