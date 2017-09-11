---
title: "&lt;Consulte também&gt; (Visual Basic) | Documentos do Microsoft"
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
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
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
ms.openlocfilehash: 915f7ea828386e5a1df3f1279f429cd5b3d240c5
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="232c8-102">&lt;Consulte também&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="232c8-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="232c8-103">Especifica um link que aparece na seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="232c8-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="232c8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="232c8-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="232c8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="232c8-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="232c8-106">Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="232c8-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="232c8-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento na saída XML.</span><span class="sxs-lookup"><span data-stu-id="232c8-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="232c8-108">`member`deve aparecer entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="232c8-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="232c8-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="232c8-109">Remarks</span></span>  
 <span data-ttu-id="232c8-110">Use o `<seealso>` marca para especificar o texto que você deseja que apareça em uma seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="232c8-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="232c8-111">Use [ \<consulte >](../../../visual-basic/language-reference/xmldoc/see.md) para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="232c8-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="232c8-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="232c8-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="232c8-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="232c8-113">Example</span></span>  
 <span data-ttu-id="232c8-114">Este exemplo usa o `<seealso>` marca no `DoesRecordExist` seção para se referir a comentários a `UpdateRecord` método.</span><span class="sxs-lookup"><span data-stu-id="232c8-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 <span data-ttu-id="232c8-115">[!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="232c8-115">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="232c8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="232c8-116">See Also</span></span>  
 [<span data-ttu-id="232c8-117">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="232c8-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
