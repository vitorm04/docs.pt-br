---
title: <remarks> -Guia de programação C#
description: Saiba mais sobre o XML <remarks> Tags. Essa marca é usada para adicionar informações sobre um tipo, complementando as informações especificadas com <summary>.
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: d38905d100e24158e7a1412f6be9f01a7ced2382
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381496"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="95421-106">\<remarks>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="95421-106">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="95421-107">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="95421-107">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="95421-108">parâmetros</span><span class="sxs-lookup"><span data-stu-id="95421-108">Parameters</span></span>

- `Description`

  <span data-ttu-id="95421-109">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="95421-109">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="95421-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="95421-110">Remarks</span></span>

<span data-ttu-id="95421-111">A `<remarks>` marca é usada para adicionar informações sobre um tipo, complementando as informações especificadas com [\<summary>](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="95421-111">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="95421-112">Essas informações são exibidas na janela do Pesquisador de Objetos.</span><span class="sxs-lookup"><span data-stu-id="95421-112">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="95421-113">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="95421-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="95421-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="95421-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="95421-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="95421-115">See also</span></span>

- [<span data-ttu-id="95421-116">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="95421-116">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="95421-117">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="95421-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
