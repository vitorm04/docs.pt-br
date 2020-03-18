---
title: '#region – Referência de C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 48e8a6796c3b07b348fd988a9b8501ee496b8ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173387"
---
# <a name="region-c-reference"></a><span data-ttu-id="195bc-102">#region (Referência de C#)</span><span class="sxs-lookup"><span data-stu-id="195bc-102">#region (C# Reference)</span></span>
<span data-ttu-id="195bc-103">`#region` permite que você especifique um bloco de código que pode ser expandido ou recolhido ao usar o recurso de [estrutura de tópicos](/visualstudio/ide/outlining) do editor do Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="195bc-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="195bc-104">Em arquivos de código mais longos, é conveniente recolher ou ocultar uma ou mais regiões para que você possa se concentrar na parte do arquivo que está trabalhando no momento.</span><span class="sxs-lookup"><span data-stu-id="195bc-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="195bc-105">O exemplo a seguir mostra como definir uma região:</span><span class="sxs-lookup"><span data-stu-id="195bc-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="195bc-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="195bc-106">Remarks</span></span>  
 <span data-ttu-id="195bc-107">Um bloco `#region` deverá ser encerrado com uma diretiva [#endregion](./preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="195bc-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="195bc-108">Um bloco `#region` não pode sobrepor um bloco [#if](./preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="195bc-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="195bc-109">No entanto, um bloco `#region` pode ser aninhado em um bloco `#if` e um bloco `#if` pode ser aninhado em um bloco `#region`.</span><span class="sxs-lookup"><span data-stu-id="195bc-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195bc-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="195bc-110">See also</span></span>

- [<span data-ttu-id="195bc-111">C# Referência</span><span class="sxs-lookup"><span data-stu-id="195bc-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="195bc-112">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="195bc-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="195bc-113">C# Diretivas de pré-processador</span><span class="sxs-lookup"><span data-stu-id="195bc-113">C# Preprocessor Directives</span></span>](./index.md)
