---
title: <returns> - Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: 784d9effa589c962b8a2b982fd199f74309fb4dc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76789706"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="c42c6-102">\<retorna> (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="c42c6-102">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="c42c6-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c42c6-103">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="c42c6-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="c42c6-104">Parameters</span></span>

- `description`

  <span data-ttu-id="c42c6-105">Uma descrição do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="c42c6-105">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="c42c6-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="c42c6-106">Remarks</span></span>

<span data-ttu-id="c42c6-107">A marca \<returns> deve ser usada no comentário para uma declaração de método descrever o valor retornado.</span><span class="sxs-lookup"><span data-stu-id="c42c6-107">The \<returns> tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="c42c6-108">Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="c42c6-108">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="c42c6-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="c42c6-109">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="c42c6-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="c42c6-110">See also</span></span>

- [<span data-ttu-id="c42c6-111">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="c42c6-111">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="c42c6-112">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="c42c6-112">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
