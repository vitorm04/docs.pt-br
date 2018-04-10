---
title: '&lt;value&gt; (Guia de programação em C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9ea900c21c2c0477c626be5eff2403312d9e8609
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltvaluegt-c-programming-guide"></a><span data-ttu-id="e670a-102">&lt;value&gt; (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="e670a-102">&lt;value&gt; (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="e670a-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e670a-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e670a-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e670a-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="e670a-105">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="e670a-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="e670a-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="e670a-106">Remarks</span></span>  
 <span data-ttu-id="e670a-107">A marca \<value> permite descrever o valor que uma propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="e670a-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="e670a-108">Observe que quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento do Visual Studio .NET, ele adicionará uma marca [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="e670a-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="e670a-109">Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="e670a-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="e670a-110">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="e670a-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e670a-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="e670a-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/value_1.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="e670a-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e670a-112">See Also</span></span>  
 [<span data-ttu-id="e670a-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="e670a-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e670a-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="e670a-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
