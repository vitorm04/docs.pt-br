---
title: '&lt;lista&gt; (Visual Basic) | Documentos do Microsoft'
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
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
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: a32f50ce8a92fa22d9627a1510a4b3ec1087364e
ms.openlocfilehash: ebeac42800b22770fbb067c0cd6fb532c3b748ae
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltlistgt-visual-basic"></a><span data-ttu-id="519f7-102">&lt;lista&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="519f7-102">&lt;list&gt; (Visual Basic)</span></span>
<span data-ttu-id="519f7-103">Define uma lista ou tabela.</span><span class="sxs-lookup"><span data-stu-id="519f7-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="519f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="519f7-104">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="519f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="519f7-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="519f7-106">O tipo da lista.</span><span class="sxs-lookup"><span data-stu-id="519f7-106">The type of the list.</span></span> <span data-ttu-id="519f7-107">Deve ser um "marcador" para uma lista com marcadores, "number" para uma lista numerada ou "table" para uma tabela de duas colunas.</span><span class="sxs-lookup"><span data-stu-id="519f7-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="519f7-108">Somente usado quando `type` é "table".</span><span class="sxs-lookup"><span data-stu-id="519f7-108">Only used when `type` is "table."</span></span> <span data-ttu-id="519f7-109">Um termo para definir, que é definido na marca de descrição.</span><span class="sxs-lookup"><span data-stu-id="519f7-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="519f7-110">Quando `type` é "marcador" ou "número", `description` é um item na lista quando `type` é "table" `description` é a definição de `term`.</span><span class="sxs-lookup"><span data-stu-id="519f7-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="519f7-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="519f7-111">Remarks</span></span>  
 <span data-ttu-id="519f7-112">O `<listheader>` bloco define o título de uma tabela ou uma definição de lista.</span><span class="sxs-lookup"><span data-stu-id="519f7-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="519f7-113">Ao definir uma tabela, você só precisa fornecer uma entrada para `term` no título.</span><span class="sxs-lookup"><span data-stu-id="519f7-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="519f7-114">Cada item na lista é especificado com um `<item>` bloco.</span><span class="sxs-lookup"><span data-stu-id="519f7-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="519f7-115">Ao criar uma lista de definições, você deve especificar ambos `term` e `description`.</span><span class="sxs-lookup"><span data-stu-id="519f7-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="519f7-116">No entanto, para uma tabela, uma lista com marcadores ou uma lista numerada, você só precisa fornecer uma entrada para `description`.</span><span class="sxs-lookup"><span data-stu-id="519f7-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="519f7-117">Uma lista ou tabela pode ter tantas `<item>` bloqueia conforme necessário.</span><span class="sxs-lookup"><span data-stu-id="519f7-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="519f7-118">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="519f7-118">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="519f7-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="519f7-119">Example</span></span>  
 <span data-ttu-id="519f7-120">Este exemplo usa o `<list>` tag para definir uma lista com marcadores na seção comentários.</span><span class="sxs-lookup"><span data-stu-id="519f7-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 <span data-ttu-id="519f7-121">[!code-vb[VbVbcnXmlDocComments n º&5;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="519f7-121">[!code-vb[VbVbcnXmlDocComments#5](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/list_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="519f7-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="519f7-122">See Also</span></span>  
 [<span data-ttu-id="519f7-123">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="519f7-123">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
