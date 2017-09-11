---
title: '&lt;Retorna&gt; (Visual Basic) | Documentos do Microsoft'
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
- returns XML tag
- <returns> XML tag
ms.assetid: a03a6469-d907-425d-882f-083187950e7e
caps.latest.revision: 9
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
ms.openlocfilehash: 8ef6120a2975439b00a928cc56f13c2ec0cd1f45
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltreturnsgt-visual-basic"></a><span data-ttu-id="898a2-102">&lt;Retorna&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="898a2-102">&lt;returns&gt; (Visual Basic)</span></span>
<span data-ttu-id="898a2-103">Especifica o valor de retorno da propriedade ou função.</span><span class="sxs-lookup"><span data-stu-id="898a2-103">Specifies the return value of the property or function.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="898a2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="898a2-104">Syntax</span></span>  
  
```xml  
<returns>description</returns>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="898a2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="898a2-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="898a2-106">Uma descrição do valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="898a2-106">A description of the return value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="898a2-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="898a2-107">Remarks</span></span>  
 <span data-ttu-id="898a2-108">Use o `<returns>` marca de comentário para uma declaração de método descrever o valor de retorno.</span><span class="sxs-lookup"><span data-stu-id="898a2-108">Use the `<returns>` tag in the comment for a method declaration to describe the return value.</span></span>  
  
 <span data-ttu-id="898a2-109">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="898a2-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="898a2-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="898a2-110">Example</span></span>  
 <span data-ttu-id="898a2-111">Este exemplo usa o `<returns>` marca para explicar o que o `DoesRecordExist` retornos de função.</span><span class="sxs-lookup"><span data-stu-id="898a2-111">This example uses the `<returns>` tag to explain what the `DoesRecordExist` function returns.</span></span>  
  
 <span data-ttu-id="898a2-112">[!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="898a2-112">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/returns_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="898a2-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="898a2-113">See Also</span></span>  
 [<span data-ttu-id="898a2-114">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="898a2-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
