---
title: '&lt;comentários&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
ms.openlocfilehash: 97fca8758d9c21ac0b8f15bf9d5831750fbabe77
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/04/2018
ms.locfileid: "43557070"
---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="26f99-102">&lt;comentários&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="26f99-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="26f99-103">Especifica uma seção de comentários para o membro.</span><span class="sxs-lookup"><span data-stu-id="26f99-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26f99-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="26f99-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="26f99-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="26f99-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="26f99-106">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="26f99-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="26f99-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="26f99-107">Remarks</span></span>  
 <span data-ttu-id="26f99-108">Use o `<remarks>` marca para adicionar informações sobre um tipo, complementando as informações especificadas com [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="26f99-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="26f99-109">Essas informações são exibidas no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="26f99-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="26f99-110">Para obter informações sobre o Pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="26f99-110">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="26f99-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="26f99-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="26f99-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="26f99-112">Example</span></span>  
 <span data-ttu-id="26f99-113">Este exemplo usa o `<remarks>` marca para explicar o que o `UpdateRecord` que o método.</span><span class="sxs-lookup"><span data-stu-id="26f99-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="26f99-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="26f99-114">See Also</span></span>  
 [<span data-ttu-id="26f99-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="26f99-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
