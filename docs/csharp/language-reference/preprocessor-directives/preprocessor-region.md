---
description: '#region – Referência de C#'
title: '#region – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: dcb806a213bea9d7c782eeddc712f1eb76257e80
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/24/2020
ms.locfileid: "91186400"
---
# <a name="region-c-reference"></a><span data-ttu-id="32c40-103">#region (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="32c40-103">#region (C# Reference)</span></span>

<span data-ttu-id="32c40-104">`#region` permite especificar um bloco de código que você pode expandir ou recolher ao usar o recurso de [estrutura de tópicos](/visualstudio/ide/outlining) do editor de códigos.</span><span class="sxs-lookup"><span data-stu-id="32c40-104">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the code editor.</span></span> <span data-ttu-id="32c40-105">Em arquivos de código mais longos, é conveniente recolher ou ocultar uma ou mais regiões para que você possa se concentrar na parte do arquivo que está trabalhando no momento.</span><span class="sxs-lookup"><span data-stu-id="32c40-105">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="32c40-106">O exemplo a seguir mostra como definir uma região:</span><span class="sxs-lookup"><span data-stu-id="32c40-106">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="32c40-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="32c40-107">Remarks</span></span>  

 <span data-ttu-id="32c40-108">Um bloco `#region` deverá ser encerrado com uma diretiva [#endregion](./preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="32c40-108">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="32c40-109">Um bloco `#region` não pode sobrepor um bloco [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="32c40-109">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="32c40-110">No entanto, um bloco `#region` pode ser aninhado em um bloco `#if` e um bloco `#if` pode ser aninhado em um bloco `#region`.</span><span class="sxs-lookup"><span data-stu-id="32c40-110">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32c40-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="32c40-111">See also</span></span>

- [<span data-ttu-id="32c40-112">Referência do C#</span><span class="sxs-lookup"><span data-stu-id="32c40-112">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="32c40-113">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="32c40-113">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="32c40-114">Diretivas de pré-processador do C#</span><span class="sxs-lookup"><span data-stu-id="32c40-114">C# Preprocessor Directives</span></span>](./index.md)
