---
title: '##error – Referência de C#'
ms.date: 08/24/2020
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: cc1e0640886e3f3c1c74a54f64961a56c8b030e4
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812361"
---
# <a name="error-c-reference"></a><span data-ttu-id="223f0-102">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="223f0-102">#error (C# Reference)</span></span>

<span data-ttu-id="223f0-103">`#error` permite gerar um erro definido pelo usuário [CS1029](../compiler-messages/cs1029.md) de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="223f0-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="223f0-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="223f0-104">For example:</span></span>

```csharp
#error Deprecated code in this method.
```

> [!NOTE]
> <span data-ttu-id="223f0-105">O compilador trata `#error version` de forma especial e relata um erro de compilador, CS8304, com uma mensagem contendo o compilador e as versões de linguagem usadas.</span><span class="sxs-lookup"><span data-stu-id="223f0-105">The compiler treats `#error version` in a special way and reports a compiler error, CS8304, with a message containing the used compiler and language versions.</span></span>

## <a name="remarks"></a><span data-ttu-id="223f0-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="223f0-106">Remarks</span></span>

<span data-ttu-id="223f0-107">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="223f0-107">A common use of `#error` is in a conditional directive.</span></span>

<span data-ttu-id="223f0-108">Também é possível gerar um aviso definido pelo usuário com [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="223f0-108">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>

## <a name="example"></a><span data-ttu-id="223f0-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="223f0-109">Example</span></span>

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

## <a name="see-also"></a><span data-ttu-id="223f0-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="223f0-110">See also</span></span>

- [<span data-ttu-id="223f0-111">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="223f0-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="223f0-112">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="223f0-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="223f0-113">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="223f0-113">C# Preprocessor Directives</span></span>](./index.md)
