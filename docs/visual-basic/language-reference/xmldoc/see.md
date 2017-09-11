---
title: '&lt;consulte&gt; (Visual Basic) | Documentos do Microsoft'
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
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
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
ms.openlocfilehash: 4b4d1f683443d4a4ed060a9042ce0949e5fd5836
ms.contentlocale: pt-br
ms.lasthandoff: 06/01/2017

---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="f1a1a-102">&lt;consulte&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f1a1a-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="f1a1a-103">Especifica um link para outro membro.</span><span class="sxs-lookup"><span data-stu-id="f1a1a-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1a1a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f1a1a-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f1a1a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f1a1a-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="f1a1a-106">Uma referência a um membro ou campo que está disponível para ser chamado a partir do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="f1a1a-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="f1a1a-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome de elemento na saída XML.</span><span class="sxs-lookup"><span data-stu-id="f1a1a-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="f1a1a-108">`member`deve aparecer entre aspas duplas ("").</span><span class="sxs-lookup"><span data-stu-id="f1a1a-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f1a1a-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f1a1a-109">Remarks</span></span>  
 <span data-ttu-id="f1a1a-110">Use o `<see>` marca para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="f1a1a-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="f1a1a-111">Use [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) para indicar o texto que você pode aparecer em uma seção "Consulte também".</span><span class="sxs-lookup"><span data-stu-id="f1a1a-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="f1a1a-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação para um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f1a1a-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f1a1a-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f1a1a-113">Example</span></span>  
 <span data-ttu-id="f1a1a-114">Este exemplo usa o `<see>` marca no `UpdateRecord` seção para se referir a comentários a `DoesRecordExist` método.</span><span class="sxs-lookup"><span data-stu-id="f1a1a-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 <span data-ttu-id="f1a1a-115">[!code-vb[VbVbcnXmlDocComments n º&6;](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]</span><span class="sxs-lookup"><span data-stu-id="f1a1a-115">[!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f1a1a-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f1a1a-116">See Also</span></span>  
 [<span data-ttu-id="f1a1a-117">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="f1a1a-117">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
