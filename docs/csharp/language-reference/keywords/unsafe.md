---
description: Palavra-chave unsafe – Referência de C#
title: Palavra-chave unsafe – Referência de C#
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 2e047a4cff77877862c5cbbb5e49eb1a75b42499
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89141953"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="156d3-103">unsafe (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="156d3-103">unsafe (C# Reference)</span></span>

<span data-ttu-id="156d3-104">A palavra-chave `unsafe` denota um contexto inseguro, que é necessário para qualquer operação que envolva ponteiros.</span><span class="sxs-lookup"><span data-stu-id="156d3-104">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="156d3-105">Para obter mais informações, consulte [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="156d3-105">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="156d3-106">Você pode usar o modificador `unsafe` na declaração de um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="156d3-106">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="156d3-107">Toda a extensão textual do tipo ou membro é, portanto, considerada um contexto inseguro.</span><span class="sxs-lookup"><span data-stu-id="156d3-107">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="156d3-108">Por exemplo, a seguir está um método declarado com o modificador `unsafe`:</span><span class="sxs-lookup"><span data-stu-id="156d3-108">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="156d3-109">O escopo do contexto inseguro se estende da lista de parâmetros até o final do método, portanto, os ponteiros também podem ser usados na lista de parâmetros:</span><span class="sxs-lookup"><span data-stu-id="156d3-109">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="156d3-110">Você também pode usar um bloco não seguro para habilitar o uso de um código não seguro dentro desse bloco.</span><span class="sxs-lookup"><span data-stu-id="156d3-110">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="156d3-111">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="156d3-111">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="156d3-112">Para compilar código não seguro, você deve especificar a [`-unsafe`](../compiler-options/unsafe-compiler-option.md) opção do compilador.</span><span class="sxs-lookup"><span data-stu-id="156d3-112">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="156d3-113">O código não seguro não é verificável pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="156d3-113">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="156d3-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="156d3-114">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="156d3-115">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="156d3-115">C# language specification</span></span>

<span data-ttu-id="156d3-116">Para saber mais, confira [código unsafe](~/_csharplang/spec/unsafe-code.md) na [Especificação da Linguagem C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="156d3-116">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="156d3-117">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="156d3-117">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="156d3-118">Confira também</span><span class="sxs-lookup"><span data-stu-id="156d3-118">See also</span></span>

- [<span data-ttu-id="156d3-119">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="156d3-119">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="156d3-120">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="156d3-120">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="156d3-121">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="156d3-121">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="156d3-122">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="156d3-122">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="156d3-123">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="156d3-123">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="156d3-124">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="156d3-124">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
