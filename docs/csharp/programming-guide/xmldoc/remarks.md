---
title: <remarks> - Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- remarks
- <remarks>
helpviewer_keywords:
- remarks C# XML tag
- <remarks> C# XML tag
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
ms.openlocfilehash: e37dac9cb9fed1df6ca027f09f2c95dbbc8ea66d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793381"
---
# <a name="remarks-c-programming-guide"></a><span data-ttu-id="2da78-102">\<observações> (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="2da78-102">\<remarks> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="2da78-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2da78-103">Syntax</span></span>

```xml
<remarks>description</remarks>
```

## <a name="parameters"></a><span data-ttu-id="2da78-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="2da78-104">Parameters</span></span>

- `Description`

  <span data-ttu-id="2da78-105">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="2da78-105">A description of the member.</span></span>

## <a name="remarks"></a><span data-ttu-id="2da78-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="2da78-106">Remarks</span></span>

<span data-ttu-id="2da78-107">As \<observações> tag é usada para adicionar informações sobre [ \< ](./summary.md)um tipo, complementando as informações especificadas com>de resumo .</span><span class="sxs-lookup"><span data-stu-id="2da78-107">The \<remarks> tag is used to add information about a type, supplementing the information specified with [\<summary>](./summary.md).</span></span> <span data-ttu-id="2da78-108">Essas informações são exibidas na janela do Pesquisador de Objetos.</span><span class="sxs-lookup"><span data-stu-id="2da78-108">This information is displayed in the Object Browser window.</span></span>

<span data-ttu-id="2da78-109">Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="2da78-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="2da78-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="2da78-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#9](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#9)]

## <a name="see-also"></a><span data-ttu-id="2da78-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="2da78-111">See also</span></span>

- [<span data-ttu-id="2da78-112">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="2da78-112">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2da78-113">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="2da78-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
