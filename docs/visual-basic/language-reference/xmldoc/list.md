---
title: <list>
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
ms.openlocfilehash: db5c571d2f2c59419c886f6596f4e4dbd30d7baf
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352315"
---
# <a name="list-visual-basic"></a><span data-ttu-id="8016a-101">> da lista de \<(Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8016a-101">\<list> (Visual Basic)</span></span>
<span data-ttu-id="8016a-102">Define uma lista ou tabela.</span><span class="sxs-lookup"><span data-stu-id="8016a-102">Defines a list or table.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8016a-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8016a-103">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="8016a-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="8016a-104">Parameters</span></span>  
 `type`  
 <span data-ttu-id="8016a-105">O tipo da lista.</span><span class="sxs-lookup"><span data-stu-id="8016a-105">The type of the list.</span></span> <span data-ttu-id="8016a-106">Deve ser um "Bullet" para uma lista com marcadores, "Number" para uma lista numerada ou "Table" para uma tabela de duas colunas.</span><span class="sxs-lookup"><span data-stu-id="8016a-106">Must be a "bullet" for a bulleted list, "number" for a numbered list, or "table" for a two-column table.</span></span>  
  
 `term`  
 <span data-ttu-id="8016a-107">Usado somente quando `type` é "Table".</span><span class="sxs-lookup"><span data-stu-id="8016a-107">Only used when `type` is "table."</span></span> <span data-ttu-id="8016a-108">Um termo a definir, que é definido na marca de descrição.</span><span class="sxs-lookup"><span data-stu-id="8016a-108">A term to define, which is defined in the description tag.</span></span>  
  
 `description`  
 <span data-ttu-id="8016a-109">Quando `type` é "Bullet" ou "Number", `description` é um item na lista quando `type` é "Table", `description` é a definição de `term`.</span><span class="sxs-lookup"><span data-stu-id="8016a-109">When `type` is "bullet" or "number," `description` is an item in the list When `type` is "table," `description` is the definition of `term`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8016a-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="8016a-110">Remarks</span></span>  
 <span data-ttu-id="8016a-111">O bloco `<listheader>` define o cabeçalho de uma tabela ou de uma lista de definições.</span><span class="sxs-lookup"><span data-stu-id="8016a-111">The `<listheader>` block defines the heading of either a table or definition list.</span></span> <span data-ttu-id="8016a-112">Ao definir uma tabela, você só precisa fornecer uma entrada para `term` no título.</span><span class="sxs-lookup"><span data-stu-id="8016a-112">When defining a table, you only have to supply an entry for `term` in the heading.</span></span>  
  
 <span data-ttu-id="8016a-113">Cada item na lista é especificado com um bloco de `<item>`.</span><span class="sxs-lookup"><span data-stu-id="8016a-113">Each item in the list is specified with an `<item>` block.</span></span> <span data-ttu-id="8016a-114">Ao criar uma lista de definições, você deve especificar `term` e `description`.</span><span class="sxs-lookup"><span data-stu-id="8016a-114">When creating a definition list, you must specify both `term` and `description`.</span></span> <span data-ttu-id="8016a-115">No entanto, para uma tabela, lista com marcadores ou lista numerada, você só precisa fornecer uma entrada para `description`.</span><span class="sxs-lookup"><span data-stu-id="8016a-115">However, for a table, bulleted list, or numbered list, you only have to supply an entry for `description`.</span></span>  
  
 <span data-ttu-id="8016a-116">Uma lista ou tabela pode ter tantos blocos de `<item>` quantos forem necessários.</span><span class="sxs-lookup"><span data-stu-id="8016a-116">A list or table can have as many `<item>` blocks as needed.</span></span>  
  
 <span data-ttu-id="8016a-117">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="8016a-117">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8016a-118">Exemplo</span><span class="sxs-lookup"><span data-stu-id="8016a-118">Example</span></span>  
 <span data-ttu-id="8016a-119">Este exemplo usa a marca de `<list>` para definir uma lista com marcadores na seção de comentários.</span><span class="sxs-lookup"><span data-stu-id="8016a-119">This example uses the `<list>` tag to define a bulleted list in the remarks section.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#5)]  
  
## <a name="see-also"></a><span data-ttu-id="8016a-120">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8016a-120">See also</span></span>

- [<span data-ttu-id="8016a-121">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="8016a-121">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
