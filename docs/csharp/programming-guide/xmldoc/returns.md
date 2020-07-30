---
title: <returns> -Guia de programação C#
description: Saiba mais sobre o XML <returns> Tags. Essa marca é usada no comentário para uma declaração de método para descrever o valor de retorno.
ms.date: 07/20/2015
f1_keywords:
- returns
- <returns>
helpviewer_keywords:
- <returns> C# XML tag
- returns C# XML tag
ms.assetid: bb2d9958-62fc-47c7-9511-6311171f119f
ms.openlocfilehash: e461d46df619a351048ae7942e59847d39e490f9
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381392"
---
# <a name="returns-c-programming-guide"></a><span data-ttu-id="87269-105">\<returns>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="87269-105">\<returns> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="87269-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="87269-106">Syntax</span></span>

```xml
<returns>description</returns>
```

## <a name="parameters"></a><span data-ttu-id="87269-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="87269-107">Parameters</span></span>

- `description`

  <span data-ttu-id="87269-108">Uma descrição do valor retornado.</span><span class="sxs-lookup"><span data-stu-id="87269-108">A description of the return value.</span></span>

## <a name="remarks"></a><span data-ttu-id="87269-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="87269-109">Remarks</span></span>

<span data-ttu-id="87269-110">A `<returns>` marca deve ser usada no comentário para uma declaração de método para descrever o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="87269-110">The `<returns>` tag should be used in the comment for a method declaration to describe the return value.</span></span>

<span data-ttu-id="87269-111">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="87269-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="87269-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="87269-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#10](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#10)]

## <a name="see-also"></a><span data-ttu-id="87269-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="87269-113">See also</span></span>

- [<span data-ttu-id="87269-114">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="87269-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="87269-115">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="87269-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
