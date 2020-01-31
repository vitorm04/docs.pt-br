---
title: <list> - C# guia de programação
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
ms.openlocfilehash: cb289b26e9bc12d561892c421fb40da18d8c3513
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789747"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="8a906-102">> de lista deC# \<(guia de programação)</span><span class="sxs-lookup"><span data-stu-id="8a906-102">\<list> (C# programming guide)</span></span>

## <a name="syntax"></a><span data-ttu-id="8a906-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8a906-103">Syntax</span></span>

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

## <a name="parameters"></a><span data-ttu-id="8a906-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8a906-104">Parameters</span></span>

- `term`

  <span data-ttu-id="8a906-105">Um termo a se definir, que será definido em `description`.</span><span class="sxs-lookup"><span data-stu-id="8a906-105">A term to define, which will be defined in `description`.</span></span>

- `description`

  <span data-ttu-id="8a906-106">Um item em uma lista com marcadores ou numerada ou uma definição de um `term`.</span><span class="sxs-lookup"><span data-stu-id="8a906-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="8a906-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="8a906-107">Remarks</span></span>

<span data-ttu-id="8a906-108">O bloco \<listheader> é usado para definir a linha de cabeçalho de uma tabela ou lista de definição.</span><span class="sxs-lookup"><span data-stu-id="8a906-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="8a906-109">Ao definir uma tabela, é necessário fornecer uma entrada para o termo no título.</span><span class="sxs-lookup"><span data-stu-id="8a906-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>

<span data-ttu-id="8a906-110">Cada item na lista é especificado com um bloco \<item>.</span><span class="sxs-lookup"><span data-stu-id="8a906-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="8a906-111">Ao criar uma lista de definições, é necessário especificar `term` e `description`.</span><span class="sxs-lookup"><span data-stu-id="8a906-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="8a906-112">No entanto, para uma tabela, lista com marcadores ou lista numerada, será necessário fornecer apenas uma entrada para `description`.</span><span class="sxs-lookup"><span data-stu-id="8a906-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>

<span data-ttu-id="8a906-113">Uma lista ou tabela pode ter quantos blocos \<item> forem necessários.</span><span class="sxs-lookup"><span data-stu-id="8a906-113">A list or table can have as many \<item> blocks as needed.</span></span>

<span data-ttu-id="8a906-114">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="8a906-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>

## <a name="example"></a><span data-ttu-id="8a906-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8a906-115">Example</span></span>

[!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]

## <a name="see-also"></a><span data-ttu-id="8a906-116">Veja também</span><span class="sxs-lookup"><span data-stu-id="8a906-116">See also</span></span>

- [<span data-ttu-id="8a906-117">Guia de programação em C#</span><span class="sxs-lookup"><span data-stu-id="8a906-117">C# programming guide</span></span>](../index.md)
- [<span data-ttu-id="8a906-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="8a906-118">Recommended tags for documentation comments</span></span>](./recommended-tags-for-documentation-comments.md)
