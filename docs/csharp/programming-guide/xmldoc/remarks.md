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
ms.openlocfilehash: 508201fed57fce93b64691de55dce45780adc13c
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523350"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="cb051-102">\<remarks> (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="cb051-102">\<remarks> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="cb051-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cb051-103">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
## <a name="parameters"></a><span data-ttu-id="cb051-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cb051-104">Parameters</span></span>  
 `Description`  
 <span data-ttu-id="cb051-105">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="cb051-105">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cb051-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="cb051-106">Remarks</span></span>  
 <span data-ttu-id="cb051-107">A marca \<remarks> é usada para adicionar informações sobre o tipo, complementando as informações especificadas com [\<summary>](./summary.md).</span><span class="sxs-lookup"><span data-stu-id="cb051-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="cb051-108">Essas informações são exibidas na janela do Pesquisador de Objetos.</span><span class="sxs-lookup"><span data-stu-id="cb051-108">This information is displayed in the Object Browser window.</span></span>  
  
 <span data-ttu-id="cb051-109">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="cb051-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb051-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="cb051-110">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]  
  
## <a name="see-also"></a><span data-ttu-id="cb051-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cb051-111">See also</span></span>

- [<span data-ttu-id="cb051-112">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="cb051-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cb051-113">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="cb051-113">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
