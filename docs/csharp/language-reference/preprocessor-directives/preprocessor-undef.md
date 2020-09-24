---
description: '#undef – Referência de C#'
title: '#undef – Referência de C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 7db79be7ea9d8462e09b6ae874bf0ae7d265afe2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150551"
---
# <a name="undef-c-reference"></a><span data-ttu-id="b5246-103">#undef (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b5246-103">#undef (C# Reference)</span></span>

<span data-ttu-id="b5246-104">`#undef` permite excluir as definições de um símbolo, de modo que, usando o símbolo como a expressão em uma diretiva [#if](./preprocessor-if.md), a expressão será avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="b5246-104">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="b5246-105">Um símbolo pode ser definido com a diretiva [#define](./preprocessor-define.md) ou a opção [-definir](../compiler-options/define-compiler-option.md) compilador.</span><span class="sxs-lookup"><span data-stu-id="b5246-105">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="b5246-106">A diretiva `#undef` deve ser exibida no arquivo antes de usar qualquer instrução que também não sejam diretivas.</span><span class="sxs-lookup"><span data-stu-id="b5246-106">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b5246-107">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b5246-107">Example</span></span>  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

<span data-ttu-id="b5246-108">**DEBUG não está definido**</span><span class="sxs-lookup"><span data-stu-id="b5246-108">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="b5246-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="b5246-109">See also</span></span>

- [<span data-ttu-id="b5246-110">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="b5246-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="b5246-111">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="b5246-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="b5246-112">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="b5246-112">C# Preprocessor Directives</span></span>](./index.md)
