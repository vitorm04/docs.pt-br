---
title: "#<a name=\"error-c-reference\"></a>error (Referência de C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#error'
dev_langs:
- CSharp
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
caps.latest.revision: 10
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
ms.openlocfilehash: d2d497d7b8345b94dfc77176bf2b0ca79674e9be
ms.contentlocale: pt-br
ms.lasthandoff: 07/28/2017

---
# <a name="error-c-reference"></a><span data-ttu-id="6ee2f-102">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="6ee2f-102">#error (C# Reference)</span></span>
<span data-ttu-id="6ee2f-103">O `#error` permite gerar um erro de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="6ee2f-103">`#error` lets you generate an error from a specific location in your code.</span></span> <span data-ttu-id="6ee2f-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="6ee2f-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="6ee2f-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="6ee2f-105">Remarks</span></span>  
 <span data-ttu-id="6ee2f-106">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="6ee2f-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="6ee2f-107">Também é possível gerar um aviso definido pelo usuário com [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="6ee2f-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ee2f-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6ee2f-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="6ee2f-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ee2f-109">See Also</span></span>  
 <span data-ttu-id="6ee2f-110">[Referência de C#](../../../csharp/language-reference/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ee2f-110">[C# Reference](../../../csharp/language-reference/index.md) </span></span>  
 <span data-ttu-id="6ee2f-111">[Guia de Programação em C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6ee2f-111">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 [<span data-ttu-id="6ee2f-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="6ee2f-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)

