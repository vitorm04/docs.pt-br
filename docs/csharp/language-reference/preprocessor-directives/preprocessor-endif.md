---
title: '#endif – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712540"
---
# <a name="endif-c-reference"></a><span data-ttu-id="7db3a-102">#endif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="7db3a-102">#endif (C# Reference)</span></span>
<span data-ttu-id="7db3a-103">O `#endif` especifica o final de uma diretiva condicional, que começou com a diretiva [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="7db3a-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="7db3a-104">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="7db3a-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="7db3a-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="7db3a-105">Remarks</span></span>  
 <span data-ttu-id="7db3a-106">Uma diretiva condicional, começando com uma diretiva `#if`, deve ser encerrada explicitamente com uma diretiva `#endif`.</span><span class="sxs-lookup"><span data-stu-id="7db3a-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="7db3a-107">Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#endif`.</span><span class="sxs-lookup"><span data-stu-id="7db3a-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7db3a-108">Confira também</span><span class="sxs-lookup"><span data-stu-id="7db3a-108">See also</span></span>

- [<span data-ttu-id="7db3a-109">C# Referência</span><span class="sxs-lookup"><span data-stu-id="7db3a-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7db3a-110">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="7db3a-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7db3a-111">C# Diretivas de pré-processador</span><span class="sxs-lookup"><span data-stu-id="7db3a-111">C# Preprocessor Directives</span></span>](./index.md)
