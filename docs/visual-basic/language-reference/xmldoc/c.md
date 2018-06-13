---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 556c00fa761a1bce5e922a304706c78893550901
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599600"
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="f15b6-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="f15b6-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="f15b6-103">Indica que o texto dentro de uma descrição é o código.</span><span class="sxs-lookup"><span data-stu-id="f15b6-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f15b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f15b6-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f15b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f15b6-105">Parameters</span></span>  
  
|<span data-ttu-id="f15b6-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="f15b6-106">Parameter</span></span>|<span data-ttu-id="f15b6-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f15b6-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="f15b6-108">O texto que você deseja indicar como código.</span><span class="sxs-lookup"><span data-stu-id="f15b6-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f15b6-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="f15b6-109">Remarks</span></span>  
 <span data-ttu-id="f15b6-110">O `<c>` marca fornece uma maneira para indicar que o texto dentro de uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="f15b6-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="f15b6-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="f15b6-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="f15b6-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="f15b6-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f15b6-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="f15b6-113">Example</span></span>  
 <span data-ttu-id="f15b6-114">Este exemplo usa o `<c>` marca na seção de resumo para indicar que `Counter` é o código.</span><span class="sxs-lookup"><span data-stu-id="f15b6-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="f15b6-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f15b6-115">See Also</span></span>  
 [<span data-ttu-id="f15b6-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="f15b6-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)
