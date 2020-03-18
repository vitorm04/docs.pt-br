---
title: <paramref>- Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- paramref
- <paramref>
helpviewer_keywords:
- <paramref> C# XML tag
- paramref C# XML tag
ms.assetid: 756c24c1-f591-40e8-a838-559761539b0b
ms.openlocfilehash: 12df257271369dc7f0a5c066b712a8d8e6c38761
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793396"
---
# <a name="paramref-c-programming-guide"></a><span data-ttu-id="76669-102">\<mref> (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="76669-102">\<paramref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="76669-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="76669-103">Syntax</span></span>

```xml
<paramref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="76669-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="76669-104">Parameters</span></span>

- `name`

  <span data-ttu-id="76669-105">O nome do parâmetro ao qual você deseja se referir.</span><span class="sxs-lookup"><span data-stu-id="76669-105">The name of the parameter to refer to.</span></span> <span data-ttu-id="76669-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="76669-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="76669-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="76669-107">Remarks</span></span>

<span data-ttu-id="76669-108">A marca \<paramref> fornece uma maneira de indicar que uma palavra nos comentários do código, por exemplo, em um blogo \<summary> ou \<remarks> refere-se a um parâmetro.</span><span class="sxs-lookup"><span data-stu-id="76669-108">The \<paramref> tag gives you a way to indicate that a word in the code comments, for example in a \<summary> or \<remarks> block refers to a parameter.</span></span> <span data-ttu-id="76669-109">O arquivo XML pode ser processado para formatar essa palavra de alguma forma distinta, como com uma fonte em negrito ou itálico.</span><span class="sxs-lookup"><span data-stu-id="76669-109">The XML file can be processed to format this word in some distinct way, such as with a bold or italic font.</span></span>

<span data-ttu-id="76669-110">Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="76669-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="76669-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="76669-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#7)]

## <a name="see-also"></a><span data-ttu-id="76669-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="76669-112">See also</span></span>

- [<span data-ttu-id="76669-113">C# Guia de Programação</span><span class="sxs-lookup"><span data-stu-id="76669-113">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="76669-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="76669-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
