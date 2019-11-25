---
title: <c>
ms.date: 07/20/2015
helpviewer_keywords:
- c XML tag
- <c> XML tag
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
ms.openlocfilehash: 857ea1ccca4d74daf65bba03845004561afefd55
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348504"
---
# <a name="c-visual-basic"></a><span data-ttu-id="bad08-101">\<c> (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="bad08-101">\<c> (Visual Basic)</span></span>
<span data-ttu-id="bad08-102">Indicates that text within a description is code.</span><span class="sxs-lookup"><span data-stu-id="bad08-102">Indicates that text within a description is code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bad08-103">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bad08-103">Syntax</span></span>  
  
```xml  
<c>text</c>  
```  
  
## <a name="parameters"></a><span data-ttu-id="bad08-104">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bad08-104">Parameters</span></span>  
  
|<span data-ttu-id="bad08-105">Parâmetro</span><span class="sxs-lookup"><span data-stu-id="bad08-105">Parameter</span></span>|<span data-ttu-id="bad08-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bad08-106">Description</span></span>|  
|---|---|  
|`text`|<span data-ttu-id="bad08-107">O texto que você deseja indicar como código.</span><span class="sxs-lookup"><span data-stu-id="bad08-107">The text you would like to indicate as code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bad08-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="bad08-108">Remarks</span></span>  
 <span data-ttu-id="bad08-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span><span class="sxs-lookup"><span data-stu-id="bad08-109">The `<c>` tag gives you a way to indicate that text within a description should be marked as code.</span></span> <span data-ttu-id="bad08-110">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) para indicar várias linhas como código.</span><span class="sxs-lookup"><span data-stu-id="bad08-110">Use [\<code>](../../../visual-basic/language-reference/xmldoc/code.md) to indicate multiple lines as code.</span></span>  
  
 <span data-ttu-id="bad08-111">Compile com [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) para processar comentários de documentação em um arquivo.</span><span class="sxs-lookup"><span data-stu-id="bad08-111">Compile with [-doc](../../../visual-basic/reference/command-line-compiler/doc.md) to process documentation comments to a file.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bad08-112">Exemplo</span><span class="sxs-lookup"><span data-stu-id="bad08-112">Example</span></span>  
 <span data-ttu-id="bad08-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span><span class="sxs-lookup"><span data-stu-id="bad08-113">This example uses the `<c>` tag in the summary section to indicate that `Counter` is code.</span></span>  
  
 [!code-vb[VbVbcnXmlDocComments#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnXmlDocComments/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="bad08-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bad08-114">See also</span></span>

- [<span data-ttu-id="bad08-115">Marcações de Comentário XML</span><span class="sxs-lookup"><span data-stu-id="bad08-115">XML Comment Tags</span></span>](../../../visual-basic/language-reference/xmldoc/index.md)
