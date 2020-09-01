---
description: '##error – Referência de C#'
title: '##error – Referência de C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 76325901c5e39f340545b186a0aa9546cd853ff8
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138092"
---
# <a name="error-c-reference"></a><span data-ttu-id="b65c9-103">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b65c9-103">#error (C# Reference)</span></span>

<span data-ttu-id="b65c9-104">`#error` permite gerar um erro definido pelo usuário [CS1029](../compiler-messages/cs1029.md) de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="b65c9-104">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="b65c9-105">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b65c9-105">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="b65c9-106">O compilador trata `#error version` de forma especial e relata um erro de compilador, CS8304, com uma mensagem contendo o compilador e as versões de linguagem usadas.</span><span class="sxs-lookup"><span data-stu-id="b65c9-106">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="b65c9-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="b65c9-107">Remarks</span></span>

<span data-ttu-id="b65c9-108">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="b65c9-108">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="b65c9-109">Também é possível gerar um aviso definido pelo usuário com [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="b65c9-109">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="b65c9-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b65c9-110">Example</span></span>

```csharp
// preprocessor_error.cs
// CS1029 expected
#define DEBUG
class MainClass
{
    static void Main()
    {
#if DEBUG
#error DEBUG is defined
#endif
    }
}
```

## <a name="see-also"></a><span data-ttu-id="b65c9-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="b65c9-111">See also</span></span>

- [<span data-ttu-id="b65c9-112">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="b65c9-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b65c9-113">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="b65c9-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b65c9-114">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="b65c9-114">C# Preprocessor Directives</span></span>](./index.md)
