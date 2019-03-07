---
title: <c> (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: d8efd2359ecb65bec1b427d8b1dca4b0c88a1152
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57469021"
---
# <a name="c-visual-basic"></a><span data-ttu-id="7cc89-102">\<c > (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cc89-102">\<c> (Visual Basic)</span></span>
<span data-ttu-id="7cc89-103">Indica que o texto dentro uma descrição é o código.</span><span class="sxs-lookup"><span data-stu-id="7cc89-103">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cc89-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7cc89-104">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cc89-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7cc89-105">Parameters</span></span>  
  
|<span data-ttu-id="7cc89-106">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="7cc89-106">Parameter</span></span>|<span data-ttu-id="7cc89-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7cc89-107">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="7cc89-108">O texto que você deseja indicar como código.</span><span class="sxs-lookup"><span data-stu-id="7cc89-108">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cc89-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="7cc89-109">Remarks</span></span>  
 <span data-ttu-id="7cc89-110">O `<c>` marcação oferece uma maneira de indicar que o texto dentro uma descrição deve ser marcado como código.</span><span class="sxs-lookup"><span data-stu-id="7cc89-110">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="7cc89-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="7cc89-111">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="7cc89-112">Compile com [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="7cc89-112">Compile with [/doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cc89-113">Exemplo</span><span class="sxs-lookup"><span data-stu-id="7cc89-113">Example</span></span>  
 <span data-ttu-id="7cc89-114">Este exemplo usa o `<c>` marca na seção de resumo para indicar que `Counter` é o código.</span><span class="sxs-lookup"><span data-stu-id="7cc89-114">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="7cc89-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7cc89-115">See also</span></span>
- [<span data-ttu-id="7cc89-116">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="7cc89-116">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
