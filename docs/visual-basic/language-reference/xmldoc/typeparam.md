---
title: '&lt;typeparam&gt; (Visual Basic) | Documentos do Microsoft'
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
- typeparam XML tag
- <typeparam> XML tag
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
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
ms.openlocfilehash: 10422e7619c0ec6a36390035f55544d5e0bfc079
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="lttypeparamgt-visual-basic"></a><span data-ttu-id="042c6-102">&lt;typeparam&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="042c6-102">&lt;typeparam&gt; (Visual Basic)</span></span>
<span data-ttu-id="042c6-103">Define um nome de parâmetro de tipo e descrição.</span><span class="sxs-lookup"><span data-stu-id="042c6-103">Defines a type parameter name and description.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="042c6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="042c6-104">Syntax</span></span>  
  
```xml  
<typeparam name="name">description</typeparam>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="042c6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="042c6-105">Parameters</span></span>  
 `name`  
 <span data-ttu-id="042c6-106">O nome do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="042c6-106">The name of the type parameter.</span></span> <span data-ttu-id="042c6-107">Coloque o nome entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="042c6-107">Enclose the name in double quotation marks (" ").</span></span>  
  
 `description`  
 <span data-ttu-id="042c6-108">Uma descrição do parâmetro de tipo.</span><span class="sxs-lookup"><span data-stu-id="042c6-108">A description of the type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="042c6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="042c6-109">Remarks</span></span>  
 <span data-ttu-id="042c6-110">Use o `<typeparam>` marca de comentário de um tipo genérico ou declaração de membro genérico descrever um dos parâmetros de tipo.</span><span class="sxs-lookup"><span data-stu-id="042c6-110">Use the `<typeparam>` tag in the comment for a generic type or generic member declaration to describe one of the type parameters.</span></span>  
  
 <span data-ttu-id="042c6-111">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="042c6-111">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="042c6-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="042c6-112">Example</span></span>  
 <span data-ttu-id="042c6-113">Este exemplo usa o `<typeparam>` marca para descrever o `id` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="042c6-113">This example uses the `<typeparam>` tag to describe the `id` parameter.</span></span>  
  
 <span data-ttu-id="042c6-114">[!code-vb[VbVbcnXmlDocComments n º&8;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="042c6-114">[!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/typeparam_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="042c6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="042c6-115">See Also</span></span>  
 [<span data-ttu-id="042c6-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="042c6-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
