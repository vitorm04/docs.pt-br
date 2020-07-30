---
title: <typeparamref>-Guia de programação C#
description: Saiba mais sobre a <typeparamref> marca XML. Essa marca permite que os consumidores do arquivo de documentação formatem a palavra de alguma forma distinta, por exemplo, em itálico.
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: a39e896f1242452c7bcc94faa1e7ef3086ae2149
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380716"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="6fd0d-104">\<typeparamref>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="6fd0d-104">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="6fd0d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6fd0d-105">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="6fd0d-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="6fd0d-106">Parameters</span></span>

- `name`

  <span data-ttu-id="6fd0d-107">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="6fd0d-107">The name of the type parameter.</span></span> <span data-ttu-id="6fd0d-108">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="6fd0d-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="6fd0d-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="6fd0d-109">Remarks</span></span>

<span data-ttu-id="6fd0d-110">Para obter mais informações sobre parâmetros de tipo em tipos e métodos genéricos, consulte [Genéricos](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="6fd0d-110">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="6fd0d-111">Use essa marca para habilitar os consumidores do arquivo de documentação a formatar a palavra de alguma forma distinta, por exemplo, em itálico.</span><span class="sxs-lookup"><span data-stu-id="6fd0d-111">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="6fd0d-112">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="6fd0d-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="6fd0d-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="6fd0d-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="6fd0d-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="6fd0d-114">See also</span></span>

- [<span data-ttu-id="6fd0d-115">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="6fd0d-115">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="6fd0d-116">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="6fd0d-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
