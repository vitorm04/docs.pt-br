---
title: <value> -Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: bd6630a8d5894fda39ad289c8dd584f6d84e5490
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287188"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="f5629-102">\<value>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="f5629-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5629-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5629-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="f5629-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5629-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="f5629-105">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f5629-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5629-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5629-106">Remarks</span></span>

<span data-ttu-id="f5629-107">A `<value>` marca permite descrever o valor que uma propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="f5629-107">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="f5629-108">Quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento .NET do Visual Studio, ela adiciona uma [\<summary>](./summary.md) marca para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="f5629-108">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="f5629-109">Em seguida, você deve adicionar manualmente uma `<value>` marca para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="f5629-109">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="f5629-110">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f5629-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="f5629-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5629-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="f5629-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="f5629-112">See also</span></span>

- [<span data-ttu-id="f5629-113">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="f5629-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f5629-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="f5629-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
