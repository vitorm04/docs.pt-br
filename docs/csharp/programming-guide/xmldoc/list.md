---
title: <list> -Guia de programação C#
description: Saiba mais sobre o XML <list> Tags. Essa marca é usada para criar tabelas e definições com marcadores ou numeradas usando blocos ' item '.
ms.date: 07/20/2015
f1_keywords:
- list
- <list>
helpviewer_keywords:
- list C# XML tag
- listheader C# XML tag
- <listheader> C# XML tag
- item C# XML tag
- <item> C# XML tag
- <list> C# XML tag
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
ms.openlocfilehash: 361c2e6f343554a9b8519c3b2e41219b209e682d
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381860"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="7ca39-105">\<list>(Guia de programação C#)</span><span class="sxs-lookup"><span data-stu-id="7ca39-105">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ca39-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7ca39-106">Syntax</span></span>

```xml
<list type="bullet|number|table">
    <listheader>
        <term>term</term>
        <description>description</description>
    </listheader>
    <item>
        <term>term</term>
        <description>description</description>
    </item>
</list>
```

## <a name="parameters"></a><span data-ttu-id="7ca39-107">parâmetros</span><span class="sxs-lookup"><span data-stu-id="7ca39-107">Parameters</span></span>

- `term`

  <span data-ttu-id="7ca39-108">Um termo a se definir, que será definido em `description`.</span><span class="sxs-lookup"><span data-stu-id="7ca39-108">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="7ca39-109">Um item em uma lista com marcadores ou numerada ou uma definição de um `term`.</span><span class="sxs-lookup"><span data-stu-id="7ca39-109">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="7ca39-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7ca39-110">Remarks</span></span>

<span data-ttu-id="7ca39-111">O `<listheader>` bloco é usado para definir a linha de cabeçalho de uma tabela ou lista de definições.</span><span class="sxs-lookup"><span data-stu-id="7ca39-111">The `<listheader>` block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="7ca39-112">Ao definir uma tabela, é necessário fornecer uma entrada para o termo no título.</span><span class="sxs-lookup"><span data-stu-id="7ca39-112">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="7ca39-113">Cada item na lista é especificado com um `<item>` bloco.</span><span class="sxs-lookup"><span data-stu-id="7ca39-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="7ca39-114">Ao criar uma lista de definições, é necessário especificar `term` e `description`.</span><span class="sxs-lookup"><span data-stu-id="7ca39-114">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="7ca39-115">No entanto, para uma tabela, lista com marcadores ou lista numerada, será necessário fornecer apenas uma entrada para `description`.</span><span class="sxs-lookup"><span data-stu-id="7ca39-115">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="7ca39-116">Uma lista ou tabela pode ter tantos `<item>` blocos quantos forem necessários.</span><span class="sxs-lookup"><span data-stu-id="7ca39-116">A list or table can have as many `<item>` blocks as needed.</span></span>

<span data-ttu-id="7ca39-117">Compile com [-Doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="7ca39-117">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="7ca39-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7ca39-118">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="7ca39-119">Confira também</span><span class="sxs-lookup"><span data-stu-id="7ca39-119">See also</span></span>

- [<span data-ttu-id="7ca39-120">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="7ca39-120">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="7ca39-121">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="7ca39-121">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
