---
title: '&lt;consulte&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- see XML tag
- <see> XML tag
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
ms.openlocfilehash: 78311651593d3d4a47c723f64a9a74d4660f7c90
ms.sourcegitcommit: fe02afbc39e78afd78cc6050e4a9c12a75f579f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2018
ms.locfileid: "43254056"
---
# <a name="ltseegt-visual-basic"></a><span data-ttu-id="45f91-102">&lt;consulte&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="45f91-102">&lt;see&gt; (Visual Basic)</span></span>
<span data-ttu-id="45f91-103">Especifica um link para outro membro.</span><span class="sxs-lookup"><span data-stu-id="45f91-103">Specifies a link to another member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="45f91-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="45f91-104">Syntax</span></span>  
  
```xml  
<see cref="member"/>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="45f91-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="45f91-105">Parameters</span></span>  
 `member`  
 <span data-ttu-id="45f91-106">Uma referência a um membro ou campo disponível para ser chamado do ambiente de compilação atual.</span><span class="sxs-lookup"><span data-stu-id="45f91-106">A reference to a member or field that is available to be called from the current compilation environment.</span></span> <span data-ttu-id="45f91-107">O compilador verifica se o elemento de código fornecido existe e passa `member` para o nome do elemento no XML de saída.</span><span class="sxs-lookup"><span data-stu-id="45f91-107">The compiler checks that the given code element exists and passes `member` to the element name in the output XML.</span></span> <span data-ttu-id="45f91-108">`member` deve ser exibido entre aspas duplas (" ").</span><span class="sxs-lookup"><span data-stu-id="45f91-108">`member` must appear within double quotation marks (" ").</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="45f91-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="45f91-109">Remarks</span></span>  
 <span data-ttu-id="45f91-110">Use o `<see>` marca para especificar um link de dentro do texto.</span><span class="sxs-lookup"><span data-stu-id="45f91-110">Use the `<see>` tag to specify a link from within text.</span></span> <span data-ttu-id="45f91-111">Use [ \<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) para indicar o texto que você talvez queira aparecem em uma seção "Consulte também".</span><span class="sxs-lookup"><span data-stu-id="45f91-111">Use [\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) to indicate text that you might want to appear in a "See Also" section.</span></span>  
  
 <span data-ttu-id="45f91-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="45f91-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45f91-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="45f91-113">Example</span></span>  
 <span data-ttu-id="45f91-114">Este exemplo usa o `<see>` marcar na `UpdateRecord` seção para se referir a comentários de `DoesRecordExist` método.</span><span class="sxs-lookup"><span data-stu-id="45f91-114">This example uses the `<see>` tag in the `UpdateRecord` remarks section to refer to the `DoesRecordExist` method.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="45f91-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="45f91-115">See Also</span></span>  
 [<span data-ttu-id="45f91-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="45f91-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
