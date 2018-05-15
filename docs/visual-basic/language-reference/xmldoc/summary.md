---
title: '&lt;Resumo&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: cf320b61a2ca1c54b22e3c3d31ae51d003366efd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="312be-102">&lt;Resumo&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="312be-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="312be-103">Especifica o resumo do membro.</span><span class="sxs-lookup"><span data-stu-id="312be-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="312be-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="312be-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="312be-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="312be-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="312be-106">Um resumo do objeto.</span><span class="sxs-lookup"><span data-stu-id="312be-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="312be-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="312be-107">Remarks</span></span>  
 <span data-ttu-id="312be-108">Use o `<summary>` marcas para descrever um tipo ou um membro de tipo.</span><span class="sxs-lookup"><span data-stu-id="312be-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="312be-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) para adicionar mais informações a uma descrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="312be-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="312be-110">O texto para o `<summary>` marca é a única fonte de informações sobre o tipo do IntelliSense e também é exibida no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="312be-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="312be-111">Para obter informações sobre o Pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="312be-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="312be-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="312be-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="312be-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="312be-113">Example</span></span>  
 <span data-ttu-id="312be-114">Este exemplo usa o `<summary>` marcas para descrever o `ResetCounter` método e `Counter` propriedade.</span><span class="sxs-lookup"><span data-stu-id="312be-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="312be-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="312be-115">See Also</span></span>  
 [<span data-ttu-id="312be-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="312be-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
