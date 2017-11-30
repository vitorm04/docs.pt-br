---
title: '&lt;consulte&gt; (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 010a3403d7748653648b323ad07f52bf93db2879
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="45e17-102">&lt;consulte&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45e17-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="45e17-103">Especifica um link para outro membro.</span><span class="sxs-lookup"><span data-stu-id="45e17-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45e17-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45e17-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45e17-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45e17-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="45e17-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="45e17-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="45e17-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome do elemento no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="45e17-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="45e17-108">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="45e17-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45e17-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="45e17-109">Remarks</span></span>  
 <span data-ttu-id="45e17-110">Use o `<see>` marca para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="45e17-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="45e17-111">Use [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) para indicar o texto que você pode aparecer em uma seção "Consulte também".</span><span class="sxs-lookup"><span data-stu-id="45e17-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="45e17-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="45e17-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45e17-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45e17-113">Example</span></span>  
 <span data-ttu-id="45e17-114">Este exemplo usa o `<see>` marca no `UpdateRecord` seção para se referir a comentários de `DoesRecordExist` método.</span><span class="sxs-lookup"><span data-stu-id="45e17-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="45e17-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45e17-115">See Also</span></span>  
 [<span data-ttu-id="45e17-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="45e17-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
