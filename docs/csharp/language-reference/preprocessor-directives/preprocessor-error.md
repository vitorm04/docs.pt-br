---
title: '#error (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: ed43c1f85142ec6c54e44db5e3b0b7de3ef36bb8
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44259868"
---
# <a name="error-c-reference"></a><span data-ttu-id="48c47-102">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="48c47-102">#error (C# Reference)</span></span>
<span data-ttu-id="48c47-103">`#error` permite gerar um erro definido pelo usuário [CS1029](../compiler-messages/cs1029.md) de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="48c47-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="48c47-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="48c47-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="48c47-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="48c47-105">Remarks</span></span>  
 <span data-ttu-id="48c47-106">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="48c47-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="48c47-107">Também é possível gerar um aviso definido pelo usuário com [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="48c47-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="48c47-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="48c47-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="48c47-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48c47-109">See Also</span></span>

- [<span data-ttu-id="48c47-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="48c47-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="48c47-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="48c47-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="48c47-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="48c47-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
