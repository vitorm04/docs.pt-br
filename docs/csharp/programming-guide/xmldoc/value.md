---
title: <value> - C# guia de programação
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793345"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="abebf-102">> de valor deC# \<(guia de programação)</span><span class="sxs-lookup"><span data-stu-id="abebf-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="abebf-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="abebf-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="abebf-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="abebf-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="abebf-105">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="abebf-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="abebf-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="abebf-106">Remarks</span></span>

<span data-ttu-id="abebf-107">A marca \<value> permite descrever o valor que uma propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="abebf-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="abebf-108">Observe que quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento do Visual Studio .NET, ele adicionará uma marca [\<summary>](./summary.md) para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="abebf-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="abebf-109">Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="abebf-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>

<span data-ttu-id="abebf-110">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="abebf-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="abebf-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="abebf-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="abebf-112">Veja também</span><span class="sxs-lookup"><span data-stu-id="abebf-112">See also</span></span>

- [<span data-ttu-id="abebf-113">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="abebf-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="abebf-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="abebf-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
