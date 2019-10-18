---
title: <list> – Guia de Programação em C#
ms.custom: seodec18
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
ms.openlocfilehash: 0df6653171aa0366f555c39e4644f13b2b7384f9
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72523437"
---
# <a name="list-c-programming-guide"></a><span data-ttu-id="88a3a-102">\<list> (Guia de Programação em C#)</span><span class="sxs-lookup"><span data-stu-id="88a3a-102">\<list> (C# Programming Guide)</span></span>
## <a name="syntax"></a><span data-ttu-id="88a3a-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88a3a-103">Syntax</span></span>  
  
```xml  
<list type="bullet" | "number" | "table">  
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
  
## <a name="parameters"></a><span data-ttu-id="88a3a-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="88a3a-104">Parameters</span></span>  
 `term`  
 <span data-ttu-id="88a3a-105">Um termo a se definir, que será definido em `description`.</span><span class="sxs-lookup"><span data-stu-id="88a3a-105">A term to define, which will be defined in `description`.</span></span>  
  
 `description`  
 <span data-ttu-id="88a3a-106">Um item em uma lista com marcadores ou numerada ou uma definição de um `term`.</span><span class="sxs-lookup"><span data-stu-id="88a3a-106">Either an item in a bullet or numbered list or the definition of a `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="88a3a-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="88a3a-107">Remarks</span></span>  
 <span data-ttu-id="88a3a-108">O bloco \<listheader> é usado para definir a linha de cabeçalho de uma tabela ou lista de definição.</span><span class="sxs-lookup"><span data-stu-id="88a3a-108">The \<listheader> block is used to define the heading row of either a table or definition list.</span></span> <span data-ttu-id="88a3a-109">Ao definir uma tabela, é necessário fornecer uma entrada para o termo no título.</span><span class="sxs-lookup"><span data-stu-id="88a3a-109">When defining a table, you only need to supply an entry for term in the heading.</span></span>  
  
 <span data-ttu-id="88a3a-110">Cada item na lista é especificado com um bloco \<item>.</span><span class="sxs-lookup"><span data-stu-id="88a3a-110">Each item in the list is specified with an \<item> block.</span></span> <span data-ttu-id="88a3a-111">Ao criar uma lista de definições, é necessário especificar `term` e `description`.</span><span class="sxs-lookup"><span data-stu-id="88a3a-111">When creating a definition list, you will need to specify both `term` and `description`.</span></span> <span data-ttu-id="88a3a-112">No entanto, para uma tabela, lista com marcadores ou lista numerada, será necessário fornecer apenas uma entrada para `description`.</span><span class="sxs-lookup"><span data-stu-id="88a3a-112">However, for a table, bulleted list, or numbered list, you only need to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="88a3a-113">Uma lista ou tabela pode ter quantos blocos \<item> forem necessários.</span><span class="sxs-lookup"><span data-stu-id="88a3a-113">A list or table can have as many \<item> blocks as needed.</span></span>  
  
 <span data-ttu-id="88a3a-114">Compile com [-doc](../../language-reference/compiler-options/doc-compiler-option.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="88a3a-114">Compile with [-doc](../../language-reference/compiler-options/doc-compiler-option.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="88a3a-115">Exemplo</span><span class="sxs-lookup"><span data-stu-id="88a3a-115">Example</span></span>  
 [!code-csharp[csProgGuideDocComments#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideDocComments/CS/DocComments.cs#6)]  
  
## <a name="see-also"></a><span data-ttu-id="88a3a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88a3a-116">See also</span></span>

- [<span data-ttu-id="88a3a-117">Guia de Programação em C#</span><span class="sxs-lookup"><span data-stu-id="88a3a-117">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="88a3a-118">Marcas recomendadas para comentários de documentação</span><span class="sxs-lookup"><span data-stu-id="88a3a-118">Recommended Tags for Documentation Comments</span></span>](./recommended-tags-for-documentation-comments.md)
