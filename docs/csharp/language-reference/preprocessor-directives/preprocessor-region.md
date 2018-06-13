---
title: '#region (Referência de C#)'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 88632b04ec8932e22f5bf7a23b8f0edf14d89f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274958"
---
# <a name="region-c-reference"></a><span data-ttu-id="9165d-102">#region (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="9165d-102">#region (C# Reference)</span></span>
<span data-ttu-id="9165d-103">`#region` permite que você especifique um bloco de código que pode ser expandido ou recolhido ao usar o recurso de [estrutura de tópicos](/visualstudio/ide/outlining) do editor do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="9165d-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="9165d-104">Em arquivos de código mais longos, é conveniente recolher ou ocultar uma ou mais regiões para que você possa se concentrar na parte do arquivo que está trabalhando no momento.</span><span class="sxs-lookup"><span data-stu-id="9165d-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="9165d-105">O exemplo a seguir mostra como definir uma região:</span><span class="sxs-lookup"><span data-stu-id="9165d-105">The following example shows how to define a region:</span></span>  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a><span data-ttu-id="9165d-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="9165d-106">Remarks</span></span>  
 <span data-ttu-id="9165d-107">Um bloco `#region` deverá ser encerrado com uma diretiva [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="9165d-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="9165d-108">Um bloco `#region` não pode sobrepor um bloco [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="9165d-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="9165d-109">No entanto, um bloco `#region` pode ser aninhado em um bloco `#if` e um bloco `#if` pode ser aninhado em um bloco `#region`.</span><span class="sxs-lookup"><span data-stu-id="9165d-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9165d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9165d-110">See Also</span></span>  
 [<span data-ttu-id="9165d-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="9165d-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9165d-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="9165d-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9165d-113">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="9165d-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
