---
title: '#error (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: ed43c1f85142ec6c54e44db5e3b0b7de3ef36bb8
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935288"
---
# <a name="error-c-reference"></a><span data-ttu-id="3841c-102">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="3841c-102">#error (C# Reference)</span></span>
<span data-ttu-id="3841c-103">`#error` permite gerar um erro definido pelo usuário [CS1029](../compiler-messages/cs1029.md) de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="3841c-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="3841c-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="3841c-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="3841c-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="3841c-105">Remarks</span></span>  
 <span data-ttu-id="3841c-106">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="3841c-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="3841c-107">Também é possível gerar um aviso definido pelo usuário com [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="3841c-107">It is also possible to generate a user-defined warning with [#warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3841c-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="3841c-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3841c-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3841c-109">See Also</span></span>

- [<span data-ttu-id="3841c-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="3841c-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3841c-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="3841c-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3841c-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="3841c-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
