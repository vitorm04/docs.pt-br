---
title: '##error – Referência de C#'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 3aa31ce7e189684bd60c238905df3bcbd1818ed6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559327"
---
# <a name="error-c-reference"></a><span data-ttu-id="50ccc-102">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="50ccc-102">#error (C# Reference)</span></span>
<span data-ttu-id="50ccc-103">`#error` permite gerar um erro definido pelo usuário [CS1029](../compiler-messages/cs1029.md) de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="50ccc-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="50ccc-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="50ccc-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="50ccc-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="50ccc-105">Remarks</span></span>  
 <span data-ttu-id="50ccc-106">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="50ccc-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="50ccc-107">Também é possível gerar um aviso definido pelo usuário com [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="50ccc-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50ccc-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="50ccc-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="50ccc-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="50ccc-109">See also</span></span>

- [<span data-ttu-id="50ccc-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="50ccc-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="50ccc-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="50ccc-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="50ccc-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="50ccc-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
