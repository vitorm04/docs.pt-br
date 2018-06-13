---
title: '#warning (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: c56458e0100c23450655e48b2abfb346e18e0bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268177"
---
# <a name="warning-c-reference"></a><span data-ttu-id="43835-102">#warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="43835-102">#warning (C# Reference)</span></span>
<span data-ttu-id="43835-103">O `#warning` permite gerar um aviso de um nível um em um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="43835-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="43835-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="43835-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="43835-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="43835-105">Remarks</span></span>  
 <span data-ttu-id="43835-106">Um uso comum de `#warning` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="43835-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="43835-107">Também é possível gerar um erro definido pelo usuário com [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="43835-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="43835-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="43835-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="43835-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="43835-109">See Also</span></span>  
 [<span data-ttu-id="43835-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="43835-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="43835-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="43835-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="43835-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="43835-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
