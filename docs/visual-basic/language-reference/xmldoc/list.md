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
ms.openlocfilehash: 5d4295d485611e75e8b6c8d8f95e079654f0cfa3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524755"
---
# <a name="list-visual-basic"></a><span data-ttu-id="55b53-102">> de \<list (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="55b53-102">\<list> (Visual Basic)</span></span>
<span data-ttu-id="55b53-103">Define uma lista ou tabela.</span><span class="sxs-lookup"><span data-stu-id="55b53-103">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="55b53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="55b53-104">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="55b53-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="55b53-105">Parameters</span></span>  
 `type`  
 <span data-ttu-id="55b53-106">O tipo da lista.</span><span class="sxs-lookup"><span data-stu-id="55b53-106">The type of the list.</span></span> <span data-ttu-id="55b53-107">Deve ser um "Bullet" para uma lista com marcadores, "Number" para uma lista numerada ou "Table" para uma tabela de duas colunas.</span><span class="sxs-lookup"><span data-stu-id="55b53-107">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="55b53-108">Usado somente quando `type` é "Table".</span><span class="sxs-lookup"><span data-stu-id="55b53-108">Only used when `type` is "table."</span></span> <span data-ttu-id="55b53-109">Um termo a definir, que é definido na marca de descrição.</span><span class="sxs-lookup"><span data-stu-id="55b53-109">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="55b53-110">Quando `type` é "Bullet" ou "Number", `description` é um item na lista quando `type` é "Table", `description` é a definição de `term`.</span><span class="sxs-lookup"><span data-stu-id="55b53-110">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="55b53-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="55b53-111">Remarks</span></span>  
 <span data-ttu-id="55b53-112">O bloco `<listheader>` define o cabeçalho de uma tabela ou de uma lista de definições.</span><span class="sxs-lookup"><span data-stu-id="55b53-112">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="55b53-113">Ao definir uma tabela, você só precisa fornecer uma entrada para `term` no título.</span><span class="sxs-lookup"><span data-stu-id="55b53-113">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="55b53-114">Cada item na lista é especificado com um bloco de `<item>`.</span><span class="sxs-lookup"><span data-stu-id="55b53-114">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="55b53-115">Ao criar uma lista de definições, você deve especificar `term` e `description`.</span><span class="sxs-lookup"><span data-stu-id="55b53-115">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="55b53-116">No entanto, para uma tabela, lista com marcadores ou lista numerada, você só precisa fornecer uma entrada para `description`.</span><span class="sxs-lookup"><span data-stu-id="55b53-116">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="55b53-117">Uma lista ou tabela pode ter tantos blocos de `<item>` quantos forem necessários.</span><span class="sxs-lookup"><span data-stu-id="55b53-117">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="55b53-118">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="55b53-118">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="55b53-119">Exemplo</span><span class="sxs-lookup"><span data-stu-id="55b53-119">Example</span></span>  
 <span data-ttu-id="55b53-120">Este exemplo usa a marca de `<list>` para definir uma lista com marcadores na seção de comentários.</span><span class="sxs-lookup"><span data-stu-id="55b53-120">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="55b53-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="55b53-121">See also</span></span>

- [<span data-ttu-id="55b53-122">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="55b53-122">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
