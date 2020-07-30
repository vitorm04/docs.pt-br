---
title: <paramref>-Guia de programação C#
description: Saiba mais sobre a <paramref> marca XML. Essa marca fornece uma maneira de indicar que uma palavra no código é um parâmetro.
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 133f43abfaf349806404d6d37fb472e3145c51b7
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381834"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="bd224-104">\<paramref>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="bd224-104">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="bd224-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bd224-105">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="bd224-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="bd224-106">Parameters</span></span>

- `name`

  <span data-ttu-id="bd224-107">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="bd224-107">The name of the parameter to refer to.</span></span> <span data-ttu-id="bd224-108">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="bd224-108">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="bd224-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bd224-109">Remarks</span></span>

<span data-ttu-id="bd224-110">A `<paramref>` marca fornece uma maneira de indicar que uma palavra nos comentários do código, por exemplo, em um `<summary>` `<remarks>` bloco ou se refere a um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="bd224-110">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="bd224-111">O arquivo XML pode ser processado para formatar essa palavra de alguma forma distinta, como com uma fonte em negrito ou itálico.</span><span class="sxs-lookup"><span data-stu-id="bd224-111">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="bd224-112">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="bd224-112">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="bd224-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bd224-113">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="bd224-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="bd224-114">See also</span></span>

- [<span data-ttu-id="bd224-115">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="bd224-115">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="bd224-116">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="bd224-116">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
