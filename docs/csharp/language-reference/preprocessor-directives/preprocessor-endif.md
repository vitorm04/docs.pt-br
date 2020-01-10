---
title: '#endif – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712540"
---
# <a name="endif-c-reference"></a><span data-ttu-id="eff11-102">#endif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="eff11-102">#endif (C# Reference)</span></span>
<span data-ttu-id="eff11-103">O `#endif` especifica o final de uma diretiva condicional, que começou com a diretiva [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="eff11-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="eff11-104">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="eff11-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="eff11-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="eff11-105">Remarks</span></span>  
 <span data-ttu-id="eff11-106">Uma diretiva condicional, começando com uma diretiva `#if`, deve ser encerrada explicitamente com uma diretiva `#endif`.</span><span class="sxs-lookup"><span data-stu-id="eff11-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="eff11-107">Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#endif`.</span><span class="sxs-lookup"><span data-stu-id="eff11-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eff11-108">Veja também</span><span class="sxs-lookup"><span data-stu-id="eff11-108">See also</span></span>

- [<span data-ttu-id="eff11-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="eff11-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="eff11-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="eff11-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="eff11-111">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="eff11-111">C# Preprocessor Directives</span></span>](./index.md)
