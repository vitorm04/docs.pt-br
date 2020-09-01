---
description: '#endif – Referência de C#'
title: '#endif – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 8068a6e437145178fd5c88763c86692a8700c349
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89138157"
---
# <a name="endif-c-reference"></a><span data-ttu-id="a670f-103">#endif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a670f-103">#endif (C# Reference)</span></span>
<span data-ttu-id="a670f-104">O `#endif` especifica o final de uma diretiva condicional, que começou com a diretiva [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="a670f-104">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="a670f-105">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="a670f-105">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="a670f-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a670f-106">Remarks</span></span>  
 <span data-ttu-id="a670f-107">Uma diretiva condicional, começando com uma diretiva `#if`, deve ser encerrada explicitamente com uma diretiva `#endif`.</span><span class="sxs-lookup"><span data-stu-id="a670f-107">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="a670f-108">Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#endif`.</span><span class="sxs-lookup"><span data-stu-id="a670f-108">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a670f-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="a670f-109">See also</span></span>

- [<span data-ttu-id="a670f-110">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="a670f-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a670f-111">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="a670f-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a670f-112">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="a670f-112">C# Preprocessor Directives</span></span>](./index.md)
