---
title: <c>-Guia de programação C#
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
ms.openlocfilehash: a09bcd069e2f85f4a21736cb218c42c0e481d70b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287461"
---
# <a name="c-c-programming-guide"></a><span data-ttu-id="4da83-102">\<c>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="4da83-102">\<c> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="4da83-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4da83-103">Syntax</span></span>

```xml
<c>text</c>
```

## <a name="parameters"></a><span data-ttu-id="4da83-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4da83-104">Parameters</span></span>

- `text`

  <span data-ttu-id="4da83-105">O texto que você deseja indicar como código.</span><span class="sxs-lookup"><span data-stu-id="4da83-105">The text you would like to indicate as code.</span></span>

## <a name="remarks"></a><span data-ttu-id="4da83-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="4da83-106">Remarks</span></span>

<span data-ttu-id="4da83-107">A `<c>` marca fornece uma maneira de indicar que o texto dentro de uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="4da83-107">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="4da83-108">Use [\<code>](./code.md) para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="4da83-108">Use [\<code>](./code.md) to indicate multiple lines as code.</span></span>

<span data-ttu-id="4da83-109">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="4da83-109">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="4da83-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="4da83-110">Example</span></span>

[!code-csharp[csProgGuideDocComments#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#2)]
  
## <a name="see-also"></a><span data-ttu-id="4da83-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="4da83-111">See also</span></span>

- [<span data-ttu-id="4da83-112">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="4da83-112">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="4da83-113">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="4da83-113">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
