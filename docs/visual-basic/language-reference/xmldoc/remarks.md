---
title: '&lt;comentários&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 137e2fcd36d5d7618e0193461ebf7ca70b24d19f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737644"
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="f75b4-102">&lt;comentários&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f75b4-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="f75b4-103">Especifica uma seção de comentários para o membro.</span><span class="sxs-lookup"><span data-stu-id="f75b4-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f75b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f75b4-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f75b4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f75b4-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="f75b4-106">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="f75b4-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f75b4-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f75b4-107">Remarks</span></span>  
 <span data-ttu-id="f75b4-108">Use o `<remarks>` marca para adicionar informações sobre um tipo, complementando as informações especificadas com [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="f75b4-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="f75b4-109">Essas informações são exibidas no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="f75b4-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="f75b4-110">Para obter informações sobre o Pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="f75b4-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="f75b4-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f75b4-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f75b4-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f75b4-112">Example</span></span>  
 <span data-ttu-id="f75b4-113">Este exemplo usa o `<remarks>` marca para explicar o que o `UpdateRecord` que o método.</span><span class="sxs-lookup"><span data-stu-id="f75b4-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f75b4-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f75b4-114">See also</span></span>
- [<span data-ttu-id="f75b4-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="f75b4-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
