---
title: '&lt;c&gt; (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 06c6899895f278fdf652725a05ecc7229805f4d4
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935352"
---
# <a name="ltcgt-visual-basic"></a><span data-ttu-id="fa798-102">&lt;c&gt; (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="fa798-102">&lt;c&gt; (Visual Basic)</span></span>
<span data-ttu-id="fa798-103">Indica que o texto dentro uma descrição é o código.</span><span class="sxs-lookup"><span data-stu-id="fa798-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa798-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa798-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
#### <a name="parameters"></a><span data-ttu-id="fa798-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fa798-105">Parameters</span></span>  
  
|<span data-ttu-id="fa798-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="fa798-106">Parameter</span></span>|<span data-ttu-id="fa798-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa798-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="fa798-108">O texto que você deseja indicar como código.</span><span class="sxs-lookup"><span data-stu-id="fa798-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa798-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa798-109">Remarks</span></span>  
 <span data-ttu-id="fa798-110">O `<c>` marcação oferece uma maneira de indicar que o texto dentro uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="fa798-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="fa798-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="fa798-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="fa798-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="fa798-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fa798-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="fa798-113">Example</span></span>  
 <span data-ttu-id="fa798-114">Este exemplo usa o `<c>` marca na seção de resumo para indicar que `Counter` é o código.</span><span class="sxs-lookup"><span data-stu-id="fa798-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="fa798-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa798-115">See Also</span></span>  
 [<span data-ttu-id="fa798-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="fa798-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
