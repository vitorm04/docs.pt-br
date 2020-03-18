---
title: <value> - Guia de programação C#
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: 120805346672738e614743ab8c98388b8dbac0f7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "76793345"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="68d70-102">\<valor> (guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="68d70-102">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="68d70-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="68d70-103">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="68d70-104">parâmetros</span><span class="sxs-lookup"><span data-stu-id="68d70-104">Parameters</span></span>

- `property-description`

  <span data-ttu-id="68d70-105">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="68d70-105">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="68d70-106">Comentários</span><span class="sxs-lookup"><span data-stu-id="68d70-106">Remarks</span></span>

<span data-ttu-id="68d70-107">A marca \<value> permite descrever o valor que uma propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="68d70-107">The \<value> tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="68d70-108">Observe que quando você adicionar uma propriedade via assistente de código no [ \<](./summary.md) ambiente de desenvolvimento do Visual Studio .NET, ele adicionará um resumo>tag para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="68d70-108">Note that when you add a property via code wizard in the Visual Studio .NET development environment, it will add a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="68d70-109">Então, você deve adicionar manualmente uma marca \<value> para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="68d70-109">You should then manually add a \<value> tag to describe the value that the property represents.</span></span>

<span data-ttu-id="68d70-110">Compilar com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="68d70-110">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="68d70-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="68d70-111">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="68d70-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="68d70-112">See also</span></span>

- [<span data-ttu-id="68d70-113">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="68d70-113">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="68d70-114">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="68d70-114">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
