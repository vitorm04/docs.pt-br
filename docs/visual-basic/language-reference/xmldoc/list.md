---
title: <list> (Visual Basic)
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
ms.openlocfilehash: 7d7b85867f4c701322c5e6c31f2d89ab38fad05d
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58818521"
---
# <a name="list-visual-basic"></a><span data-ttu-id="59c59-102">\<lista > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="59c59-102">\<list> (Visual Basic)</span></span>
<span data-ttu-id="59c59-103">Define uma lista ou tabela.</span><span class="sxs-lookup"><span data-stu-id="59c59-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="59c59-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="59c59-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="59c59-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="59c59-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="59c59-106">O tipo de lista.</span><span class="sxs-lookup"><span data-stu-id="59c59-106">The type of the list.</span></span> <span data-ttu-id="59c59-107">Deve ser "bullet" para uma lista com marcadores, "number" para uma lista numerada ou "table" para uma tabela de duas colunas.</span><span class="sxs-lookup"><span data-stu-id="59c59-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="59c59-108">Somente usado ao `type` é "table".</span><span class="sxs-lookup"><span data-stu-id="59c59-108">Only used when `type` is "table."</span></span> <span data-ttu-id="59c59-109">Um termo para definir, que é definido na marca de descrição.</span><span class="sxs-lookup"><span data-stu-id="59c59-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="59c59-110">Quando `type` é "bullet" ou "number" `description` é um item na lista quando `type` é "table" `description` é a definição de `term`.</span><span class="sxs-lookup"><span data-stu-id="59c59-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="59c59-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="59c59-111">Remarks</span></span>  
 <span data-ttu-id="59c59-112">O `<listheader>` bloco define o título de uma tabela ou uma definição de lista.</span><span class="sxs-lookup"><span data-stu-id="59c59-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="59c59-113">Ao definir uma tabela, você só precisará fornecer uma entrada para `term` no título.</span><span class="sxs-lookup"><span data-stu-id="59c59-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="59c59-114">Cada item na lista é especificado com um `<item>` bloco.</span><span class="sxs-lookup"><span data-stu-id="59c59-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="59c59-115">Ao criar uma lista de definições, você deve especificar ambos `term` e `description`.</span><span class="sxs-lookup"><span data-stu-id="59c59-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="59c59-116">No entanto, para uma tabela, lista com marcadores ou lista numerada, você só precisa fornecer uma entrada para `description`.</span><span class="sxs-lookup"><span data-stu-id="59c59-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="59c59-117">Uma lista ou tabela pode ter quantos `<item>` bloqueia conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="59c59-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="59c59-118">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="59c59-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="59c59-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="59c59-119">Example</span></span>  
 <span data-ttu-id="59c59-120">Este exemplo usa o `<list>` marca para definir uma lista com marcadores na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="59c59-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="59c59-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="59c59-121">See also</span></span>

- [<span data-ttu-id="59c59-122">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="59c59-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
