---
title: '##warning – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715064"
---
# <a name="warning-c-reference"></a><span data-ttu-id="9151d-102">#warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9151d-102">#warning (C# Reference)</span></span>
<span data-ttu-id="9151d-103">`#warning` permite gerar um aviso do compilador [CS1030](../../misc/cs1030.md) de nível um de um local específico no código.</span><span class="sxs-lookup"><span data-stu-id="9151d-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="9151d-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="9151d-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="9151d-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="9151d-105">Remarks</span></span>
 <span data-ttu-id="9151d-106">Um uso comum de `#warning` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="9151d-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="9151d-107">Também é possível gerar um erro definido pelo usuário com [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="9151d-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9151d-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9151d-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="9151d-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="9151d-109">See also</span></span>

- [<span data-ttu-id="9151d-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="9151d-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9151d-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9151d-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9151d-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="9151d-112">C# Preprocessor Directives</span></span>](./index.md)
