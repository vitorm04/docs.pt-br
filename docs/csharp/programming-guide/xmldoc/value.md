---
title: <value> – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 3495a6c88d340342362d84d6ea3f12048d42b21f
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56982148"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="6bc92-102">\<value> (Guia de programação em C#)</span><span class="sxs-lookup"><span data-stu-id="6bc92-102">\<value> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="6bc92-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6bc92-103">Syntax</span></span>  
  
```xml  
<value>property-description</value>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6bc92-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6bc92-104">Parameters</span></span>  
 `property-description`  
 <span data-ttu-id="6bc92-105">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="6bc92-105">A description for the property.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6bc92-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="6bc92-106">Remarks</span></span>  
 <span data-ttu-id="6bc92-107">A marca \<value> permite descrever o valor que uma propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="6bc92-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="6bc92-108">Observe que quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento do Visual Studio .NET, ele adicionará uma marca [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="6bc92-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md) tag for the new property.</span></span> <span data-ttu-id="6bc92-109">Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="6bc92-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>  
  
 <span data-ttu-id="6bc92-110">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6bc92-110">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6bc92-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6bc92-111">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]  
  
## <a name="see-also"></a><span data-ttu-id="6bc92-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6bc92-112">See also</span></span>

- [<span data-ttu-id="6bc92-113">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="6bc92-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="6bc92-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="6bc92-114">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
