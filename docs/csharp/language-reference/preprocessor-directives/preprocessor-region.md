---
title: '#region – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 723a904d18955caceea9e0d485ab51f84366c66e
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715125"
---
# <a name="region-c-reference"></a><span data-ttu-id="a6c36-102">#region (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="a6c36-102">#region (C# Reference)</span></span>
<span data-ttu-id="a6c36-103">`#region` permite que você especifique um bloco de código que pode ser expandido ou recolhido ao usar o recurso de [estrutura de tópicos](/visualstudio/ide/outlining) do editor do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="a6c36-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="a6c36-104">Em arquivos de código mais longos, é conveniente recolher ou ocultar uma ou mais regiões para que você possa se concentrar na parte do arquivo que está trabalhando no momento.</span><span class="sxs-lookup"><span data-stu-id="a6c36-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="a6c36-105">O exemplo a seguir mostra como definir uma região:</span><span class="sxs-lookup"><span data-stu-id="a6c36-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="a6c36-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6c36-106">Remarks</span></span>  
 <span data-ttu-id="a6c36-107">Um bloco `#region` deverá ser encerrado com uma diretiva [#endregion](./preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="a6c36-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="a6c36-108">Um bloco `#region` não pode sobrepor um bloco [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="a6c36-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="a6c36-109">No entanto, um bloco `#region` pode ser aninhado em um bloco `#if` e um bloco `#if` pode ser aninhado em um bloco `#region`.</span><span class="sxs-lookup"><span data-stu-id="a6c36-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a6c36-110">Veja também</span><span class="sxs-lookup"><span data-stu-id="a6c36-110">See also</span></span>

- [<span data-ttu-id="a6c36-111">Referência de C#</span><span class="sxs-lookup"><span data-stu-id="a6c36-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a6c36-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="a6c36-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a6c36-113">Diretivas do pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="a6c36-113">C# Preprocessor Directives</span></span>](./index.md)
