---
title: '&lt;para&gt; (Visual Basic) | Documentos do Microsoft'
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
- <para> XML tag
- para XML tag
ms.assetid: a3a18b6c-6416-4358-94ec-37b22675fd37
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
ms.openlocfilehash: fab820ac702c1868142b8f31783f1725cb07222f
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltparagt-visual-basic"></a><span data-ttu-id="29567-102">&lt;para&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="29567-102">&lt;para&gt; (Visual Basic)</span></span>
<span data-ttu-id="29567-103">Especifica que o conteúdo é formatado como um parágrafo.</span><span class="sxs-lookup"><span data-stu-id="29567-103">Specifies that the content is formatted as a paragraph.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29567-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29567-104">Syntax</span></span>  
  
```xml  
<para>content</para>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29567-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29567-105">Parameters</span></span>  
 `content`  
 <span data-ttu-id="29567-106">O texto do parágrafo.</span><span class="sxs-lookup"><span data-stu-id="29567-106">The text of the paragraph.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="29567-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="29567-107">Remarks</span></span>  
 <span data-ttu-id="29567-108">O `<para>` marca é para uso dentro de uma marca, como [ \<resumo >](../../../visual-basic/language-reference/xmldoc/summary.md), [ \<comentários >](../../../visual-basic/language-reference/xmldoc/remarks.md), ou [ \<retorna >](../../../visual-basic/language-reference/xmldoc/returns.md)e permite que você adicione estrutura ao texto.</span><span class="sxs-lookup"><span data-stu-id="29567-108">The `<para>` tag is for use inside a tag, such as [\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md), [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md), or [\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md), and lets you add structure to the text.</span></span>  
  
 <span data-ttu-id="29567-109">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="29567-109">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="29567-110">Exemplo</span><span class="sxs-lookup"><span data-stu-id="29567-110">Example</span></span>  
 <span data-ttu-id="29567-111">Este exemplo usa o `<para>` marca para dividir a seção comentários para o `UpdateRecord` método em dois parágrafos.</span><span class="sxs-lookup"><span data-stu-id="29567-111">This example uses the `<para>` tag to split the remarks section for the `UpdateRecord` method into two paragraphs.</span></span>  
  
 <span data-ttu-id="29567-112">[!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="29567-112">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/para_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29567-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29567-113">See Also</span></span>  
 [<span data-ttu-id="29567-114">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="29567-114">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
