---
title: "&lt;comentários&gt; (Visual Basic) | Documentos do Microsoft"
ms.custom: 
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
- <remarks> XML tag
- remarks XML tag
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
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
ms.openlocfilehash: c1b2c48dc3247935f703ff4107f29829c494a305
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltremarksgt-visual-basic"></a><span data-ttu-id="f5120-102">&lt;comentários&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5120-102">&lt;remarks&gt; (Visual Basic)</span></span>
<span data-ttu-id="f5120-103">Especifica uma seção de comentários para o membro.</span><span class="sxs-lookup"><span data-stu-id="f5120-103">Specifies a remarks section for the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5120-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5120-104">Syntax</span></span>  
  
```xml  
<remarks>description</remarks>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5120-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5120-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="f5120-106">Uma descrição do membro.</span><span class="sxs-lookup"><span data-stu-id="f5120-106">A description of the member.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5120-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5120-107">Remarks</span></span>  
 <span data-ttu-id="f5120-108">Use o `<remarks>` marca para adicionar informações sobre um tipo, complementando as informações especificadas com [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md).</span><span class="sxs-lookup"><span data-stu-id="f5120-108">Use the `<remarks>` tag to add information about a type, supplementing the information specified with [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md).</span></span>  
  
 <span data-ttu-id="f5120-109">Essas informações aparecem no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="f5120-109">This information appears in the Object Browser.</span></span> <span data-ttu-id="f5120-110">Para obter informações sobre o Pesquisador de objetos, consulte [exibindo a estrutura do código](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="f5120-110">For information about the Object Browser, see [Viewing the Structure of Code](https://docs.microsoft.com/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="f5120-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f5120-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5120-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5120-112">Example</span></span>  
 <span data-ttu-id="f5120-113">Este exemplo usa o `<remarks>` marca para explicar o que o `UpdateRecord` método faz.</span><span class="sxs-lookup"><span data-stu-id="f5120-113">This example uses the `<remarks>` tag to explain what the `UpdateRecord` method does.</span></span>  
  
 <span data-ttu-id="f5120-114">[!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f5120-114">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5120-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5120-115">See Also</span></span>  
 [<span data-ttu-id="f5120-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="f5120-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
