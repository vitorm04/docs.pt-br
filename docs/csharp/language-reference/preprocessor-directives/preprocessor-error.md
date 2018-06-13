---
title: '#error (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 9ea4c24dcc3c0a4d39499bee5900cb9c6cc768c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269393"
---
# <a name="error-c-reference"></a><span data-ttu-id="bfd11-102">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="bfd11-102">#error (C# Reference)</span></span>
<span data-ttu-id="bfd11-103">O `#error` permite gerar um erro de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="bfd11-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="bfd11-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bfd11-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="bfd11-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="bfd11-105">Remarks</span></span>  
 <span data-ttu-id="bfd11-106">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="bfd11-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="bfd11-107">Também é possível gerar um aviso definido pelo usuário com [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="bfd11-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bfd11-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bfd11-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="bfd11-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bfd11-109">See Also</span></span>  
 [<span data-ttu-id="bfd11-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="bfd11-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="bfd11-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="bfd11-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bfd11-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="bfd11-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
