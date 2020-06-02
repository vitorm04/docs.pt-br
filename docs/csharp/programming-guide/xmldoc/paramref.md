---
title: <paramref>-Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 4f3b521d24c8b4677a05b0b145cb36c31b2793f2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287305"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="c68fb-102">\<paramref>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="c68fb-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c68fb-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c68fb-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="c68fb-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c68fb-104">Parameters</span></span>

- `name`

  <span data-ttu-id="c68fb-105">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="c68fb-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="c68fb-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="c68fb-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="c68fb-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="c68fb-107">Remarks</span></span>

<span data-ttu-id="c68fb-108">A `<paramref>` marca fornece uma maneira de indicar que uma palavra nos comentários do código, por exemplo, em um `<summary>` `<remarks>` bloco ou se refere a um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="c68fb-108">The `<paramref>` tag gives you a way to indicate that a word in the code comments, for example in a `<summary>` or `<remarks>` block refers to a parameter.</span></span> <span data-ttu-id="c68fb-109">O arquivo XML pode ser processado para formatar essa palavra de alguma forma distinta, como com uma fonte em negrito ou itálico.</span><span class="sxs-lookup"><span data-stu-id="c68fb-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="c68fb-110">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c68fb-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c68fb-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c68fb-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="c68fb-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="c68fb-112">See also</span></span>

- [<span data-ttu-id="c68fb-113">Guia de programação C#</span><span class="sxs-lookup"><span data-stu-id="c68fb-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c68fb-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="c68fb-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
