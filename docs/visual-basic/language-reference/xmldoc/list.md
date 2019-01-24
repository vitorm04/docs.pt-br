---
title: '&lt;lista&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- listheader XML tag
- <item> XML tag
- <list> XML tag
- <listheader> XML tag
- term XML tag
- list XML tag
- <description> XML tag
- description XML tag
- item XML tag
- <term> XML tag
ms.assetid: ec35fced-d58e-4520-a764-0691256e014b
ms.openlocfilehash: 8d9bcffc32a1d1670aba1ce0e7b0ff0a6dc7112d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521108"
---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="30e81-102">&lt;lista&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="30e81-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="30e81-103">Define uma lista ou tabela.</span><span class="sxs-lookup"><span data-stu-id="30e81-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30e81-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="30e81-104">Syntax</span></span>  
  
```xml  
<list type="type">  
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
  
#### <a name="parameters"></a><span data-ttu-id="30e81-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="30e81-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="30e81-106">O tipo de lista.</span><span class="sxs-lookup"><span data-stu-id="30e81-106">The type of the list.</span></span> <span data-ttu-id="30e81-107">Deve ser "bullet" para uma lista com marcadores, "number" para uma lista numerada ou "table" para uma tabela de duas colunas.</span><span class="sxs-lookup"><span data-stu-id="30e81-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="30e81-108">Somente usado ao `type` é "table".</span><span class="sxs-lookup"><span data-stu-id="30e81-108">Only used when `type` is "table."</span></span> <span data-ttu-id="30e81-109">Um termo para definir, que é definido na marca de descrição.</span><span class="sxs-lookup"><span data-stu-id="30e81-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="30e81-110">Quando `type` é "bullet" ou "number" `description` é um item na lista quando `type` é "table" `description` é a definição de `term`.</span><span class="sxs-lookup"><span data-stu-id="30e81-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="30e81-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="30e81-111">Remarks</span></span>  
 <span data-ttu-id="30e81-112">O `<listheader>` bloco define o título de uma tabela ou uma definição de lista.</span><span class="sxs-lookup"><span data-stu-id="30e81-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="30e81-113">Ao definir uma tabela, você só precisará fornecer uma entrada para `term` no título.</span><span class="sxs-lookup"><span data-stu-id="30e81-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="30e81-114">Cada item na lista é especificado com um `<item>` bloco.</span><span class="sxs-lookup"><span data-stu-id="30e81-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="30e81-115">Ao criar uma lista de definições, você deve especificar ambos `term` e `description`.</span><span class="sxs-lookup"><span data-stu-id="30e81-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="30e81-116">No entanto, para uma tabela, lista com marcadores ou lista numerada, você só precisa fornecer uma entrada para `description`.</span><span class="sxs-lookup"><span data-stu-id="30e81-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="30e81-117">Uma lista ou tabela pode ter quantos `<item>` bloqueia conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="30e81-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="30e81-118">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="30e81-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="30e81-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="30e81-119">Example</span></span>  
 <span data-ttu-id="30e81-120">Este exemplo usa o `<list>` marca para definir uma lista com marcadores na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="30e81-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="30e81-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="30e81-121">See also</span></span>
- [<span data-ttu-id="30e81-122">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="30e81-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
