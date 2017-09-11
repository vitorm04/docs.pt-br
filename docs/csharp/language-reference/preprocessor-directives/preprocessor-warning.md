---
title: "#<a name=\"warning-c-reference\"></a>warning (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#warning'
dev_langs:
- CSharp
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
caps.latest.revision: 9
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 8630101a90bd6d4ed2036b495b254c9475531dc0
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="warning-c-reference"></a><span data-ttu-id="5960c-102">#warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="5960c-102">#warning (C# Reference)</span></span>
<span data-ttu-id="5960c-103">O `#warning` permite gerar um aviso de um nível um em um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="5960c-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="5960c-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="5960c-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="5960c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="5960c-105">Remarks</span></span>  
 <span data-ttu-id="5960c-106">Um uso comum de `#warning` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="5960c-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="5960c-107">Também é possível gerar um erro definido pelo usuário com [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="5960c-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="5960c-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="5960c-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="5960c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5960c-109">See Also</span></span>  
 <span data-ttu-id="5960c-110">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="5960c-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="5960c-111">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="5960c-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="5960c-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="5960c-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

