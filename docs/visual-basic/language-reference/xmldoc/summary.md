---
title: '&lt;Resumo&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- <summary> XML tag
- summary XML tag
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
ms.openlocfilehash: 5ef9b7a98503ff36174de4418ca7d599c365f5aa
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/08/2018
ms.locfileid: "44187254"
---
# <a name="ltsummarygt-visual-basic"></a><span data-ttu-id="1d5b0-102">&lt;Resumo&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1d5b0-102">&lt;summary&gt; (Visual Basic)</span></span>
<span data-ttu-id="1d5b0-103">Especifica o resumo do membro.</span><span class="sxs-lookup"><span data-stu-id="1d5b0-103">Specifies the summary of the member.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d5b0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1d5b0-104">Syntax</span></span>  
  
```xml  
<summary>description</summary>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="1d5b0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1d5b0-105">Parameters</span></span>  
 `description`  
 <span data-ttu-id="1d5b0-106">Um resumo do objeto.</span><span class="sxs-lookup"><span data-stu-id="1d5b0-106">A summary of the object.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1d5b0-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="1d5b0-107">Remarks</span></span>  
 <span data-ttu-id="1d5b0-108">Use o `<summary>` marca para descrever um tipo ou membro de tipo.</span><span class="sxs-lookup"><span data-stu-id="1d5b0-108">Use the `<summary>` tag to describe a type or a type member.</span></span> <span data-ttu-id="1d5b0-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) para adicionar mais informações a uma descrição de tipo.</span><span class="sxs-lookup"><span data-stu-id="1d5b0-109">Use [\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md) to add supplemental information to a type description.</span></span>  
  
 <span data-ttu-id="1d5b0-110">O texto para o `<summary>` marca é a única fonte de informações sobre o tipo no IntelliSense e também é exibida no Pesquisador de objetos.</span><span class="sxs-lookup"><span data-stu-id="1d5b0-110">The text for the `<summary>` tag is the only source of information about the type in IntelliSense, and is also displayed in the Object Browser.</span></span> <span data-ttu-id="1d5b0-111">Para obter informações sobre o Pesquisador de objetos, consulte [exibindo a estrutura do código](/visualstudio/ide/viewing-the-structure-of-code).</span><span class="sxs-lookup"><span data-stu-id="1d5b0-111">For information about the Object Browser, see [Viewing the Structure of Code](/visualstudio/ide/viewing-the-structure-of-code).</span></span>  
  
 <span data-ttu-id="1d5b0-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="1d5b0-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d5b0-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="1d5b0-113">Example</span></span>  
 <span data-ttu-id="1d5b0-114">Este exemplo usa o `<summary>` marca para descrever o `ResetCounter` método e `Counter` propriedade.</span><span class="sxs-lookup"><span data-stu-id="1d5b0-114">This example uses the `<summary>` tag to describe the `ResetCounter` method and `Counter` property.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="1d5b0-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1d5b0-115">See Also</span></span>  
 [<span data-ttu-id="1d5b0-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="1d5b0-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
