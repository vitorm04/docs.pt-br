---
title: <remarks> – Guia de Programação em C#
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 3e6625c55a6f5c29fb55bff2eb87959f3237652e
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2019
ms.locfileid: "56975843"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="56551-102">\<remarks> (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="56551-102">\<remarks> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="56551-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="56551-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="56551-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="56551-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="56551-105">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="56551-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="56551-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="56551-106">Remarks</span></span>  
 <span data-ttu-id="56551-107">A marca \<remarks> é usada para adicionar informações sobre o tipo, complementando as informações especificadas com [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="56551-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](../../../csharp/programming-guide/xmldoc/summary.md).</span></span> <span data-ttu-id="56551-108">Essas informações são exibidas na janela do Pesquisador de Objetos.</span><span class="sxs-lookup"><span data-stu-id="56551-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="56551-109">Compile com [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="56551-109">Compile with [/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56551-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="56551-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="56551-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="56551-111">See also</span></span>

- [<span data-ttu-id="56551-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="56551-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="56551-113">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="56551-113">Recommended Tags for Documentation Comments</span></span>](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)
