---
title: '#undef (Referência de C#)'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 3957d58f61e51fab01618f5e1146be9cd0da58fd
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44269287"
---
# <a name="undef-c-reference"></a><span data-ttu-id="34d3d-102">#undef (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="34d3d-102">#undef (C# Reference)</span></span>
<span data-ttu-id="34d3d-103">`#undef` permite excluir as definições de um símbolo, de modo que, usando o símbolo como a expressão em uma diretiva [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), a expressão será avaliada como `false`.</span><span class="sxs-lookup"><span data-stu-id="34d3d-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="34d3d-104">Um símbolo pode ser definido com a diretiva [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) ou com a opção do compilador [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="34d3d-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="34d3d-105">A diretiva `#undef` deve ser exibida no arquivo antes de usar qualquer instrução que também não sejam diretivas.</span><span class="sxs-lookup"><span data-stu-id="34d3d-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="34d3d-106">Exemplo</span><span class="sxs-lookup"><span data-stu-id="34d3d-106">Example</span></span>  

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

<span data-ttu-id="34d3d-107">**DEBUG não está definido**</span><span class="sxs-lookup"><span data-stu-id="34d3d-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="34d3d-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="34d3d-108">See Also</span></span>

- [<span data-ttu-id="34d3d-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="34d3d-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="34d3d-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="34d3d-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="34d3d-111">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="34d3d-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
