---
title: '&lt;Consulte também&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <seealso> XML tag
- seealso XML tag
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
ms.openlocfilehash: 1d45c0c5fa95de9cfa345c0bdbf496aa227b9af5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ltseealsogt-visual-basic"></a><span data-ttu-id="f5927-102">&lt;Consulte também&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f5927-102">&lt;seealso&gt; (Visual Basic)</span></span>
<span data-ttu-id="f5927-103">Especifica um link que aparece na seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="f5927-103">Specifies a link that appears in the See Also section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5927-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5927-104">Syntax</span></span>  
  
```xml  
<seealso cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f5927-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5927-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="f5927-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="f5927-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="f5927-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome do elemento no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="f5927-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="f5927-108">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="f5927-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f5927-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f5927-109">Remarks</span></span>  
 <span data-ttu-id="f5927-110">Use o `<seealso>` marca para especificar o texto que você deseja que apareça em uma seção Consulte também.</span><span class="sxs-lookup"><span data-stu-id="f5927-110">Use the `<seealso>` tag to specify the text that you want to appear in a See Also section.</span></span> <span data-ttu-id="f5927-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="f5927-111">Use [\<see>](../../../visual-basic/language-reference/xmldoc/see.md) to specify a link from within text.</span></span>  
  
 <span data-ttu-id="f5927-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f5927-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5927-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f5927-113">Example</span></span>  
 <span data-ttu-id="f5927-114">Este exemplo usa o `<seealso>` marca no `DoesRecordExist` seção para se referir a comentários de `UpdateRecord` método.</span><span class="sxs-lookup"><span data-stu-id="f5927-114">This example uses the `<seealso>` tag in the `DoesRecordExist` remarks section to refer to the `UpdateRecord` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f5927-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f5927-115">See Also</span></span>  
 [<span data-ttu-id="f5927-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="f5927-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
