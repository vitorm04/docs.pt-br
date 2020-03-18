---
title: '##error – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 28e77304edee617adc1422e6a52d0a617cd9b3bb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173400"
---
# <a name="error-c-reference"></a><span data-ttu-id="f1dda-102">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="f1dda-102">#error (C# Reference)</span></span>
<span data-ttu-id="f1dda-103">`#error` permite gerar um erro definido pelo usuário [CS1029](../compiler-messages/cs1029.md) de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="f1dda-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="f1dda-104">Por exemplo: </span><span class="sxs-lookup"><span data-stu-id="f1dda-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="f1dda-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1dda-105">Remarks</span></span>  
 <span data-ttu-id="f1dda-106">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="f1dda-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="f1dda-107">Também é possível gerar um aviso definido pelo usuário com [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="f1dda-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1dda-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1dda-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f1dda-109">Confira também</span><span class="sxs-lookup"><span data-stu-id="f1dda-109">See also</span></span>

- [<span data-ttu-id="f1dda-110">C# Referência</span><span class="sxs-lookup"><span data-stu-id="f1dda-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f1dda-111">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="f1dda-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f1dda-112">C# Diretivas de pré-processador</span><span class="sxs-lookup"><span data-stu-id="f1dda-112">C# Preprocessor Directives</span></span>](./index.md)
