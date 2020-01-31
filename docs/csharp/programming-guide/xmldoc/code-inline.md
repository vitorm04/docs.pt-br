---
title: Guia de C# programação de <c>
ms.date: 07/20/2015
f1_keywords:
- c
- <c>
helpviewer_keywords:
- text, marking as code [C#]
- code, marking text as [C#]
- c C# XML tag
- <c> C# XML tag
ms.assetid: aad5b16e-a29e-445e-bd0d-eea0b138d7b2
ms.openlocfilehash: d5b28ee6db52d191f8454592d792ac0a1e1dc73b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793449"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="1783f-102">\<c > (C# guia de programação)</span><span class="sxs-lookup"><span data-stu-id="1783f-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="1783f-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1783f-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="1783f-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1783f-104">Parameters</span></span>

- `text`

  <span data-ttu-id="1783f-105">O texto que você deseja indicar como código.</span><span class="sxs-lookup"><span data-stu-id="1783f-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="1783f-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="1783f-106">Remarks</span></span>

<span data-ttu-id="1783f-107">A marca \<c> oferece uma maneira de indicar que o texto em uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="1783f-107">The \<c> tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="1783f-108">Use [\<code>](./code.md) para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="1783f-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="1783f-109">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="1783f-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="1783f-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1783f-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="1783f-111">Veja também</span><span class="sxs-lookup"><span data-stu-id="1783f-111">See also</span></span>

- [<span data-ttu-id="1783f-112">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="1783f-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="1783f-113">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="1783f-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
