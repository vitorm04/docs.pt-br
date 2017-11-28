---
title: "#<a name=\"error-c-reference\"></a>error (Referência de C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#error'
helpviewer_keywords: '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
caps.latest.revision: "10"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 23528ae81e4ddca23c67c937ca2588ab4c982e98
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="error-c-reference"></a><span data-ttu-id="e34bb-102">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="e34bb-102">#error (C# Reference)</span></span>
<span data-ttu-id="e34bb-103">O `#error` permite gerar um erro de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="e34bb-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="e34bb-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="e34bb-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="e34bb-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="e34bb-105">Remarks</span></span>  
 <span data-ttu-id="e34bb-106">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="e34bb-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="e34bb-107">Também é possível gerar um aviso definido pelo usuário com [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="e34bb-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="e34bb-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e34bb-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="e34bb-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e34bb-109">See Also</span></span>  
 [<span data-ttu-id="e34bb-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="e34bb-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e34bb-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e34bb-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e34bb-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="e34bb-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
