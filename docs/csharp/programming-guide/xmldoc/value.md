---
title: <value> -Guia de programação C#
description: Saiba mais sobre o XML <value> Tags. Essa marca permite descrever o valor que uma propriedade representa.
ms.date: 07/20/2015
f1_keywords:
- <value>
helpviewer_keywords:
- <value> C# XML tag
- value C# XML tag
ms.assetid: 08dbadaf-9ab6-43d9-9493-98e43bed199a
ms.openlocfilehash: d8294b477d7067653c71d1ec2047a85a0bfe6d02
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87380768"
---
# <a name="value-c-programming-guide"></a><span data-ttu-id="f10ec-105">\<value>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="f10ec-105">\<value> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="f10ec-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f10ec-106">Syntax</span></span>

```xml
<value>property-description</value>
```

## <a name="parameters"></a><span data-ttu-id="f10ec-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="f10ec-107">Parameters</span></span>

- `property-description`

  <span data-ttu-id="f10ec-108">Uma descrição da propriedade.</span><span class="sxs-lookup"><span data-stu-id="f10ec-108">A description for the property.</span></span>

## <a name="remarks"></a><span data-ttu-id="f10ec-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f10ec-109">Remarks</span></span>

<span data-ttu-id="f10ec-110">A `<value>` marca permite descrever o valor que uma propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="f10ec-110">The `<value>` tag lets you describe the value that a property represents.</span></span> <span data-ttu-id="f10ec-111">Quando você adiciona uma propriedade por meio do assistente de código no ambiente de desenvolvimento .NET do Visual Studio, ela adiciona uma [\<summary>](./summary.md) marca para a nova propriedade.</span><span class="sxs-lookup"><span data-stu-id="f10ec-111">When you add a property via code wizard in the Visual Studio .NET development environment, it adds a [\<summary>](./summary.md) tag for the new property.</span></span> <span data-ttu-id="f10ec-112">Em seguida, você deve adicionar manualmente uma `<value>` marca para descrever o valor que a propriedade representa.</span><span class="sxs-lookup"><span data-stu-id="f10ec-112">You should then manually add a `<value>` tag to describe the value that the property represents.</span></span>

<span data-ttu-id="f10ec-113">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f10ec-113">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="f10ec-114">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f10ec-114">Example</span></span>

[!code-csharp[csProgGuideDocComments#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#14)]

## <a name="see-also"></a><span data-ttu-id="f10ec-115">Confira também</span><span class="sxs-lookup"><span data-stu-id="f10ec-115">See also</span></span>

- [<span data-ttu-id="f10ec-116">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="f10ec-116">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="f10ec-117">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="f10ec-117">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
