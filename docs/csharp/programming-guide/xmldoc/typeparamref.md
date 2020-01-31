---
title: Guia de C# programação de <typeparamref>
ms.date: 07/20/2015
f1_keywords:
- typeparamref
helpviewer_keywords:
- typeparamref C# XML tag
- <typeparamref> C# XML tag
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
ms.openlocfilehash: 266eadad322fd3c4167c7a911cb57ef1e1333012
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789652"
---
# <a name="typeparamref-c-programming-guide"></a><span data-ttu-id="02b79-102">\<typeparamref > (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="02b79-102">\<typeparamref> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="02b79-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="02b79-103">Syntax</span></span>

```xml
<typeparamref name="name"/>
```

## <a name="parameters"></a><span data-ttu-id="02b79-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="02b79-104">Parameters</span></span>

- `name`

  <span data-ttu-id="02b79-105">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="02b79-105">The name of the type parameter.</span></span> <span data-ttu-id="02b79-106">Coloque o nome entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="02b79-106">Enclose the name in double quotation marks (" ").</span></span>

## <a name="remarks"></a><span data-ttu-id="02b79-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="02b79-107">Remarks</span></span>

<span data-ttu-id="02b79-108">Para obter mais informações sobre parâmetros de tipo em tipos e métodos genéricos, consulte [Genéricos](../generics/index.md).</span><span class="sxs-lookup"><span data-stu-id="02b79-108">For more information on type parameters in generic types and methods, see [Generics](../generics/index.md).</span></span>

<span data-ttu-id="02b79-109">Use essa marca para habilitar os consumidores do arquivo de documentação a formatar a palavra de alguma forma distinta, por exemplo, em itálico.</span><span class="sxs-lookup"><span data-stu-id="02b79-109">Use this tag to enable consumers of the documentation file to format the word in some distinct way, for example in italics.</span></span>

<span data-ttu-id="02b79-110">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="02b79-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="02b79-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="02b79-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#13](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#13)]

## <a name="see-also"></a><span data-ttu-id="02b79-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="02b79-112">See also</span></span>

- [<span data-ttu-id="02b79-113">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="02b79-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="02b79-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="02b79-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
