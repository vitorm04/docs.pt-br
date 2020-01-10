---
title: '##error – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#error'
helpviewer_keywords:
- '#error directive [C#]'
ms.assetid: f2a7f3af-4cf9-4111-b369-70204d24b26b
ms.openlocfilehash: 7203e1271da66e78bfbd70717b0f5e536a7ebd86
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712514"
---
# <a name="error-c-reference"></a><span data-ttu-id="261db-102">#error (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="261db-102">#error (C# Reference)</span></span>
<span data-ttu-id="261db-103">`#error` permite gerar um erro definido pelo usuário [CS1029](../compiler-messages/cs1029.md) de um local específico em seu código.</span><span class="sxs-lookup"><span data-stu-id="261db-103">`#error` lets you generate a [CS1029](../compiler-messages/cs1029.md) user-defined error from a specific location in your code.</span></span> <span data-ttu-id="261db-104">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="261db-104">For example:</span></span>  
  
```csharp
#error Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="261db-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="261db-105">Remarks</span></span>  
 <span data-ttu-id="261db-106">Um uso comum de `#error` é em uma diretiva condicional.</span><span class="sxs-lookup"><span data-stu-id="261db-106">A common use of `#error` is in a conditional directive.</span></span>  
  
 <span data-ttu-id="261db-107">Também é possível gerar um aviso definido pelo usuário com [#warning](./preprocessor-warning.md).</span><span class="sxs-lookup"><span data-stu-id="261db-107">It is also possible to generate a user-defined warning with [#warning](./preprocessor-warning.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="261db-108">Exemplo</span><span class="sxs-lookup"><span data-stu-id="261db-108">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="261db-109">Veja também</span><span class="sxs-lookup"><span data-stu-id="261db-109">See also</span></span>

- [<span data-ttu-id="261db-110">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="261db-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="261db-111">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="261db-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="261db-112">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="261db-112">C# Preprocessor Directives</span></span>](./index.md)
