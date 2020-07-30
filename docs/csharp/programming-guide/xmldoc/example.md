---
title: <example> -Guia de programação C#
description: Saiba mais sobre o XML <example> Tags. Essa marca permite que você especifique um exemplo de como usar um método ou outro membro da biblioteca.
ms.date: 07/20/2015
f1_keywords:
- <example>
- example
helpviewer_keywords:
- <example> C# XML tag
- example C# XML tag
ms.assetid: 32d6e73b-2554-4abb-83ee-a1e321334fd2
ms.openlocfilehash: dd529e8f2a54cf9086d0d8c555dd1adb70b99126
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381522"
---
# <a name="example-c-programming-guide"></a><span data-ttu-id="a8225-105">\<example>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="a8225-105">\<example> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8225-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8225-106">Syntax</span></span>

```xml
<example>description</example>
```

## <a name="parameters"></a><span data-ttu-id="a8225-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8225-107">Parameters</span></span>

- `description`

  <span data-ttu-id="a8225-108">Uma descrição do exemplo de código.</span><span class="sxs-lookup"><span data-stu-id="a8225-108">A description of the code sample.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8225-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="a8225-109">Remarks</span></span>

<span data-ttu-id="a8225-110">A `<example>` marca permite especificar um exemplo de como usar um método ou outro membro da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="a8225-110">The `<example>` tag lets you specify an example of how to use a method or other library member.</span></span> <span data-ttu-id="a8225-111">Isso geralmente envolve o uso da [\<code>](./code.md) marca.</span><span class="sxs-lookup"><span data-stu-id="a8225-111">This commonly involves using the [\<code>](./code.md) tag.</span></span>

<span data-ttu-id="a8225-112">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="a8225-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="a8225-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="a8225-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#3)]

## <a name="see-also"></a><span data-ttu-id="a8225-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="a8225-114">See also</span></span>

- [<span data-ttu-id="a8225-115">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="a8225-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a8225-116">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="a8225-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
