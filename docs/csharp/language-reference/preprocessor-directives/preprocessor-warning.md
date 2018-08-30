---
title: '#warning (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 59ca63d5089e377627a9116f24f9a0a1681bb4b2
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932671"
---
# <a name="warning-c-reference"></a><span data-ttu-id="b9ce0-102">#warning (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="b9ce0-102">#warning (C# Reference)</span></span>
<span data-ttu-id="b9ce0-103">`#warning` permite gerar um aviso do compilador [CS1030](../../misc/cs1030.md) de nível um de um local específico no código.</span><span class="sxs-lookup"><span data-stu-id="b9ce0-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="b9ce0-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b9ce0-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="b9ce0-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="b9ce0-105">Remarks</span></span>
 <span data-ttu-id="b9ce0-106">Um uso comum de `#warning` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="b9ce0-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="b9ce0-107">Também é possível gerar um erro definido pelo usuário com [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="b9ce0-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b9ce0-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="b9ce0-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="b9ce0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b9ce0-109">See Also</span></span>

- [<span data-ttu-id="b9ce0-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="b9ce0-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b9ce0-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="b9ce0-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b9ce0-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="b9ce0-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
