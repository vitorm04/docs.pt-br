---
title: <c>-Guia de programação C#
description: Saiba mais sobre a <c> marca XML. Esta marca marca um texto de linha única em uma descrição como código, enquanto <code>indicates multiple lines.
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
ms.openlocfilehash: 78e59e1df4b096782e0a97b6d12c21c843a1cb21
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87382016"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="09104-104">\<c>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="09104-104">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="09104-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09104-105">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="09104-106">parâmetros</span><span class="sxs-lookup"><span data-stu-id="09104-106">Parameters</span></span>

- `text`

  <span data-ttu-id="09104-107">O texto que você deseja indicar como código.</span><span class="sxs-lookup"><span data-stu-id="09104-107">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="09104-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="09104-108">Remarks</span></span>

<span data-ttu-id="09104-109">A `<c>` marca fornece uma maneira de indicar que o texto dentro de uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="09104-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="09104-110">Use [\<code>](./code.md) para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="09104-110">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="09104-111">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="09104-111">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="09104-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="09104-112">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="09104-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="09104-113">See also</span></span>

- [<span data-ttu-id="09104-114">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="09104-114">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="09104-115">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="09104-115">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
