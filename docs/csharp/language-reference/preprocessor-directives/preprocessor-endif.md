---
title: '#endif – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 74205c836b4eeb2d8b17b907bb13708f3225df08
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608575"
---
# <a name="endif-c-reference"></a><span data-ttu-id="d8f12-102">#endif (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="d8f12-102">#endif (C# Reference)</span></span>
<span data-ttu-id="d8f12-103">O `#endif` especifica o final de uma diretiva condicional, que começou com a diretiva [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="d8f12-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="d8f12-104">Por exemplo,</span><span class="sxs-lookup"><span data-stu-id="d8f12-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="d8f12-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="d8f12-105">Remarks</span></span>  
 <span data-ttu-id="d8f12-106">Uma diretiva condicional, começando com uma diretiva `#if`, deve ser encerrada explicitamente com uma diretiva `#endif`.</span><span class="sxs-lookup"><span data-stu-id="d8f12-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="d8f12-107">Consulte [#if](./preprocessor-if.md) para obter um exemplo de como usar `#endif`.</span><span class="sxs-lookup"><span data-stu-id="d8f12-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8f12-108">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d8f12-108">See also</span></span>

- [<span data-ttu-id="d8f12-109">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="d8f12-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d8f12-110">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="d8f12-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d8f12-111">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="d8f12-111">C# Preprocessor Directives</span></span>](./index.md)
