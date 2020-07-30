---
title: Como usar ponteiros para copiar uma matriz de bytes-guia de programação C#
description: Saiba como usar ponteiros para copiar uma matriz de bytes. Consulte um exemplo de código e recursos adicionais disponíveis.
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 70ab1441d25ea69afb2244bd94bd404a3e32838d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381782"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="18f45-104">Como usar ponteiros para copiar uma matriz de bytes (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="18f45-104">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="18f45-105">O exemplo a seguir usa ponteiros para copiar bytes de uma matriz para outra.</span><span class="sxs-lookup"><span data-stu-id="18f45-105">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="18f45-106">Este exemplo usa a palavra-chave [não seguro](../../language-reference/keywords/unsafe.md), que permite que você use ponteiros no método `Copy`.</span><span class="sxs-lookup"><span data-stu-id="18f45-106">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="18f45-107">A instrução [fixo](../../language-reference/keywords/fixed-statement.md) é usada para declarar ponteiros para as matrizes de origem e de destino.</span><span class="sxs-lookup"><span data-stu-id="18f45-107">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="18f45-108">A instrução `fixed`*fixa* o local das matrizes de origem e de destino na memória para que elas não sejam movidas pela coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="18f45-108">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="18f45-109">Os blocos de memória para as matrizes não serão fixado quando o bloco `fixed` for concluído.</span><span class="sxs-lookup"><span data-stu-id="18f45-109">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="18f45-110">Como o método `Copy` neste exemplo usa a palavra-chave `unsafe`, ele precisa ser compilado com a opção do compilador [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="18f45-110">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="18f45-111">Este exemplo acessa os elementos das duas matrizes usando índices em vez de um segundo ponteiro não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="18f45-111">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="18f45-112">A declaração dos ponteiros `pSource` e `pTarget` fixa as matrizes.</span><span class="sxs-lookup"><span data-stu-id="18f45-112">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="18f45-113">Esse recurso está disponível começando com o C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="18f45-113">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="18f45-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="18f45-114">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="18f45-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="18f45-115">See also</span></span>

- [<span data-ttu-id="18f45-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="18f45-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="18f45-117">Código e ponteiros inseguros</span><span class="sxs-lookup"><span data-stu-id="18f45-117">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="18f45-118">-Não seguro (opções do compilador C#)</span><span class="sxs-lookup"><span data-stu-id="18f45-118">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="18f45-119">Coleta de lixo</span><span class="sxs-lookup"><span data-stu-id="18f45-119">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
