---
title: '##warning – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 3d09cd95ef4d53e3f11d9feb9675ebba22d6f857
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608516"
---
# <a name="warning-c-reference"></a><span data-ttu-id="fc2ff-102">#warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="fc2ff-102">#warning (C# Reference)</span></span>
<span data-ttu-id="fc2ff-103">`#warning` permite gerar um aviso do compilador [CS1030](../../misc/cs1030.md) de nível um de um local específico no código.</span><span class="sxs-lookup"><span data-stu-id="fc2ff-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="fc2ff-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="fc2ff-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="fc2ff-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="fc2ff-105">Remarks</span></span>
 <span data-ttu-id="fc2ff-106">Um uso comum de `#warning` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="fc2ff-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="fc2ff-107">Também é possível gerar um erro definido pelo usuário com [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="fc2ff-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="fc2ff-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fc2ff-108">Example</span></span>  

```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass
{  
    static void Main()
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  

## <a name="see-also"></a><span data-ttu-id="fc2ff-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fc2ff-109">See also</span></span>

- [<span data-ttu-id="fc2ff-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="fc2ff-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fc2ff-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="fc2ff-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fc2ff-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="fc2ff-112">C# Preprocessor Directives</span></span>](./index.md)
