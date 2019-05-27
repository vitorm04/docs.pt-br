---
title: Palavra-chave unsafe – Referência de C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: bca12c1dd8c79a5ae17e4a9b7b75d3c7b302fb89
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65875869"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="8962c-102">unsafe (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="8962c-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="8962c-103">A palavra-chave `unsafe` denota um contexto inseguro, que é necessário para qualquer operação que envolva ponteiros.</span><span class="sxs-lookup"><span data-stu-id="8962c-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="8962c-104">Para obter mais informações, consulte [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="8962c-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="8962c-105">Você pode usar o modificador `unsafe` na declaração de um tipo ou membro.</span><span class="sxs-lookup"><span data-stu-id="8962c-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="8962c-106">Toda a extensão textual do tipo ou membro é, portanto, considerada um contexto inseguro.</span><span class="sxs-lookup"><span data-stu-id="8962c-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="8962c-107">Por exemplo, a seguir está um método declarado com o modificador `unsafe`:</span><span class="sxs-lookup"><span data-stu-id="8962c-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="8962c-108">O escopo do contexto inseguro se estende da lista de parâmetros até o final do método, portanto, os ponteiros também podem ser usados na lista de parâmetros:</span><span class="sxs-lookup"><span data-stu-id="8962c-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="8962c-109">Você também pode usar um bloco não seguro para habilitar o uso de um código não seguro dentro desse bloco.</span><span class="sxs-lookup"><span data-stu-id="8962c-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="8962c-110">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="8962c-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="8962c-111">Para compilar o código não seguro, você deve especificar a opção do compilador [`-unsafe`](../compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="8962c-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="8962c-112">O código não seguro não é verificável pelo Common Language Runtime.</span><span class="sxs-lookup"><span data-stu-id="8962c-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="8962c-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8962c-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="8962c-114">Especificação da linguagem C#</span><span class="sxs-lookup"><span data-stu-id="8962c-114">C# language specification</span></span>

<span data-ttu-id="8962c-115">Para saber mais, confira [código unsafe](~/_csharplang/spec/unsafe-code.md) na [Especificação da Linguagem C#](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="8962c-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="8962c-116">A especificação da linguagem é a fonte definitiva para a sintaxe e o uso de C#.</span><span class="sxs-lookup"><span data-stu-id="8962c-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="8962c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8962c-117">See also</span></span>

- [<span data-ttu-id="8962c-118">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="8962c-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="8962c-119">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="8962c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="8962c-120">Palavras-chave do C#</span><span class="sxs-lookup"><span data-stu-id="8962c-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="8962c-121">Instrução fixed</span><span class="sxs-lookup"><span data-stu-id="8962c-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="8962c-122">Código não seguro e ponteiros</span><span class="sxs-lookup"><span data-stu-id="8962c-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="8962c-123">Buffers de tamanho fixo</span><span class="sxs-lookup"><span data-stu-id="8962c-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
