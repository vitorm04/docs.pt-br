---
title: "&lt;código&gt; (Visual Basic) | Documentos do Microsoft"
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
- code XML tag
- <code> XML tag
ms.assetid: 925e5342-be05-45f2-bf66-7398bbd6710e
caps.latest.revision: 10
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
ms.openlocfilehash: 24e9b769d46d7ffab6556cbbc0653cfd7c084e09
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltcodegt-visual-basic"></a><span data-ttu-id="089d0-102">&lt;código&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="089d0-102">&lt;code&gt; (Visual Basic)</span></span>
<span data-ttu-id="089d0-103">Indica que o texto de várias linhas de código.</span><span class="sxs-lookup"><span data-stu-id="089d0-103">Indicates that the text is multiple lines of code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="089d0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="089d0-104">Syntax</span></span>  
  
```xml  
<code>content</code>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="089d0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="089d0-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="089d0-106">O texto para marcar como código.</span><span class="sxs-lookup"><span data-stu-id="089d0-106">The text to mark as code.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="089d0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="089d0-107">Remarks</span></span>  
 <span data-ttu-id="089d0-108">Use o `<code>` marca para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="089d0-108">Use the `<code>` tag to indicate multiple lines as code.</span></span> <span data-ttu-id="089d0-109">Use [ \<c >](../../../visual-basic/language-reference/xmldoc/c.md) para indicar que o texto dentro uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="089d0-109">Use [\<c>](../../../visual-basic/language-reference/xmldoc/c.md) to indicate that text within a description should be marked as code.</span></span>  
  
 <span data-ttu-id="089d0-110">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="089d0-110">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="089d0-111">Exemplo</span><span class="sxs-lookup"><span data-stu-id="089d0-111">Example</span></span>  
 <span data-ttu-id="089d0-112">Este exemplo usa o \<código > tag para incluir o código de exemplo para usar o `ID` campo.</span><span class="sxs-lookup"><span data-stu-id="089d0-112">This example uses the \<code> tag to include example code for using the `ID` field.</span></span>  
  
 <span data-ttu-id="089d0-113">[!code-vb[VbVbcnXmlDocComments n º&2;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="089d0-113">[!code-vb[VbVbcnXmlDocComments#2](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/code_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="089d0-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="089d0-114">See Also</span></span>  
 [<span data-ttu-id="089d0-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="089d0-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
