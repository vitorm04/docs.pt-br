---
title: '#undef – Referência de C#'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: fdf22e90be766e87e823a7f8cc27ea00c17d2bb5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605592"
---
# <a name="undef-c-reference"></a><span data-ttu-id="87d2b-102">#undef (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="87d2b-102">#undef (C# Reference)</span></span>
<span data-ttu-id="87d2b-103">`#undef` permite excluir as definições de um símbolo, de modo que, usando o símbolo como a expressão em uma diretiva [#if](./preprocessor-if.md), a expressão será avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="87d2b-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="87d2b-104">Um símbolo pode ser definido com a diretiva [#define](./preprocessor-define.md) ou com a opção do compilador [/define](../compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="87d2b-104">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="87d2b-105">A diretiva `#undef` deve ser exibida no arquivo antes de usar qualquer instrução que também não sejam diretivas.</span><span class="sxs-lookup"><span data-stu-id="87d2b-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="87d2b-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87d2b-106">Example</span></span>  

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

<span data-ttu-id="87d2b-107">**DEBUG não está definido**</span><span class="sxs-lookup"><span data-stu-id="87d2b-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="87d2b-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="87d2b-108">See also</span></span>

- [<span data-ttu-id="87d2b-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="87d2b-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="87d2b-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="87d2b-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="87d2b-111">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="87d2b-111">C# Preprocessor Directives</span></span>](./index.md)
