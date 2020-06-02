---
title: <remarks> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: 739027786e02e559d86f990bf614e261b497c76f
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287279"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="d0cfc-102">\<remarks>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="d0cfc-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="d0cfc-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d0cfc-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="d0cfc-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d0cfc-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="d0cfc-105">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="d0cfc-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="d0cfc-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="d0cfc-106">Remarks</span></span>

<span data-ttu-id="d0cfc-107">A `<remarks>` marca é usada para adicionar informações sobre um tipo, complementando as informações especificadas com [\<summary>](./summary.md) .</span><span class="sxs-lookup"><span data-stu-id="d0cfc-107">The `<remarks>` tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="d0cfc-108">Essas informações são exibidas na janela do Pesquisador de Objetos.</span><span class="sxs-lookup"><span data-stu-id="d0cfc-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="d0cfc-109">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="d0cfc-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="d0cfc-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="d0cfc-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="d0cfc-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="d0cfc-111">See also</span></span>

- [<span data-ttu-id="d0cfc-112">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="d0cfc-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d0cfc-113">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="d0cfc-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
